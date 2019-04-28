---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 59d47eda97e97629408ece12a1d1dfbe804feb3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667315"
---
# <a name="claimsauthorizationmanager"></a>\<claimsAuthorizationManager >
入力方向の要求のクレーム承認マネージャーを登録します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthorizationManager >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|種類|派生したカスタム型、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラス。 詳細を指定する方法については、`type`属性は、「[カスタム型の参照](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)します。|  
  
### <a name="child-elements"></a>子要素  
 ある場合ありません`type`属性、または、`type`属性参照、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラス、`<claimsAuthorizationManager>`要素は子要素を取りません。 ただし、から派生したクラス<xref:System.Security.Claims.ClaimsAuthorizationManager>子構成要素を定義できます。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの id の設定を指定します。|  
  
## <a name="remarks"></a>Remarks  
 によって提供される既定の動作、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラスは常に、入力方向の要求を承認します。 いない場合`type`属性が指定されて場合は、`type`属性を指定します、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラス、`<claimsAuthorizationManager>`要素は子要素を取りません。 指定することができます、`type`から派生した型を登録する属性、<xref:System.Security.Claims.ClaimsAuthorizationManager>カスタム動作を実装するクラス。 派生クラスの子要素を使用した構成をサポートできる、`<claimsAuthorizationManager>`要素をオーバーライドすることで、<xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>これらの要素を処理するメソッド。 子要素に対して定義されているスキーマは、最大クラスのデザイナーです。  
  
> [!IMPORTANT]
>  使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コードによって参照される id の構成で信頼性情報ベースのアクセス制御を提供するクラス、`<federationConfiguration>`要素は、クレーム承認マネージャーとを使用して、ポリシーを構成します。承認の判断。 これは Windows Communication Foundation (WCF) アプリケーションまたは Web ベースでないアプリケーションなど、受動的な Web シナリオではないシナリオであっても、当てはまります。 アプリケーションが、パッシブの Web アプリケーションではない場合、`<claimsAuthorizationManager>`要素 (とその子ポリシー要素、存在する場合) の参照先の id 構成だけに適用される設定。 その他のすべての設定は無視されます。 詳細については、次を参照してください。、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。  
  
 この要素の設定、<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType>プロパティ。  
  
## <a name="example"></a>例  
 次の XML では、リソースの操作を実行する、要求元が持つ必要があるクレームのブール型の組み合わせを指定のリソースとアクションのペアから成るポリシーを実装するマネージャー要求の承認の構成を示します。 このポリシーを使用できるクレーム承認マネージャーを実装するコードが記載されて、`ClaimsBasedAuthorization`サンプル。  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
