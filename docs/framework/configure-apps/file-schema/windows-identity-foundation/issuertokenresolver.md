---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: da591940910b16d42ef8ab1a05c4b244dbe543f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942628"
---
# <a name="issuertokenresolver"></a>\<issuerTokenResolver >
トークンハンドラーコレクションのハンドラーによって使用される発行者トークンリゾルバーを登録します。 発行者トークンリゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<issuerTokenResolver >  
  
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
|種類|発行者トークンリゾルバーの種類を指定します。 は、クラスまた<xref:System.IdentityModel.Tokens.IssuerTokenResolver>は<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスから派生した型のいずれかである必要があります。 必須。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 発行者トークンリゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。 署名の確認に使用される暗号化マテリアルを取得するために使用されます。 `type`属性を指定する必要があります。 指定できる型は、また<xref:System.IdentityModel.Tokens.IssuerTokenResolver>は<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスから派生したカスタム型のいずれかです。  
  
 一部のトークンハンドラーでは、構成で発行者トークンリゾルバーの設定を指定できます。 個々のトークンハンドラーの設定は、セキュリティトークンハンドラーコレクションで指定された設定よりも優先されます。  
  
> [!NOTE]
> 要素を、指定した[ \<>](identityconfiguration.md)要素の子要素として指定することは推奨されていませんが、旧バージョンとの互換性のためにサポートされています。 `<issuerTokenResolver>` 要素の設定`<securityTokenHandlerConfiguration>`は、要素の設定`<identityConfiguration>`よりも優先されます。  
  
## <a name="example"></a>例  
 次の XML は、から<xref:System.IdentityModel.Tokens.IssuerTokenResolver>派生したカスタムクラスに基づく発行者トークンリゾルバーの構成を示しています。 トークンリゾルバーは、クラスに対して定義されているカスタム構成要素 (`<AddAudienceKeyPair>`) から初期化される、ユーザーとキーのペアのディクショナリを保持します。 クラスは、 <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>メソッドをオーバーライドしてこの要素を処理します。 オーバーライドを次の例に示します。ただし、簡潔にするために呼び出すメソッドは表示されません。 完全な例については`CustomToken` 、「」のサンプルを参照してください。  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>例  
  
```  
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
