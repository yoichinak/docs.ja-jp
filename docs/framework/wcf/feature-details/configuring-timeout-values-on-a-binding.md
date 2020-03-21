---
title: バインディングでのタイムアウト値の構成
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 968e80bbd4b50d72d089a325f8e3fe498de2eac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185284"
---
# <a name="configuring-timeout-values-on-a-binding"></a>バインディングでのタイムアウト値の構成
WCF バインディングには、さまざまなタイムアウト設定が用意されています。 これらのタイムアウト設定を正しく行うことによって、サービスのパフォーマンスが向上するだけでなく、サービスの操作性とセキュリティにも役立ちます。 WCF バインディングで使用できるタイムアウトは次のとおりです。  
  
1. OpenTimeout  
  
2. CloseTimeout  
  
3. SendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>WCF バインディングのタイムアウト  
 このトピックで説明する各設定は、バインディング自体に対して、コードまたは構成を使用して適用されます。 次のコードは、自己ホスト型サービスのコンテキストで、WCF バインディングのタイムアウトをプログラムで設定する方法を示します。  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");

    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));

        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);

        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 次の例は、構成ファイル内でバインディングのタイムアウトを構成する方法を示します。  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00"
                 closeTimeout="00:10:00"
                 sendTimeout="00:10:00"
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 これらの設定の詳細については、<xref:System.ServiceModel.Channels.Binding> クラスに関するドキュメントを参照してください。  
  
### <a name="client-side-timeouts"></a>サービス側のタイムアウト  
 クライアント側:  
  
1. SendTimeout: OperationTimeout の初期化に使用します。要求/応答サービス操作の応答メッセージの受信を含め、メッセージの送信プロセス全体を制御します。 このタイムアウトは、コールバック コントラクト メソッドから応答メッセージを送信するときにも適用されます。  
  
2. OpenTimeout – 明示的なタイムアウト値が指定されていないときにチャネルを開くときに使用されます。  
  
3. CloseTimeout – 明示的なタイムアウト値が指定されていないときにチャネルを閉じるときに使用されます。  
  
4. タイムアウトの受信 – は使用されません。  
  
### <a name="service-side-timeouts"></a>サービス側のタイムアウト  
 サービス側のタイムアウトは次のとおりです。  
  
1. 送信タイムアウト、オープンタイムアウト、クローズタイムアウトはクライアントと同じです。  
  
2. ReceiveTimeout: セッションがタイムアウトするまでのアイドル状態の時間を制御するセッション アイドル タイムアウトを初期化するために Service Framework Layer で使用します。
