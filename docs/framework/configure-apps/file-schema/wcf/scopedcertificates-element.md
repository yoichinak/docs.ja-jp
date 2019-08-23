---
title: <scopedCertificates> 要素
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: ed53a42575a8d57c365f7a329a1a9c1df075d6d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935217"
---
# <a name="scopedcertificates-element"></a>\<scopedCertificates > 要素
認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。 このコレクションは一般に、フェデレーション シナリオでセキュリティ トークン サービスのサービス証明書を指定するために使用されます。  
  
 \<system.ServiceModel >  
\<<behaviors>  
endpointBehaviors セクション  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate>  
\<scopedCertificates > 要素  
\<scopedCertificates > の > \<要素の追加  
  
## <a name="syntax"></a>構文  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|範囲指定された証明書のコレクションに X.509 証明書を追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCertificate >](servicecertificate-of-servicecredentials.md)|クライアントに対してサービスを認証する際に使用される証明書を指定します。|  
  
## <a name="remarks"></a>Remarks  
 このコレクションを使用すると、クライアントは、通信するサービスの URL に基づいて、使用するサービス証明書を構成できます。 これは、クライアントが複数のサービス (エンド サービスと中間セキュリティ トークン サービス) と通信している可能性がある発行済みトークンのシナリオで特に便利です。 証明書に基づくメッセージ セキュリティを使用したバインドにおいて、この証明書を使用してサービスへのメッセージを暗号化します。サービスがクライアントへの応答に署名する際には、この証明書を使用することが要求されます。  
  
 バインディングにサービスの証明書が必要で、サービスの URL に対する特定の証明書が ScopedCertificates 内に存在しない場合は、既定の証明書が使用されます。  
  
 詳細について[は、「How to:フェデレーションクライアント](../../../wcf/feature-details/how-to-create-a-federated-client.md)を作成します。  
  
## <a name="example"></a>例  
 次の例は、ドメインの名前のエンドポイントと通信するときに使用するクライアントのサービス証明書を指定する `http://www.contoso.com` HTTP プロトコル経由します。  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)
- [方法: フェデレーションクライアントを作成する](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [クライアントのセキュリティ保護](../../../wcf/securing-clients.md)
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
