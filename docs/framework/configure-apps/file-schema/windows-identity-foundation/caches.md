---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252156"
---
# <a name="caches"></a>\<キャッシュ >
セッショントークンとトークンリプレイ検出に使用されるキャッシュを登録します。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<システムの >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<構成 >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<キャッシュ >**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Sessionsecuritytokencache> >](sessionsecuritytokencache.md)|セッショントークンのキャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。|  
|[\<tokenReplayCache>](tokenreplaycache.md)|トークン再生キャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|サービスレベルの id 設定を指定します。|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 要素は、要素の`<identityConfiguration>`下のサービスレベルで指定することも、 `<securityTokenHandlerConfiguration>`要素の下のセキュリティトークンハンドラーコレクションレベルで指定することもできます。 `<caches>` トークンハンドラーコレクションの設定は、サービスで指定された設定よりも優先されます。  
  
 要素は、 <xref:System.IdentityModel.Configuration.IdentityModelCachesElement>クラスによって表されます。 `<caches>` 構成されたキャッシュは、 <xref:System.IdentityModel.Configuration.IdentityModelCaches>クラスによって表されます。  
  
## <a name="example"></a>例  
 次の XML は、セッションセキュリティトークン (<xref:System.IdentityModel.Tokens.SessionSecurityToken>) を保持するためのカスタムキャッシュの構成を示しています。 この構成は、 `ClaimsAwareWebFarm`サンプルから取得されます。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
