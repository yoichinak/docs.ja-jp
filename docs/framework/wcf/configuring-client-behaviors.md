---
title: クライアントの動作の構成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193656"
---
# <a name="configuring-client-behaviors"></a>クライアントの動作の構成
Windows Communication Foundation (WCF) は、2 つの方法で動作を構成します--で定義されている動作の構成を参照して、`<behavior>`セクションのクライアント アプリケーション構成ファイル – またはプログラムで、呼び出し元。アプリケーション。 このトピックでは、両方の方法について説明します。  
  
 構成ファイルを使用する場合、動作の構成には、構成設定の名前付きコレクションがあります。 各動作の構成には、一意の名前を指定する必要があります。 この文字列をエンドポイントの構成の `behaviorConfiguration` 属性で使用し、エンドポイントと動作を関連付けます。  
  
## <a name="example"></a>例  
 `myBehavior` という動作を定義する構成コードを次に示します。 クライアント エンドポイントは、この動作を `behaviorConfiguration` 属性で参照します。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a>プログラムによる動作の使用  
 設定を探し、適切な動作をプログラムで挿入や`Behaviors`Windows Communication Foundation (WCF) クライアント オブジェクトまたはクライアントを開く前に、クライアント チャネル ファクトリ オブジェクトのプロパティ。  
  
## <a name="example"></a>例  
 次のコード例は、チャネル オブジェクトの作成前に、<xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> プロパティから返される <xref:System.ServiceModel.Description.ServiceEndpoint> 上の <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> プロパティにアクセスすることで、プログラムでクライアント動作が挿入される方法を示します。  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>関連項目

- [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
