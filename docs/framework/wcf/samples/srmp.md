---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 92a0bac3cf6ac6b57792419c913ec481ff0ee6c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769451"
---
# <a name="srmp"></a>SRMP
このサンプルでは、HTTP 経由でメッセージ キュー (MSMQ) を使用して、トランザクション キューによる通信を実行する方法を示します。  
  
 キュー通信では、クライアントはサービスとの通信にキューを使用します。 厳密には、クライアントはメッセージをキューに送信します。 サービスは、メッセージをキューから受信します。 したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。  
  
 MSMQ は HTTP (HTTPS を含む) を使用できるようにして、メッセージをキューに送信します。 この例では、通信および HTTP 経由でメッセージを送信する方法に Windows Communication Foundation (WCF) を使用してキューに置かれたについて説明します。 MSMQ では SRMP というプロトコルを使用します。これは、HTTP 経由の通信に使用する SOAP ベースのプロトコルです。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
4. サンプルを実行する前に**Windows コンポーネントの追加/削除**MSMQ がインストールされていることを確認します。 HTTP をサポートします。 HTTP サポートをインストールすると、インターネット インフォメーション サービス (IIS) が自動的にインストールされ、MSMQ 用のプロトコル サポートが IIS に追加されます。  
  
5. HTTP が通信に使用されていることを確認するには、MSMQ を強化モードで実行します。 これにより、HTTP 以外のトランスポートを使用した場合は、コンピュータ上でホストされているすべてのキューにメッセージが到着できないようになります。  
  
6. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では、MSMQ を強化モードで実行するように選択した後でコンピュータを再起動する必要があります。  
  
7. サービスを実行します。  
  
8. クライアントを実行します。 エンドポイント アドレスは、localhost ではなくコンピュータ名または IP アドレスを指定するように変更してください。 クライアントはメッセージを送信して終了します。  
  
## <a name="requirements"></a>必要条件  
 このサンプルを実行するには、MSMQ に加え、IIS をサービス コンピュータとクライアント コンピュータの両方にインストールする必要があります。  
  
## <a name="demonstrates"></a>使用例  
 サンプルでは、WCF の送信では HTTP 経由で MSMQ を使用してメッセージをキューに登録します。 これは、SRMP メッセージングとも呼ばれます。 キューに置かれたメッセージが送信されると、送信元コンピュータの MSMQ は、このメッセージを TCP または HTTP トランスポート経由で受信キュー マネージャに転送します。 SRMP を選択すると、HTTP をキュー転送用のトランスポートとして選択したことになります。 SRMP Secure を選択すると、HTTPS を使用できます。  
  
## <a name="example"></a>例  
 このサンプル コードはトランザクションのサンプルに基づいています。 SRMP を使用してキューにメッセージを送信したり、キューからメッセージを受信したりする方法は、ネイティブ プロトコルを使用してメッセージを送受信する方法と同じです。  
  
 クライアントの構成は、キュー転送プロトコルの選択を示すように変更されます。 キュー転送プロトコルには、ネイティブ、SRMP、または SRMP Secure のいずれか 1 つを選択できます。 既定の転送プロトコルはネイティブです。 この例では、クライアントとサービスの構成で SRMP を使用するように指定されます。  
  
 セキュリティの関係で、SRMP には制限があります。 既定の MSMQ トランスポート セキュリティには Active Directory が必要です。Active Directory では、送信キュー マネージャと受信キュー マネージャが同じ Windows ドメインに存在する必要があります。 HTTP 境界を越えてメッセージを送信する場合、これは不可能です。 このため、既定のトランスポート セキュリティは機能しません。 トランスポート セキュリティが必要な場合は、トランスポート セキュリティを Certificate に設定する必要があります。 また、メッセージのセキュリティ保護にメッセージ セキュリティを使用することもできます。 このサンプルでは SRMP メッセージングを説明するために、トランスポート セキュリティとメッセージ セキュリティはどちらも無効になっています。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"   
           bindingConfiguration="srmpBinding"   
           binding="netMsmqBinding"   
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 このサンプルを実行すると、次の出力が生成されます。  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
