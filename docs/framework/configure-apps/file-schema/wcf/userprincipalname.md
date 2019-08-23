---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 423a3249a9298675517f0cff08566c3735fa35f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940509"
---
# <a name="userprincipalname"></a>\<userPrincipalName>
クライアントで認証するサービスのユーザー プリンシパル名 (UPN) を指定します。  
  
 UPN の設定の詳細については、「[サービス id と認証](../../../wcf/feature-details/service-identity-and-authentication.md)」を参照してください。  
  
\<identity>  
\<userPrincipalName>  
  
## <a name="syntax"></a>構文  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|value|ユーザー アカウント名 (ユーザー ログイン名と呼ばれることもある) と、ユーザー アカウントの検索範囲のドメインを識別するドメイン名です。 これは、Windows ドメインにログオンするための標準的使用方法です。 形式はsomeone@example.com 、(電子メールアドレスの場合) です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identity>](identity.md)|クライアントで認証するサービスの ID を指定します。|  
  
## <a name="remarks"></a>Remarks  
 この id を持つエンドポイントに接続するセキュリティで保護された Windows Communication Foundation (WCF) クライアントは、エンドポイントで SSPI 認証を実行するときに UPN を使用します。  
  
## <a name="example"></a>例  
 次の構成コードは、クライアントで認証するサービスの UPN を指定します。  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [サービス ID と認証](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
