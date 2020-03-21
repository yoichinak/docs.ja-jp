---
title: ConcurrencyMode 再入
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183895"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode 再入
このサンプルでは、サービス実装で ConcurrencyMode.Reentrant を使用する必要性と影響を示します。 ConcurrencyMode.Reentrant は、サービス (またはコールバック) が指定された時間で処理するメッセージが 1 つだけであることを示します (`ConcurencyMode.Single` に似ています)。 スレッドの安全性を確保するために、Windows 通信基盤 (WCF) は、他の`InstanceContext`メッセージを処理できないように、メッセージの処理をロックします。 再入モードの場合、サービスが呼び出しの送信を行う直前に `InstanceContext` のロックが解除されます。これによりその後の呼び出しが可能になり (サンプルに示すように再入可能になり)、次回サービスに呼び出しが届いたときにロックされます。 この動作を示すために、サンプルでは、クライアントとサービスが双方向コントラクトを使用してメッセージを相互に送信する方法を示します。  
  
 定義されているコントラクトは双方向コントラクトで、サービスによって実装される `Ping` メソッドと、クライアントによって実装されるコールバック メソッド `Pong` を含みます。 クライアントは、サーバーの `Ping` メソッドを呼び出します。このメソッドには、呼び出しを初期化するチック カウントが含まれています。 サービスはチック カウントが 0 でないことを確認し、チック カウントをデクリメントしながらコールバックの `Pong` メソッドを呼び出します。 これは、サンプルの次のコードによって行います。  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 コールバックの `Pong` 実装のロジックは、`Ping` 実装のロジックと同じです。 つまり、このメソッドはチック カウントが 0 でないことを確認し、その後コールバック チャネル (この場合は、元の `Ping` メッセージの送信に使用されたチャネル) の `Ping` メソッドを呼び出し、チック カウントを 1 だけデクリメントします。 チック カウントが 0 になると、このメソッドは返されます。これによってすべての応答のラップが解除され、クライアントが呼び出して初期化した最初の呼び出しに戻されます。 これを、コールバック実装で示します。  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 `Ping` メソッドと `Pong` メソッドはどちらも要求/応答です。つまり、`Ping` の最初の呼び出しは、`CallbackChannel<T>.Pong()` の呼び出しが返される以前には返されません。 クライアントでは、`Pong` メソッドは、このメソッドを返す次の `Ping` 呼び出しが返される以前には返されません。 コールバックとサービスはどちらも、保留中の要求に対して応答できるように、あらかじめ要求/応答の呼び出しを送信する必要があるので、どちらの実装も ConcurrencyMode.Reentrant 動作でマークする必要があります。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。  
  
## <a name="demonstrates"></a>対象  
 サンプルを実行するには、クライアント プロジェクトとサーバー プロジェクトをビルドします。 次に、2 つのコマンド ウィンドウを開\<き、サンプル>\CS\サービス\bin\デバッグ ディレクトリと\<サンプル>\CS\クライアント\bin\デバッグ ディレクトリに変更します。 次に、入力`service.exe`してサービスを開始し、入力引数として渡されたティックの初期値を使用して Client.exe を呼び出します。 サンプルでは、チックとして 10 が出力されます。  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
