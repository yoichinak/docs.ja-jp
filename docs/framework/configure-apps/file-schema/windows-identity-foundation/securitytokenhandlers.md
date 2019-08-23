---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942459"
---
# <a name="securitytokenhandlers"></a>\<securityTokenHandlers>
エンドポイントに登録されているセキュリティトークンハンドラーのコレクションを指定します。  
  
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
|name|トークンハンドラーコレクションの名前を指定します。 フレームワークによって認識される値は、"ActAs" と "OnBehalfOf" だけです。 これらのいずれかの名前でトークンハンドラーコレクションが指定されている場合、ActAs または OnBehalfOf トークンをそれぞれ処理するときにコレクションが使用されます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](add.md)|トークンハンドラーコレクションにセキュリティトークンハンドラーを追加します。|  
|[\<clear>](clear.md)|すべてのセキュリティトークンハンドラーをトークンハンドラーコレクションから削除します。|  
|[\<remove>](remove.md)|トークンハンドラーコレクションからセキュリティトークンハンドラーを削除します。|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|トークンハンドラーのコレクションの構成を提供します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|サービスレベルの id 設定を指定します。|  
  
## <a name="remarks"></a>Remarks  
 サービス構成では、セキュリティトークンハンドラーの1つ以上の名前付きコレクションを指定できます。 `name`属性を使用して、コレクションの名前を指定できます。 フレームワークによって処理される名前は、"ActAs" と "OnBehalfOf" だけです。 これらのコレクションにハンドラーが存在する場合は、 `ActAs` `OnBehalfOf`トークンの処理時に既定のハンドラーではなく、Security Token Service (STS) によって使用されます。  
  
 既定では<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>、コレクションには<xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>、、、、、 、およびの各ハンドラー型が設定されます。<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> コレクションは、 `<add>` `<remove>`、、および`<clear>`の各要素を使用して変更できます。 コレクション内に存在する特定の種類のハンドラーが1つだけであることを確認する必要があります。 たとえば、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラスからハンドラーを派生させる場合、ハンドラーまたはが<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 1 つのコレクションで構成されていることがありますが、両方を構成することはできません。  
  
 コレクション内`<securityTokenHandlerConfiguration>`のハンドラーの構成設定を指定するには、要素を使用します。 この要素によって指定された設定は、サービスで指定された設定よりも、ユーザー [ \<構成 >](identityconfiguration.md)要素を介してオーバーライドされます。 いくつかの組み込みハンドラー型を含む一部のハンドラーは、 `<add>`要素の子要素を通じて追加の構成をサポートできます。 ハンドラーに指定された設定は、コレクションまたはサービスで指定された同等の設定よりも優先されます。
