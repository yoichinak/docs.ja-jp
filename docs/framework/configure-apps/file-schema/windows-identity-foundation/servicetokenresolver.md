---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152581"
---
# <a name="servicetokenresolver"></a>\<>
トークン ハンドラー コレクション内のハンドラーによって使用されるサービス トークン リゾルバーを登録します。 サービス トークン リゾルバーは、受信トークンとメッセージの暗号化トークンを解決するために使用されます。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<id構成>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>**  
  
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
|type|サービス トークン リゾルバーの種類を指定します。 <xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスから派生する<xref:System.IdentityModel.Selectors.SecurityTokenResolver>型または型。 `type`属性の指定方法の詳細については、「[カスタム型参照]」を参照してください。 必須。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>](securitytokenhandlerconfiguration.md)|セキュリティ トークン ハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>解説  
 サービス トークン リゾルバーを使用して、受信トークンとメッセージの暗号化トークンを解決できます。 これは、受信トークンの暗号化を解除するために使用するキーを取得するために使用されます。 属性を指定する`type`必要があります。 指定する型は、<xref:System.IdentityModel.Selectors.SecurityTokenResolver><xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスから派生するカスタム型のいずれかです。  
  
 一部のトークン ハンドラーでは、構成でサービス トークン リゾルバーの設定を指定できます。 個々のトークン ハンドラーの設定は、セキュリティ トークン ハンドラーコレクションで指定された設定をオーバーライドします。  
  
> [!NOTE]
> 要素を`<serviceTokenResolver>` [ \<identityConfiguration>](identityconfiguration.md)要素の子要素として指定することは非推奨になりましたが、下位互換性のために引き続きサポートされています。 要素の設定`<securityTokenHandlerConfiguration>`は、要素上の`<identityConfiguration>`設定よりも優先されます。  
  
## <a name="example"></a>例  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
