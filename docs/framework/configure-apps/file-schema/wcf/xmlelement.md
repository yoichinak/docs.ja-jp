---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: a72641b438801cfd493c322297e7c384e83e687c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230500"
---
# <a name="xmlelement"></a>\<xmlElement>
トークンの要求時にセキュリティ トークン サービスへのメッセージ本文で送信される XML 要素を指定します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<wsFederatedBinding>  
\<binding>  
\<セキュリティ >  
\<message>  
\<tokenRequestParameters>  
  
## <a name="syntax"></a>構文  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|xmlElement|トークンの要求時にセキュリティ トークン サービスへのメッセージ本文で送信される XML 要素を指定する文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|トークン要求パラメーターのコレクション。 各パラメーターは、XML 要素です。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [カスタム バインドを使用したセキュリティ機能](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
