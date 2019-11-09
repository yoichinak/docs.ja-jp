---
title: WCF 開発者向けのメタデータ-gRPC
description: GRPC でメタデータを使用して、クライアントとサーバーの間に追加のコンテキストを渡す方法
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 32559b3404b12f366fc1624299d04cff9faad9d6
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "73841583"
---
# <a name="metadata"></a>メタデータ

"メタデータ" とは、要求と応答の処理中に便利な追加データを指しますが、実際のアプリケーションデータの一部ではありません。 メタデータには、認証トークン、監視のための要求識別子とタグ、データセット内のレコードの数などのデータに関する情報が含まれます。

<xref:System.ServiceModel.OperationContextScope> と <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> プロパティを使用して WCF メッセージに汎用キー/値ヘッダーを追加し、<xref:System.ServiceModel.Channels.MessageProperties>を使用して処理することができます。

gRPC の呼び出しと応答には、HTTP ヘッダーに似たメタデータを含めることもできます。 これらはほとんどの場合、gRPC 自体には見えず、アプリケーションコードまたはミドルウェアによって処理されるために渡されます。 メタデータはキーと値のペアとして表され、キーは文字列で、値は文字列またはバイナリデータのいずれかになります。 `.proto` ファイルでメタデータを指定する必要はありません。

メタデータは、 [Grpc. Core. Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet パッケージの `Metadata` クラスを使用して処理されます。 このクラスは、コレクション初期化子構文と共に使用できます。

次の例は、 C#クライアントからの呼び出しにメタデータを追加する方法を示しています。

```csharp
var metadata = new Metadata
{
    { "Requester", _clientName }
};

var request = new GetPortfolioRequest
{
    Id = portfolioId
};

var response = await client.GetPortfolioAsync(request, metadata);
```

gRPC サービスは、`ServerCallContext` 引数の `RequestHeaders` プロパティからメタデータにアクセスできます。

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var requesterHeader = context.RequestHeaders.FirstOrDefault(e => e.Key == "Requester");
    if (requesterHeader != null)
    {
        _logger.LogInformation($"Request from {requesterHeader.Value}");
    }
    // ...
}
```

サービスは、`ServerCallContext`の `ResponseTrailers` プロパティを使用して、クライアントにメタデータを送信できます。

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
>[前へ](rpc-types.md)
>[次へ](error-handling.md)
