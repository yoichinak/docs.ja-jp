---
title: <serviceCertificate> <clientCredentials>要素
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4fe196ef8737c7abde939e36c2bb7afd5a0d86b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670301"
---
# <a name="servicecertificate-of-clientcredentials-element"></a>\<serviceCertificate > の\<clientCredentials > 要素
クライアントに対してサービスを認証する際に使用される証明書を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<endpointBehaviors>  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate>  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<defaultCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|ネゴシエーション プロトコル経由でサービスまたは STS が証明書を提供しないときに使用される X.509 証明書を指定します。|  
|[\<scopedCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。 このコレクションは一般に、フェデレーション シナリオでセキュリティ トークン サービスのサービス証明書を指定するために使用されます。|  
|[\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|クライアントで使用されるサービス証明書の認証動作を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|サービスに対するクライアント自身の認証のためにクライアントによって使用される資格情報を指定します。|  
  
## <a name="remarks"></a>Remarks  
 この構成要素は、SSL 認証を使用してサービスから提示された証明書を検証するためにクライアントが使用する設定を指定します。 また、このクラスには、メッセージ セキュリティを使用してサービスへのメッセージを暗号化するためにクライアントで明示的に構成される、サービスの証明書も含まれます。  
  
 属性、`serviceCertificate`要素は同一の属性には、 [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)
- [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
