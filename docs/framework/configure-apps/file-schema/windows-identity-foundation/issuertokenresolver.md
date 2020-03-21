---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152672"
---
# <a name="issuertokenresolver"></a>\<>
トークン ハンドラー コレクション内のハンドラーによって使用される発行者トークン リゾルバーを登録します。 発行者トークン リゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。  
  
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
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
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
|type|発行者トークン リゾルバーの種類を指定します。 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスまたはクラスから<xref:System.IdentityModel.Tokens.IssuerTokenResolver>派生する型である必要があります。 必須。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>](securitytokenhandlerconfiguration.md)|セキュリティ トークン ハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>解説  
 発行者トークン リゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。 署名のチェックに使用される暗号資料を取得するために使用されます。 属性を指定する`type`必要があります。 指定する型は、<xref:System.IdentityModel.Tokens.IssuerTokenResolver><xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスから派生するカスタム型のいずれかです。  
  
 トークン ハンドラーによっては、構成で発行者トークン リゾルバーの設定を指定できるものもあります。 個々のトークン ハンドラーの設定は、セキュリティ トークン ハンドラーコレクションで指定された設定をオーバーライドします。  
  
> [!NOTE]
> 要素を`<issuerTokenResolver>` [ \<identityConfiguration>](identityconfiguration.md)要素の子要素として指定することは非推奨になりましたが、下位互換性のために引き続きサポートされています。 要素の設定`<securityTokenHandlerConfiguration>`は、要素上の`<identityConfiguration>`設定よりも優先されます。  
  
## <a name="example"></a>例  
 次の XML は、 から<xref:System.IdentityModel.Tokens.IssuerTokenResolver>派生したカスタム クラスに基づく発行者トークン リゾルバーの構成を示しています。 トークン リゾルバーは、クラスに対して定義されたカスタム構成要素 (`<AddAudienceKeyPair>`) から初期化された対象ユーザーとキーのペアのディクショナリを保持します。 このクラスは、この<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>要素を処理するメソッドをオーバーライドします。 オーバーライドは次の例に示します。ただし、簡潔にするために、呼び出すメソッドは表示されません。 完全な例については、サンプルを`CustomToken`参照してください。  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>例
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
