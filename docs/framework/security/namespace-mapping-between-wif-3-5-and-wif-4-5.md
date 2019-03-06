---
title: WIF 3.5 と WIF 4.5 間での名前空間マッピング
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
ms.openlocfilehash: ef5801ccfdda22b1c89c22ea9c2b14ea0855ed26
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352790"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>WIF 3.5 と WIF 4.5 間での名前空間マッピング

.NET 4.5 以降では、Windows Identity Foundation (WIF) は .NET Framework に完全に統合されています。 この統合により、名前の変更および WIF の名前空間と API サーフェスの統合が行われました。 このトピックでは、いくつかのガイダンスと、WIF 3.5 の名前空間と WIF 4.5 の名前空間の間の一般的なマッピングを示します。 すべてを網羅するものではなく、使い慣れた WIF 3.5 のクラスが WIF 4.5 のどこで見つかるかについての一般的な情報を提供するだけです。 WIF 3.5 と WIF 4.5 の間の違いについては、「[Windows Identity Foundation 4.5 の新機能](../../../docs/framework/security/whats-new-in-wif.md)」を参照してください。 WIF 3.5 を使ってビルドされたアプリケーションを WIF 4.5 に移行する方法のガイダンスについては、「[Guidelines for Migrating an Application Built Using WIF 3.5 to WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)」(WIF 3.5 でビルドされたアプリケーションを WIF 4.5 に移行するためのガイドライン) を参照してください。

## <a name="wif-35-to-wif-45-namespace-map"></a>WIF 3.5 から WIF 4.5 への名前空間のマッピング

WIF 3.5 では `Microsoft.IdentityModel` 名前空間に集められていた WIF のクラスは、WIF 4.5 では `System.Security.Claims`、`System.ServiceModel.Security`、`System.IdentityModel` の各名前空間に分散されています。 さらに、WIF 3.5 の一部の名前空間は、WIF 4.5 では統合されるか完全に削除されています。

> [!IMPORTANT]
> 
  `System.IdentityModel`、<xref:System.IdentityModel.Claims?displayProperty=nameWithType>、および <xref:System.IdentityModel.Policy?displayProperty=nameWithType> という <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> 名前空間には、WCF クレーム ベースの ID モデルを実装するクラスが含まれます。 WCF クレーム ベース ID モデルは WIF に置き換えられています。 WIF に基づいてソリューションをビルドする際は、これら 3 つの名前空間でクラスを使用しないでください。

次の表では、WIF 3.5 のクラスが WIF 4.5 で見つかる場所を示します。

|**WIF 3.5 の名前空間**|**WIF 4.5 の名前空間**|**コメント**|
|-|-|-|
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-   定数を表すほとんどのクラスは実装されません。<br />-   セキュリティ トークン サービスの構築に使われるクラスは、`Microsoft.IdentityModel.SecurityTokenService` から <xref:System.IdentityModel?displayProperty=nameWithType> に移動されました。<br />-   `Microsoft.IdentityModel.Threading` のクラスは、<xref:System.IdentityModel?displayProperty=nameWithType> に移動されました。<br />-   `ExceptionMapper` クラスと `MruSecurityTokenCache` クラスは実装されていません。|
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|-   `IClaimsPrincipal` および `IClaimsIdentity` インターフェイスは、WIF 4.5 では実装されていません。 代わりに、<xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> と <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> が、.NET のほとんどのプリンシパル クラスと ID クラスを派生する基底クラスになっています。 つまり、WIF 4.5 では `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` や `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` などの特殊化された要求プリンシパル クラスおよび ID クラスは必要なく、代わりに <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> および <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> を使います。 WIF 3.5 に存在した他の特殊化された要求プリンシパル クラスおよび ID クラスにも同じことがいえます。<br />-   `Microsoft.IdentityModel.Claims.ClaimsCollection` クラスは WIF 4.5 では実装されていません。 代わりに、要求のコレクションは <xref:System.Security.Claims.Claim?displayProperty=nameWithType> 型の列挙可能なコレクションとして公開されています。<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> および <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> は、LINQ を完全にサポートするようになったメソッドを提供します。|
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|WIF 4.5 では一部の要素とクラスは名前を変更されており、一部は削除されています。たとえば、`Microsoft.IdentityModel.Configuration.ServiceConfiguration` は <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType> になっています。|
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSIdentity`|WIF 4.5 では実装されていません。|WIF 3.5 に含まれていた CardSpace をサポートするためのクラスは、WIF 4.5 では実装されていません。|
|`Microsoft.IdentityModel.Protocols.WSTrust`|<xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> 名前空間と <xref:System.ServiceModel.Security?displayProperty=nameWithType> 名前空間に分割されています。|WS-Trust の成果物を表すクラスは、<xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> 名前空間に含まれます (<xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> クラスなど)。 WCF サービスが WS-Trust プロトコルを使って通信できるようにする WCF サービス コントラクト、サービス ホスト、およびチャネルを表すクラスは、<xref:System.ServiceModel.Security?displayProperty=nameWithType> 名前空間に含まれます (<xref:System.ServiceModel.Security.WSTrustServiceHost> クラスなど)。|
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|WIF 4.5 では実装されていません。|-|
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|WIF 4.5 では実装されていません。|WIF 3.5 では XML 暗号化定数を表すクラスを含みました。 WIF 4.5 では、これらの定数は実装されていません。|
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` クラスおよび定数を表すクラスは実装されていません。|
|`Microsoft.IdentityModel.SecurityTokenService`|<xref:System.IdentityModel?displayProperty=nameWithType>、<xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>、<xref:System.IdentityModel.Tokens?displayProperty=nameWithType> の各名前空間に分割されています。|-|
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|パッシブ (WS-Federation) シナリオの構成を提供するクラスは、ほとんど <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType> に移動されました。ただし、一部のクラスは <xref:System.IdentityModel.Services?displayProperty=nameWithType> に含まれます。|
|`Microsoft.IdentityModel.Web.Controls`|WIF 4.5 では実装されていません。|`Microsoft.IdentityModel.Web.Controls` のクラスはフェデレーション パッシブ サインイン コントロールを実装していましたが、WIF 4.5 には存在しません。|
|`Microsoft.IdentityModel.WindowsTokenService`|WIF 4.5 では実装されていません。|-|

## <a name="see-also"></a>関連項目

- [Windows Identity Foundation 4.5 の新機能](../../../docs/framework/security/whats-new-in-wif.md)
- [WIF 3.5 でビルドされたアプリケーションを WIF 4.5 に移行するためのガイドライン](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
