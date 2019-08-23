---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942664"
---
# <a name="issuernameregistry"></a>\<issuerNameRegistry >
トークンハンドラーコレクションのハンドラーによって使用される発行者名レジストリを構成します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
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
|型|<xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラスから派生する型。 カスタム`type`を指定する方法の詳細については、「[カスタム型参照]」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<trustedIssuers >](trustedissuers.md)|属性で`type`構成ベースの発行者名レジストリ<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (クラス) [ \<](trustedissuers.md)を指定する場合は、trustedIssuers > 要素を指定する必要があります。 TrustedIssuers > 要素は、、 `<add>` `<clear>`、または`<remove>`要素を子要素として受け取ることができます。 [ \<](trustedissuers.md)|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 発行者のトークンはすべて、発行者名レジストリを使用して検証されます。 これは、 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラスから派生するオブジェクトです。 発行者名レジストリは、対応する発行者によって生成されるトークンの署名を検証するために必要な暗号マテリアルにニーモニック名を関連付けるために使用されます。 発行者名レジストリは、証明書利用者 (RP) アプリケーションによって信頼されている発行者の一覧を保持します。 発行者名レジストリの種類は、 `type`属性を使用して指定されます。 要素`<issuerNameRegistry>`は、指定された型の構成を提供する1つ以上の子要素を持つことができます。 これらの子要素を処理するロジックは、 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>メソッドをオーバーライドすることによって指定します。  
  
 WIF では、単一の発行者名のレジストリの<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>種類が、クラスのすぐに使用できます。 このクラスは、構成で指定された信頼された発行者証明書のセットを使用します。 これには、信頼され`<trustedIssuers>`た発行元の証明書のコレクションを構成する子構成要素が必要です。 信頼された証明書は、asn.1 でエンコードされた証明書の拇印を使用して指定され`<add>`、 `<clear>`、、 `<remove>`または要素を使用してコレクションに追加または削除されます。  
  
 要素は、 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>クラスによって表されます。 `<issuerNameRegistry>`  
  
> [!NOTE]
> 要素を、指定した[ \<>](identityconfiguration.md)要素の子要素として指定することは推奨されていませんが、旧バージョンとの互換性のためにサポートされています。 `<issuerNameRegistry>` 要素の設定`<securityTokenHandlerConfiguration>`は、要素の設定`<identityConfiguration>`よりも優先されます。  
  
## <a name="example"></a>例  
 次の XML は、構成ベースの発行者名レジストリを指定する方法を示しています。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
