---
title: <serviceAuthorization> 要素
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: b73e2049afb460bf9be8b76ee272ba0547b61453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936400"
---
# <a name="serviceauthorization-element"></a>\<serviceAuthorization > 要素
サービス操作へのアクセスを許可する設定を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceAuthorization >  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|impersonateCallerForAllOperations|サービスのすべての操作が呼び出し元を偽装するかどうかを指定するブール値。 既定値は `false` です。<br /><br /> 特定のサービス操作が呼び出し元を偽装する場合、スレッド コンテキストは、指定されたサービスを実行する前に呼び出し元のコンテキストに切り替えられます。|  
|principalPermissionMode|サーバーでの操作を実行するために使用されるプリンシパルを設定します。 次の値があります。<br /><br /> -なし<br />-UseWindowsGroups<br />-UseAspNetRoles<br />-カスタム<br /><br /> 既定値は UseWindowsGroups です。 値は、<xref:System.ServiceModel.Description.PrincipalPermissionMode> 型です。 この属性の使用方法の詳細につい[ては、「方法:PrincipalPermissionAttribute クラス](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)を使用してアクセスを制限します。|  
|roleProviderName|Windows Communication Foundation (WCF) アプリケーションにロール情報を提供するロール プロバイダーの名前を指定する文字列。 既定値は空の文字列です。|  
|ServiceAuthorizationManagerType|サービス承認マネージャーの型を含む文字列。 詳細については、「 <xref:System.ServiceModel.ServiceAuthorizationManager> 」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|authorizationPolicies|`add` キーワードを使用して追加できる承認ポリシーの種類のコレクションを含みます。 各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。 この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。 アクセス制御は、それに基づいて許可または拒否されます。 詳細については、「 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement> 」を参照してください。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|サービスの動作設定のコレクションが含まれています。|  
  
## <a name="remarks"></a>Remarks  
 このセクションには、承認、カスタム ロール プロバイダー、および偽装に影響する要素が含まれています。  
  
 `principalPermissionMode` 属性は、保護メソッドの使用を承認するときに使用するユーザー グループを指定します。 既定値は `UseWindowsGroups` で、リソースにアクセスしようとしている ID を、"Administrators" や "Users" などの Windows グループから検索するように指定します。 次のコードに`UseAspNetRoles`示すように、system.web > 要素の\<下に構成されているカスタムロールプロバイダーを使用するように指定することもできます。  
  
```xml  
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```  
  
 `roleProviderName` 属性で `principalPermissionMode` を使用する方法を次のコードに示します。  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 この構成要素の使用例については、「[サービス操作](../../../wcf/samples/authorizing-access-to-service-operations.md)と[承認ポリシー](../../../wcf/samples/authorization-policy.md)へのアクセスの承認」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [セキュリティ動作](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [サービス操作へのアクセスの承認](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [方法: サービスのカスタム承認マネージャーを作成する](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [方法: PrincipalPermissionAttribute クラスを使用してアクセスを制限する](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [承認ポリシー](../../../wcf/samples/authorization-policy.md)
