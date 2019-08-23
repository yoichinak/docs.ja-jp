---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923104"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver >
トークンハンドラーコレクションのハンドラーによって使用されるサービストークンリゾルバーを登録します。 サービストークンリゾルバーは、受信トークンとメッセージの暗号化トークンを解決するために使用されます。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|型|サービストークンリゾルバーの種類を指定します。 クラスから派生した型または型。<xref:System.IdentityModel.Selectors.SecurityTokenResolver> <xref:System.IdentityModel.Selectors.SecurityTokenResolver> `type`属性を指定する方法の詳細については、「[カスタム型参照]」を参照してください。 必須。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 サービストークンリゾルバーを使用して、受信トークンとメッセージの暗号化トークンを解決できます。 これは、受信トークンの暗号化を解除するために使用する必要があるキーを取得するために使用されます。 `type`属性を指定する必要があります。 指定できる型は、また<xref:System.IdentityModel.Selectors.SecurityTokenResolver>は<xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスから派生したカスタム型のいずれかです。  
  
 一部のトークンハンドラーでは、構成でサービストークンリゾルバーの設定を指定できます。 個々のトークンハンドラーの設定は、セキュリティトークンハンドラーコレクションで指定された設定よりも優先されます。  
  
> [!NOTE]
> 要素を、指定した[ \<>](identityconfiguration.md)要素の子要素として指定することは推奨されていませんが、旧バージョンとの互換性のためにサポートされています。 `<serviceTokenResolver>` 要素の設定`<securityTokenHandlerConfiguration>`は、要素の設定`<identityConfiguration>`よりも優先されます。  
  
## <a name="example"></a>例  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
