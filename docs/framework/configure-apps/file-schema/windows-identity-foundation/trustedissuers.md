---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944273"
---
# <a name="trustedissuers"></a>\<trustedIssuers >
構成ベースの発行者名レジストリ (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>) によって使用される、信頼された発行者の証明書の一覧を構成します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
\<trustedIssuers >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|信頼された発行者のコレクションに証明書を追加します。 証明書は`thumbprint`属性で指定されます。 この属性は必須であり、証明書の拇印の asn.1 エンコード形式を含んでいる必要があります。 `name`属性は省略可能で、証明書のフレンドリ名を指定するために使用できます。|  
|`<clear>`|信頼された発行者のコレクションからすべての証明書を削除します。|  
|`<remove thumbprint=xs:string>`|信頼された発行者のコレクションから証明書を削除します。 証明書は`thumbprint`属性で指定されます。 この属性は必須です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](issuernameregistry.md)|発行者名レジストリを構成します。 **重要:** 要素`type` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>の属性は、 `<trustedIssuers>`要素を有効にするためにクラスを参照する必要があります。 `<issuerNameRegistry>`|  
  
## <a name="remarks"></a>Remarks  
 Windows Identity Foundation (WIF) は、クラスの1つ<xref:System.IdentityModel.Tokens.IssuerNameRegistry>の実装を、 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラスのすぐに使用できるようにします。 構成発行者名レジストリは、構成から読み込まれる信頼された発行者の一覧を保持します。 リストでは、発行者によって生成されたトークンの署名を検証するために必要な x.509 証明書に各発行者名が関連付けられます。 信頼された発行者の証明書の`<trustedIssuers>`一覧は、要素の下で指定されます。 リスト内の各要素は、ニーモニック発行者名と、その発行者によって生成されるトークンの署名を検証するために必要な x.509 証明書を関連付けます。 信頼された証明書は、asn.1 エンコード形式の証明書の拇印を使用して指定さ`<add>`れ、要素を使用してコレクションに追加されます。 要素`<clear>` と`<remove>`要素を使用して、一覧から発行者 (証明書) を消去または削除できます。  
  
 要素`type` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>の属性は、 `<trustedIssuers>`要素を有効にするためにクラスを参照する必要があります。 `<issuerNameRegistry>`  
  
## <a name="example"></a>例  
 次の XML は、構成ベースの発行者名レジストリを指定する方法を示しています。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
