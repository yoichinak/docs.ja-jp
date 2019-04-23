---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: ae263a4590cc523c64306ff5d53e54b5190ca510
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202522"
---
# <a name="issuernameregistry"></a>\<issuerNameRegistry>
トークン ハンドラー コレクションのハンドラーによって使用される発行者名レジストリを構成します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
  
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
|型|派生した型、<xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラス。 詳細については、ユーザー設定を指定する方法についての`type`、[カスタム型の参照] を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|ときに、`type`属性が構成ベースの発行者名レジストリを指定します (、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラス)、 [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)要素を指定する必要があります。 [ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)要素がかかる`<add>`、 `<clear>`、または`<remove>`要素の子要素として。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラー コレクションのセキュリティの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 すべての発行者トークンは、発行者名レジストリを使用して検証されます。 これはオブジェクトから派生した、<xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラス。 発行者名レジストリを使用して、対応する発行者によって生成されたトークンの署名を検証するために必要な暗号化マテリアルにニーモニック名を関連付けます。 発行者名レジストリは、証明書利用者 (RP) アプリケーションによって信頼されている発行者の一覧を保持します。 使用して、発行者名レジストリの種類を指定、`type`属性。 `<issuerNameRegistry>`要素は、指定した型の構成を提供する 1 つまたは複数の子要素を持つことができます。 これらの子要素をオーバーライドすることで処理するロジックを提供する、<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>メソッド。  
  
 WIF には単一の発行者名レジストリの種類をすぐに使える、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラス。 このクラスは、一連の構成で指定されている信頼された発行者の証明書を使用します。 構成の子要素に要する`<trustedIssuers>`、信頼された発行者の証明書のコレクションが構成されています。 証明書が指定の ASN.1 を使用してエンコードされた証明書の拇印の形式とが追加または削除、コレクションからを使用して信頼された`<add>`、 `<clear>`、または`<remove>`要素。  
  
 `<issuerNameRegistry>`要素が表される、<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>クラス。  
  
> [!NOTE]
>  指定する、`<issuerNameRegistry>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は非推奨とされましたが、旧バージョンとの互換性もサポートします。 上の設定、`<securityTokenHandlerConfiguration>`要素のオーバーライド、`<identityConfiguration>`要素。  
  
## <a name="example"></a>例  
 次の XML では、名前のレジストリをベースの構成の発行者を指定する方法を示します。  
  
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
