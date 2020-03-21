---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152750"
---
# <a name="claimsauthenticationmanager"></a>\<クレーム認証マネージャー>
受信要求のクレーム認証マネージャーを登録します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<id構成>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<クレーム認証マネージャー>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|type|クラスから派生するカスタム型を指定します<xref:System.Security.Claims.ClaimsAuthenticationManager>。 `type`属性の指定方法の詳細については、「[カスタム型参照]」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 属性がない`type`場合、または属性がクラスを`type`参照している<xref:System.Security.Claims.ClaimsAuthenticationManager>場合、`<claimsAuthenticationManager>`要素は子要素を受け取りません。ただし、派生したクラス<xref:System.Security.Claims.ClaimsAuthenticationManager>は子構成要素を定義できます。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<id構成>](identityconfiguration.md)|サービス レベルの ID 設定を指定します。|  
  
## <a name="remarks"></a>解説  
 クラスを通じて指定される<xref:System.Security.Claims.ClaimsAuthenticationManager>既定の動作は、受信した要求をエコーします。 属性が`type`指定されていない場合、または属性`type`がクラスを<xref:System.Security.Claims.ClaimsAuthenticationManager>指定する場合`<claimsAuthenticationManager>`、要素は子要素を受け取りません。 クラスから派生した`type`型を登録してカスタム動作を実装<xref:System.Security.Claims.ClaimsAuthenticationManager>する属性を指定できます。 派生クラスは、これらの要素を処理するメソッド`<claimsAuthenticationManager>`をオーバーライドすることで、要素<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>の子要素を通じて構成をサポートできます。 子要素に対して定義されたスキーマは、クラスのデザイナーによって行われます。  
  
 要素`<claimsAuthenticationManager>`は、プロパティ<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>を設定します。  
  
## <a name="example"></a>例  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
