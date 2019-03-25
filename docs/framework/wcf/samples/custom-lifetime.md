---
title: カスタムの有効期間
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: be6013d568e3625c5eac7e0c145db7df1c6917e3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410382"
---
# <a name="custom-lifetime"></a>カスタムの有効期間

このサンプルでは、共有の WCF サービスのインスタンス用のカスタムの有効期間サービスを提供する Windows Communication Foundation (WCF) 拡張機能の記述方法を示します。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、この記事の最後を参照してください。

## <a name="shared-instancing"></a>共有インスタンス化

WCF には、サービス インスタンス用のいくつかのインスタンス化モードが用意されています。 この記事で説明する共有インスタンス化モードでは、複数のチャネルでのサービス インスタンスを共有する方法を提供します。 クライアントは、サービスのファクトリ メソッドにお問い合わせくださいし、の通信を開始する新しいチャネルを作成します。 次のコード スニペットは、クライアント アプリケーションが既存のサービス インスタンスに新しいチャネルを作成する方法を示しています。

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

他のインスタンス化モードとは異なり、共有インスタンス化モードでは、独特の方法でサービス インスタンスを解放します。 すべてのチャネルが閉じられたときに、既定で、 <xref:System.ServiceModel.InstanceContext>、WCF サービスのランタイムをかどうかを確認しますサービス<xref:System.ServiceModel.InstanceContextMode>するように構成<xref:System.ServiceModel.InstanceContextMode.PerCall>または<xref:System.ServiceModel.InstanceContextMode.PerSession>、場合にそのため、インスタンスを解放し、リソースを要求します。 場合、カスタム<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>が使用されている WCF を呼び出す、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>インスタンスをリリースする前に、プロバイダーの実装のメソッド。 場合<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>返します`true`、それ以外の場合、インスタンスが解放、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>に通知するため、実装は、`Dispatcher`のコールバック メソッドを使用してアイドル状態です。 これは、呼び出すことで、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>プロバイダーのメソッド。

このサンプルでは、解放を延期する方法、 <xref:System.ServiceModel.InstanceContext> 20 秒のアイドル状態のタイムアウトを設定しています。

## <a name="extending-the-instancecontext"></a>InstanceContext の拡張

WCF では、<xref:System.ServiceModel.InstanceContext>サービス インスタンスの間のリンクは、および`Dispatcher`します。 WCF の拡張可能オブジェクト パターンを使用して新しい状態または動作を追加することで、このランタイム コンポーネントを拡張することができます。 拡張可能オブジェクト パターンは、またはオブジェクトに新しい状態の機能を追加するか、新しい機能を既存のランタイム クラスを拡張する、WCF で使用されます。 拡張可能オブジェクト パターンには、<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601>、および <xref:System.ServiceModel.IExtensionCollection%601> の 3 つのインターフェイスがあります。

<xref:System.ServiceModel.IExtensibleObject%601>インターフェイスが、機能をカスタマイズする拡張機能を許可するオブジェクトによって実装されます。


  <xref:System.ServiceModel.IExtension%601> インターフェイスは、`T` 型のクラスの拡張が可能なオブジェクトによって実装されます。

最後に、<xref:System.ServiceModel.IExtensionCollection%601>インターフェイスのコレクションである<xref:System.ServiceModel.IExtension%601>の実装を取得するためにできる実装<xref:System.ServiceModel.IExtension%601>をその型。

