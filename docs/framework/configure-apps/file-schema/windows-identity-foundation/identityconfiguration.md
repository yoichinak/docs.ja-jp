---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 91d64ce0d6a5cdbf32fec4a476fb111afe9a7952
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212496"
---
# <a name="identityconfiguration"></a>\<identityConfiguration>

サービス レベルの id の設定を指定します。

 \<system.identityModel>\
\<identityConfiguration>

## <a name="syntax"></a>構文

```xml
<system.identityModel>
  <identityConfiguration
      name=xs:string
      saveBootstrapContext=xs:boolean>
      maximumClockSkew=TimeSpan >
  </identityConfiguration>
</system.identityModel>
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|name|Id の構成セクションの名前。 この名前を使用して、特定の構成セクションを参照することができます。 ない場合は`name`属性を指定すると、セクションは、既定の構成を定義します。 既定の構成は常に、パッシブ フェデレーション シナリオの使用します。 詳細については、次を参照してください。、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。|
|saveBootstrapContext|セッション トークンにブートス トラップ トークンを含める必要があるかどうかを指定します。 設定して、値がトークン ハンドラー コレクションに設定することも可能性があります、`saveBootstrapContext`属性を[ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。 トークン ハンドラー コレクションに設定値は、サービスの設定値をオーバーライドします。|
|maximumClockSkew|A<xref:System.TimeSpan>許可されている最大のクロック スキューを指定します。 サインイン セッションの有効期限の検証などの時間を区別する操作を実行するときは、最大の許可されている時刻のずれを制御します。 既定値は 5 分間、"00: 継続"。 指定する方法の詳細についての<xref:System.TimeSpan>値を参照してください[Timespan 値](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)します。 設定して、最大クロック スキューがトークン ハンドラー コレクションに設定することも可能性があります、`maximumClockSkew`属性を[ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。 トークン ハンドラー コレクションに設定値は、サービスの設定値をオーバーライドします。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<caches>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|セッション トークンやトークン リプレイ検出のために使用されるキャッシュを登録します。 サービス レベルまたはセキュリティ トークン ハンドラー コレクションに指定できます。 任意。|
|[\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|トークン ハンドラーを使用して証明書の検証の設定を制御します。 サービス レベルまたはセキュリティ トークン ハンドラー コレクションに指定できます。 任意。|
|[\<claimsAuthenticationManager>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|入力方向の要求のクレーム認証マネージャーを登録します。 任意。|
|[\<claimsAuthorizationManager>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|入力方向の要求のクレーム承認マネージャーを登録します。 任意。|
|[\<claimTypeRequired>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|必要な受信セキュリティ トークンのクレームのセットを指定します。 任意。|
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|セキュリティ トークン ハンドラーのコレクションを指定します。 セキュリティ トークン ハンドラーの 0 個以上のコレクションを指定することができます。 任意。|
|[\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|トークン リプレイ検出が有効にし、トークンの有効期限を指定します。 サービス レベルまたはセキュリティ トークン ハンドラー コレクションに指定できます。 任意。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|アプリケーションの Windows Identity Foundation (WIF) オプションを有効にするための構成を提供します。|

## <a name="remarks"></a>Remarks

それぞれに一意の名前を複数の id 構成を定義することがあります。 動作は次のとおりです。

1. ない場合は`<identityConfiguration>`要素が指定されています。 既定の id 構成では、実行時に作成され、既定値が入力されます。

2. 場合、1 つ`<identityConfiguration>`要素が指定されています。 既定の id 構成することをお勧めします。 という名前または名前のないかどうかは関係ありません。

3. 複数`<identityConfiguration>`の要素を指定します。 名前のない要素には、既定の id 構成を指定します。 お勧めする複数指定するときに`<identityConfiguration>`要素、うち 1 つはならない名前付き。

> [!WARNING]
> 複数指定する場合`<identityConfiguration>`要素、うち 1 つはならない名前付き。 名前のない要素が既定の id 構成になります。

 指定された設定の一部、`<identityConfiguration>`要素は、セキュリティ トークン ハンドラー コレクションの設定によって、または個々 のセキュリティ トークン ハンドラーの設定によってオーバーライドできます。

> [!IMPORTANT]
> 使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コードによって参照される id の構成で信頼性情報ベースのアクセス制御を提供するクラス、`<federationConfiguration>`要素は、クレーム承認マネージャーとを使用して、ポリシーを構成します。承認の判断。 これは Windows Communication Foundation (WCF) アプリケーションまたは Web ベースでないアプリケーションなど、受動的な Web シナリオではないシナリオであっても、当てはまります。 アプリケーションが、パッシブの Web アプリケーションではない場合、 [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)要素 (とその子ポリシー要素、存在する場合) の参照先の id 構成だけに適用される設定。 その他のすべての設定は無視されます。 詳細については、次を参照してください。、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。

`<identityConfiguration>`要素が表される、<xref:System.IdentityModel.Configuration.IdentityConfigurationElement>クラス。 Id の構成セクションがによって表される、<xref:System.IdentityModel.Configuration.IdentityConfiguration>クラス。

> [!IMPORTANT]
> 子要素として、次の要素を指定する、`<identityConfiguration>`動作は旧バージョンとの互換性のため引き続きサポートされています。 要素は推奨されていません。 これらの要素を指定する必要があります、代わりに、 [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。
>
> - [\<audienceUris>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)
> - [\<issuerNameRegistry>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)
> - [\<issuerTokenResolver>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)
> - [\<serviceTokenResolver>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)

## <a name="example"></a>例

次の例では、"alternateConfiguration"をという名前の id 構成を作成します。 Id の構成では、既定の設定を指定します。

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
