---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 28ae27481ea9cb86c31b5be1f12b5491f8ca143e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936153"
---
# <a name="serviceprincipalname"></a>\<servicePrincipalName >
サービスの ID をサービス プリンシパル名 (SPN) により指定します。  
  
 SPN の設定の詳細については、「[サービス id と認証](../../../wcf/feature-details/service-identity-and-authentication.md)」を参照してください。  
  
 \<identity>  
\<servicePrincipalName >  
  
## <a name="syntax"></a>構文  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|value|クライアントがサービスのインスタンスを一意に識別する名前です。 フォレストの複数のコンピューターに 1 つのサービスの複数のインスタンスをインストールする場合、各インスタンスには独自の SPN が必要です。 クライアントが認証に使用できる複数の名前がある場合は、指定したサービス インスタンスに複数の SPN を設定できます。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identity>](identity.md)|クライアントで認証するサービスの ID を指定します。|  
  
## <a name="remarks"></a>Remarks  
 この id を持つエンドポイントに接続するセキュリティで保護された Windows Communication Foundation (WCF) クライアントは、エンドポイントで SSPI 認証を実行するときに SPN を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [サービス ID と認証](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