そのため、拡張するには、 <xref:System.ServiceModel.InstanceContext>、実装する必要があります、<xref:System.ServiceModel.IExtension%601>インターフェイス。 このサンプル プロジェクトで、`CustomLeaseExtension`クラスには、この実装が含まれています。

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```


  <xref:System.ServiceModel.IExtension%601> インターフェイスには、<xref:System.ServiceModel.IExtension%601.Attach%2A> と <xref:System.ServiceModel.IExtension%601.Detach%2A> の 2 つのメソッドが含まれています。 名前が示すように、これらの 2 つのメソッドは、ランタイムが <xref:System.ServiceModel.InstanceContext> クラスのインスタンスに拡張機能を関連付けるときと関連付けを解除するときに呼び出されます。 このサンプルでは、`Attach` メソッドを使用して、拡張機能の現在のインスタンスに属する <xref:System.ServiceModel.InstanceContext> オブジェクトを追跡します。

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

また、有効期間の延長をサポートするには、必要な実装を拡張機能に追加する必要があります。 そのため、`ICustomLease`インターフェイスは、目的のメソッドで宣言されで実装されて、`CustomLeaseExtension`クラス。

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

WCF を呼び出すときに、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>メソッドで、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>実装では、この呼び出しにルーティングされます、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>のメソッド、`CustomLeaseExtension`します。 次に、`CustomLeaseExtension`して、そのプライベート状態を確認するかどうか、<xref:System.ServiceModel.InstanceContext>がアイドル状態です。 返すかどうかは、アイドル状態が、`true`します。 それ以外の場合は、延長された指定の有効期間のタイマーが開始されます。

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

タイマーの`Elapsed`イベント ディスパッチャーでコールバック関数は、別のクリーンアップ サイクルを開始するために呼び出されます。

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

アイドル状態に移行中のインスタンスに新しいメッセージが届いたときに、実行中のタイマーを更新する方法はありません。

このサンプルでは、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドの呼び出しを受け取って <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> にルーティングするために `CustomLeaseExtension` を実装します。 
  <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、`CustomLifetimeLease` クラスに含まれています。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF がサービス インスタンスを解放するときにメソッドが呼び出されます。 ただし、ServiceBehavior の `ISharedSessionInstance` コレクションに存在する特定の <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装のインスタンスは 1 つだけです。 つまり、知る必要が場合の方法はありません、 <xref:System.ServiceModel.InstanceContext> WCF チェック時に、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>メソッド。 そのため、このサンプルはスレッドへの要求をシリアル化するロックを使用、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>メソッド。

> [!IMPORTANT]
> シリアル化はアプリケーションのパフォーマンスに大きな影響を及ぼす可能性があるので、スレッド ロックは使用しないことをお勧めします。

プライベート メンバー フィールドが使用される、`CustomLifetimeLease`アイドル状態を追跡するためにクラスし、によって返される、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>メソッド。 毎回、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>メソッドが呼び出される、`isIdle`フィールドが返され、リセット`false`します。  ディスパッチャーが `false` メソッドを呼び出すようにするには、この値を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> に設定する必要があります。

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

場合、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>メソッドを返します。 `false`、ディスパッチャーを使用して、コールバック関数の登録、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>メソッド。 このメソッドは、解放される <xref:System.ServiceModel.InstanceContext> への参照を受け取ります。 そのため、サンプル コードを問い合わせることができます、`ICustomLease`拡張子を入力し、確認、`ICustomLease.IsIdle`拡張状態プロパティ。

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

前に、`ICustomLease.IsIdle`プロパティをチェックして、コールバック プロパティは、これには、重要な設定が必要`CustomLeaseExtension`アイドル状態になったときに、ディスパッチャーに通知します。 
  `ICustomLease.IsIdle` が `true` を返す場合は、`isIdle` プライベート メンバーが `CustomLifetimeLease` で単に `true` に設定され、コールバック メソッドが呼び出されます。 コードでは、ロックを保持しているために、他のスレッドは、このプライベート メンバーの値を変更できません。 次回ディスパッチャーを呼び出すと、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>を返します`true`でき、ディスパッチャーのインスタンスを解放します。

これでカスタム拡張機能の基礎が完成したので、この拡張機能をサービス モデルにフックする必要があります。 フックするため、`CustomLeaseExtension`を実装、 <xref:System.ServiceModel.InstanceContext>、WCF の提供、<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>のブートス トラップを実行するインターフェイス<xref:System.ServiceModel.InstanceContext>。 このサンプルでは、`CustomLeaseInitializer` クラスでこのインターフェイスを実装し、`CustomLeaseExtension` のインスタンスを唯一のメソッドの初期化から得られる <xref:System.ServiceModel.InstanceContext.Extensions%2A> コレクションに追加します。 このメソッドは、<xref:System.ServiceModel.InstanceContext> の初期化中にディスパッチャーによって呼び出されます。

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 最後に、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>実装にフックされる、サービス モデルを使用して、<xref:System.ServiceModel.Description.IServiceBehavior>実装します。 この実装は、`CustomLeaseTimeAttribute` クラスに配置されています。また、<xref:System.Attribute> 基本クラスから派生してこの動作を属性として公開します。

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

この動作は、`CustomLeaseTime` 属性を使用して注釈を付けることにより、サンプル サービス クラスに追加できます。

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。

### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)します。

2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。

3. 1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](running-the-samples.md)します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
