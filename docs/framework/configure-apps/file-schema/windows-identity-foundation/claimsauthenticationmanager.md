---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252090"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager >
入力方向の要求に対して要求認証マネージャーを登録します。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<システムの >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<構成 >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthenticationManager >**  
  
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
|種類|<xref:System.Security.Claims.ClaimsAuthenticationManager>クラスから派生するカスタム型を指定します。 `type`属性を指定する方法の詳細については、「[カスタム型参照]」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 `type`属性が存在しない場合、または`type`属性が<xref:System.Security.Claims.ClaimsAuthenticationManager>クラスを`<claimsAuthenticationManager>`参照している場合、要素は子要素を受け取りません<xref:System.Security.Claims.ClaimsAuthenticationManager> 。ただし、から派生したクラスは子構成要素を定義できます。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|サービスレベルの id 設定を指定します。|  
  
## <a name="remarks"></a>Remarks  
 クラスに<xref:System.Security.Claims.ClaimsAuthenticationManager>よって提供される既定の動作では、入力方向の要求がエコーされます。 属性が指定されていない`type`場合、また<xref:System.Security.Claims.ClaimsAuthenticationManager>は属性で`<claimsAuthenticationManager>`クラスが指定されている場合、要素は子要素を受け取りません。 `type` `type`属性を指定して、 <xref:System.Security.Claims.ClaimsAuthenticationManager>クラスから派生した型を登録し、カスタム動作を実装することができます。 派生クラスでは、 `<claimsAuthenticationManager>`要素の子要素を使用した構成をサポートできます。これを行うには、 <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>メソッドをオーバーライドしてこれらの要素を処理します。 子要素に対して定義されているスキーマは、クラスのデザイナーによって作成されます。  
  
 要素`<claimsAuthenticationManager>`は、プロパティ<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>を設定します。  
  
## <a name="example"></a>例  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
