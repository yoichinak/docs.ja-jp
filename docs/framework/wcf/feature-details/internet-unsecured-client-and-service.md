---
title: セキュリティで保護されていないインターネット環境のクライアントとサービス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 480242d519fee6ddabac3b39ff21f8e1b76827f0
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410668"
---
# <a name="internet-unsecured-client-and-service"></a>セキュリティで保護されていないインターネット環境のクライアントとサービス
次の図は、パブリック、セキュリティ保護されていない Windows Communication Foundation (WCF) クライアントとサービスの例を示します。  
  
 ![セキュリティ保護されていないインターネットのシナリオを示すスクリーン ショット](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|特徴|説明|  
|--------------------|-----------------|  
|セキュリティ モード|なし|  
|Transport|HTTP|  
|バインド|<xref:System.ServiceModel.BasicHttpBinding> コードでは、または[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)構成内の要素。|  
|相互運用性|既存の Web サービス クライアントとサービスを使用する|  
|認証|なし|  
|整合性|なし|  
|機密性|なし|  
  
## <a name="service"></a>サービス  
 次のコードと構成は、別々に実行します。 次のいずれかの操作を行います。  
  
-   構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。  
  
-   提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。  
  
### <a name="code"></a>コード  
 次のコードは、セキュリティで保護されないエンドポイントを作成する方法を示しています。 既定では、<xref:System.ServiceModel.BasicHttpBinding> のセキュリティ モードは <xref:System.ServiceModel.BasicHttpSecurityMode.None> に設定されます。  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a>サービス構成  
 次のコードは、構成を使用して同一のエンドポイントをセットアップします。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"   
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>クライアント  
 次のコードと構成は、別々に実行します。 次のいずれかの操作を行います。  
  
-   コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。  
  
-   エンドポイント アドレスを定義しないクライアントを作成します。 代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。 例:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>コード  
 次のコードでは、セキュリティ保護されていないエンドポイントにアクセスする基本的な WCF クライアントを示します。  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a>クライアント構成  
 クライアントを構成する場合のコード例を次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"   
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"   
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目
- [一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
