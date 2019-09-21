---
title: '方法: ポート共有を使用するように Windows Communication Foundation サービスを構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: e92ce3468bd43456ac3f838cfc44ea7c6624502b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912214"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>方法: ポート共有を使用するように Windows Communication Foundation サービスを構成する
Windows Communication Foundation (WCF) アプリケーションで net.tcp://ポート共有を使用する最も簡単な方法は、 <xref:System.ServiceModel.NetTcpBinding>を使用してサービスを公開することです。  
  
 このバインディングは、<xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> プロパティを提供します。このプロパティは、このバインディングを使用して構成されるサービスに対して net.tcp:// ポート共有を有効にするかどうかを制御します。  
  
 以下の手順では、<xref:System.ServiceModel.NetTcpBinding> クラスを使用して URI (Uniform Resource Identifier)、net.tcp://localhost/MyService にあるエンドポイントを開く方法を示します。最初にコードを使用する場合の手順を示し、次に構成要素を使用する場合の手順を示します。  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>コードで NetTcpBinding の net.tcp:// ポート共有を有効にするには  
  
1. というコントラクトを実装するサービスを`IMyService`作成し`MyService`、という名前を呼び出します。  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> プロパティを `true` に設定します。  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <xref:System.ServiceModel.ServiceHost> を作成し、ポート共有を有効にした `MyService` を使用し、エンドポイント アドレス URI "net.tcp://localhost/MyService" をリッスンする <xref:System.ServiceModel.NetTcpBinding> のサービス エンドポイントを追加します。  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > このエンドポイント アドレス URI は異なるポート番号を指定しないため、この例では既定の TCP ポートである 808 を使用します。 トランスポート バインディングでポート共有が明示的に有効になっているため、このサービスはポート 808 を他のプロセスの他のサービスと共有できます。 ポート共有が許可されておらず、既に別のアプリケーションがポート 808 を使用している場合は、このサービスを開こうとすると <xref:System.ServiceModel.AddressAlreadyInUseException> がスローされます。  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>構成で NetTcpBinding の net.tcp:// ポート共有を有効にするには  
  
1. 次の例では、構成要素を使用してポート共有を有効にし、サービス エンドポイントを追加します。  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>関連項目

- [Net.TCP ポート共有](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [方法: Net.tcp ポート共有サービスを有効にする](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
