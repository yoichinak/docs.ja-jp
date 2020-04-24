---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646067"
---
# <a name="sessionsecuritytokencache"></a>\<>
サービスまたはセキュリティ トークン ハンドラーコレクションを使用して、セッション トークンのキャッシュを登録します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<id構成>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<キャッシュ>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|type|クラスから派生する<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>型。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<キャッシュ>](caches.md)|サービスまたはセキュリティ トークン ハンドラーのコレクションで使用されるキャッシュを登録します。|  
  
## <a name="example"></a>例  
 次の XML は、セッション セキュリティ トークン ( )<xref:System.IdentityModel.Tokens.SessionSecurityToken>を保持するためのカスタム キャッシュの構成を示しています。 構成はサンプルから取得されます`ClaimsAwareWebFarm`。 このサンプルの詳細については、「 [WIF コード サンプル インデックス](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index)」を参照してください。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
