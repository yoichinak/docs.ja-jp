---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: a5af3893ab72d23c2b3814569decfc50431b8e55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793836"
---
# <a name="securitytokenhandlers"></a>\<securityTokenHandlers>
エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|トークン ハンドラー コレクションの名前を指定します。 フレームワークによって認識される唯一の値は、"ActAs"と"OnBehalfOf"です。 トークン ハンドラー コレクションにこれらの名前のいずれかを指定する場合、コレクションをそれぞれトークン ActAs または OnBehalfOf を処理するときに使用します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|トークン ハンドラー コレクションには、セキュリティ トークン ハンドラーを追加します。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|トークン ハンドラー コレクションからすべてのセキュリティ トークン ハンドラーをクリアします。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|トークン ハンドラー コレクションからセキュリティ トークン ハンドラーを削除します。|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラーのコレクションの構成を提供します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの id の設定を指定します。|  
  
## <a name="remarks"></a>Remarks  
 サービス構成では、セキュリティ トークン ハンドラーの 1 つまたは複数の名前付きコレクションを指定できます。 使用してコレクションの名前を指定することができます、`name`属性。 フレームワークを処理する唯一の名前とは、"ActAs"と"OnBehalfOf"です。 ハンドラーは、これらのコレクションに存在する場合で使用されるセキュリティ トークン サービス (STS)、既定のハンドラーではなく処理するときに`ActAs`と`OnBehalfOf`トークンです。  
  
 既定では、コレクションは、次の種類のハンドラーで設定されます: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、および<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>します。 使用して、コレクションを変更することができます、 `<add>`、 `<remove>`、および`<clear>`要素。 特定の型の 1 つのハンドラーのみがコレクションに存在することを確認する必要があります。 たとえば、次のハンドラーからの派生、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラスか、ハンドラーまたは<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>両方ではなく 1 つのコレクションで構成することがあります。  
  
 使用して、`<securityTokenHandlerConfiguration>`要素をコレクション内で、ハンドラーの構成設定を指定します。 この要素で指定された設定をオーバーライドを通じてサービスに指定されている、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。 いくつかのハンドラー (いくつかの組み込みハンドラー型を含む) の子要素を追加の構成をサポートできる、`<add>`要素。 ハンドラーで指定した設定では、コレクションまたはサービスに指定した同等の設定をオーバーライドします。
