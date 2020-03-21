---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183342"
---
# <a name="srmp"></a>SRMP
このサンプルでは、HTTP 経由でメッセージ キュー (MSMQ) を使用して、トランザクション キューによる通信を実行する方法を示します。  
  
 キュー通信では、クライアントはサービスとの通信にキューを使用します。 厳密には、クライアントはメッセージをキューに送信します。 サービスは、メッセージをキューから受信します。 したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。  
  
 MSMQ は HTTP (HTTPS を含む) を使用できるようにして、メッセージをキューに送信します。 この例では、Windows 通信基盤 (WCF) キューに入れされた通信の使用方法と、HTTP 経由でメッセージを送信する方法を示します。 MSMQ では SRMP というプロトコルを使用します。これは、HTTP 経由の通信に使用する SOAP ベースのプロトコルです。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。  
  
4. **「Windows コンポーネントの追加と削除**」のサンプルを実行する前に、MSMQ が HTTP サポートでインストールされていることを確認してください。 HTTP サポートをインストールすると、インターネット インフォメーション サービス (IIS) が自動的にインストールされ、MSMQ 用のプロトコル サポートが IIS に追加されます。  
  
5. HTTP が通信に使用されていることを確認するには、MSMQ を強化モードで実行します。 これにより、HTTP 以外のトランスポートを使用した場合は、コンピュータ上でホストされているすべてのキューにメッセージが到着できないようになります。  
  
6. MSMQ をセキュリティ強化モードで実行するように選択した後、コンピュータは Windows Server 2003 で再起動する必要があります。  
  
7. サービスを実行します。  
  
8. クライアントを実行します。 エンドポイント アドレスは、localhost ではなくコンピュータ名または IP アドレスを指定するように変更してください。 クライアントはメッセージを送信して終了します。  
  
## <a name="requirements"></a>必要条件  
 このサンプルを実行するには、MSMQ に加え、IIS をサービス コンピュータとクライアント コンピュータの両方にインストールする必要があります。  
  
## <a name="demonstrates"></a>対象  
 このサンプルでは、MSMQ を使用して HTTP 経由で WCF キューに入れメッセージを送信する方法を示します。 これは、SRMP メッセージングとも呼ばれます。 キューに置かれたメッセージが送信されると、送信元コンピュータの MSMQ は、このメッセージを TCP または HTTP トランスポート経由で受信キュー マネージャに転送します。 SRMP を選択すると、HTTP をキュー転送用のトランスポートとして選択したことになります。 SRMP Secure を選択すると、HTTPS を使用できます。  
  
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
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
