---
title: WCF 開発者向けの RPC-gRPC の種類
description: WCF でサポートされているリモートプロシージャコールの種類と gRPC で対応するリモートプロシージャコールのレビュー
ms.date: 09/02/2019
ms.openlocfilehash: 58f097bac61395e6810155e8ae9a6bbf2219ec5e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503444"
---
# <a name="types-of-rpc"></a>RPC の種類

Windows Communication Foundation (WCF) 開発者は、次の種類のリモートプロシージャコール (RPC) を扱うために使用されることがあります。

- 要求/応答
- 通信
  - セッションを含む一方向の二重
  - セッションを使用した全二重
- 一方向

これらの RPC の種類は、既存の gRPC の概念に自然にマップすることができます。 この章では、これらの各領域について見ていきます。 [第5章](migrate-wcf-to-grpc.md)では、同様の例について詳しく説明します。

| WCF | gRPC |
| --- | ---- |
| 通常の要求/応答 | 単項演算子 |
| クライアントコールバックインターフェイスを使用したセッションを使用した双方向サービス | サーバーストリーミング |
| セッションを使用した全二重サービス | 双方向ストリーミング |
| 一方向の操作 | クライアントストリーミング |

## <a name="requestreply"></a>要求/応答

少量のデータを取得して返す単純な要求/応答メソッドの場合は、最も単純な gRPC パターンである単項 RPC を使用します。

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

ご覧のように、gRPC の単項 RPC サービスメソッドを実装することは、WCF 操作の実装に似ています。 ただし、gRPC では、インターフェイスを実装するのではなく、基底クラスのメソッドをオーバーライドする点が異なります。 サーバーでは、gRPC の基本メソッドは常に <xref:System.Threading.Tasks.Task%601>を返します。ただし、クライアントはサービスを呼び出すための非同期メソッドとブロッキングメソッドの両方を提供します。

## <a name="wcf-duplex-one-way-to-client"></a>WCF デュプレックス (クライアントへの一方向)

WCF アプリケーション (特定のバインドを使用) では、クライアントとサーバーの間に永続的な接続を作成できます。 サーバーは、[<xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>] プロパティで指定された*コールバックインターフェイス*を使用して、接続が閉じられるまで、非同期にデータをクライアントに送信できます。

gRPC サービスは、メッセージストリームと同様の機能を提供します。 実装という点で、ストリームは WCF 双方向サービスに*厳密*にはマップされませんが、同じ結果を得ることができます。

### <a name="grpc-streaming"></a>gRPC ストリーミング

gRPC では、クライアントからサーバー、およびサーバーからクライアントへの永続的なストリームの作成がサポートされています。 両方の種類のストリームを同時にアクティブにすることができます。 この機能は、双方向ストリーミングと呼ばれます。 

時間の経過と共に、任意の非同期メッセージングにストリームを使用できます。 または、1つの要求または応答で生成および送信するには大きすぎる大規模なデータセットを渡すために使用できます。

次の例は、サーバーストリーミング RPC を示しています。

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

このサーバーストリームは、次のコードに示すように、クライアントアプリケーションから使用できます。

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> サーバーストリーミング Rpc は、サブスクリプション形式のサービスに役立ちます。 また、データセット全体をメモリ内に構築するのが非効率であるか不可能である場合に、大規模なデータセットを送信する場合にも役立ちます。 ただし、ストリーミング応答は、1つのメッセージで `repeated` フィールドを送信する場合ほど高速ではありません。 ルールとして、小規模なデータセットには streaming を使用しないでください。

### <a name="differences-from-wcf"></a>WCF との違い

WCF 双方向サービスでは、複数のメソッドを持つことができるクライアントコールバックインターフェイスが使用されます。 GRPC サーバーストリーミングサービスは、1つのストリームでのみメッセージを送信できます。 複数のメソッドが必要な場合は、[任意のフィールドまたはフィールドの](protobuf-any-oneof.md)いずれかを含むメッセージ型を使用して、異なるメッセージを送信し、それらを処理するためのコードをクライアントに記述します。

WCF では、セッションを使用した[ServiceContract](xref:System.ServiceModel.ServiceContractAttribute)クラスは、接続が閉じられるまで維持されます。 セッション内では、複数のメソッドを呼び出すことができます。 GRPC では、実装メソッドが返す `Task` は、接続が閉じられるまで完了しません。

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>WCF の一方向操作と gRPC クライアントストリーミング

WCF は、トランスポート固有の確認を返す一方向操作 (`[OperationContract(IsOneWay = true)]`) を提供します。 gRPC サービスメソッドは、空の場合でも、常に応答を返します。 クライアントは、常にその応答を待機する必要があります。 GRPC でのメッセージングの "火災と忘れる" スタイルについては、クライアントストリーミングサービスを作成できます。

### <a name="thing_logproto"></a>thing_log. proto

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a>ThingLogService.cs

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a>のログクライアントの例

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

前の例で示したように、火災および忘れるメッセージにクライアントストリーミング Rpc を使用できます。 また、非常に大規模なデータセットをサーバーに送信するために使用することもできます。 パフォーマンスに関する同じ警告が適用されます。小規模なデータセットの場合は、通常のメッセージで `repeated` フィールドを使用します。

## <a name="wcf-full-duplex-services"></a>WCF の全二重サービス

WCF 双方向バインドでは、サービスインターフェイスとクライアントコールバックインターフェイスの両方で、複数の一方向操作がサポートされます。 このサポートにより、クライアントとサーバーの間で実行中のメッセージ交換が可能になります。 gRPC では、双方向ストリーミング Rpc と同様のものがサポートされていますが、両方のパラメーターが `stream` 修飾子でマークされています。

### <a name="chatproto"></a>チャット. プロトコル

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a>ChatterService.cs

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

前の例では、実装メソッドが要求ストリーム (`IAsyncStreamReader<MessageRequest>`) と応答ストリーム (`IServerStreamWriter<MessageResponse>`) の両方を受け取ることがわかります。 メソッドは、接続が閉じられるまで、メッセージの読み取りと書き込みを行うことができます。

### <a name="chatter-client"></a>Chatter クライアント

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
>[前へ](wcf-bindings.md)
>[次へ](metadata.md)
