---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 9f5e0c5ded3d750a1102492c7a506e6d5643b2d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942750"
---
# <a name="identityconfiguration"></a>\<identityConfiguration>

サービスレベルの id 設定を指定します。

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
|name|Id 構成セクションの名前。 この名前を使用して、特定の構成セクションを参照することができます。 `name`属性が指定されていない場合、セクションでは既定の構成を定義します。 既定の構成は、パッシブフェデレーションシナリオでは常に使用されます。 詳細については、「 [ \<federationConfiguration >](federationconfiguration.md)要素」を参照してください。|
|saveBootstrapContext|ブートストラップトークンをセッショントークンに含める必要があるかどうかを指定します。 また、 `saveBootstrapContext` [ \<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)要素の属性を設定することによって、トークンハンドラーコレクションに値を設定することもできます。 トークンハンドラーコレクションに設定された値は、サービスで設定された値よりも優先されます。|
|maximumClockSkew|許容される最大のクロックスキューを指定する。<xref:System.TimeSpan> サインインセッションの有効期限の検証など、時間を区別する操作を実行するときに許容される最大のクロックスキューを制御します。 既定値は5分 "00:05:00" です。 値を指定<xref:System.TimeSpan>する方法の詳細については、「 [Timespan values](../windows-workflow-foundation/index.md)」を参照してください。 SecurityTokenHandlerConfiguration > 要素の`maximumClockSkew`属性[を設定することによって、トークンハンドラーコレクションに最大クロックスキューを設定することもできます。 \<](securitytokenhandlerconfiguration.md) トークンハンドラーコレクションに設定された値は、サービスで設定された値よりも優先されます。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<キャッシュ >](caches.md)|セッショントークンとトークンリプレイ検出に使用されるキャッシュを登録します。 は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。 任意。|
|[\<certificateValidation >](certificatevalidation.md)|トークンハンドラーが証明書を検証するために使用する設定を制御します。 は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。 任意。|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|入力方向の要求に対して要求認証マネージャーを登録します。 任意。|
|[\<claimsAuthorizationManager >](claimsauthorizationmanager.md)|入力方向の要求に対して要求承認マネージャーを登録します。 任意。|
|[\<claimTypeRequired>](claimtyperequired.md)|受信セキュリティトークンに必要な要求のセットを指定します。 任意。|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|セキュリティトークンハンドラーのコレクションを指定します。 セキュリティトークンハンドラーの0個以上のコレクションを指定できます。 任意。|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|トークンリプレイ検出を有効にし、トークンの有効期限を指定します。 は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。 任意。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|アプリケーションで Windows Identity Foundation (WIF) オプションを有効にするための構成を提供します。|

## <a name="remarks"></a>Remarks

複数の id 構成を定義し、それぞれに一意の名前を指定できます。 動作は次のとおりです。

1. `<identityConfiguration>`要素が指定されていない場合は。 既定の id 構成は、実行時に作成され、既定値が設定されます。

2. 1つ`<identityConfiguration>`の要素が指定されている場合。 これは既定の id 構成です。 名前が付けられているか名前が付いていないかは関係ありません。

3. 複数`<identityConfiguration>`の要素が指定されている場合。 無名の要素は、既定の id 構成を指定します。 複数`<identityConfiguration>`の要素を指定する場合は、そのうちの1つを名前のないものにすることをお勧めします。

> [!WARNING]
> 複数`<identityConfiguration>`の要素を指定する場合は、そのうちの1つを名前なしにする必要があります。 名前のない要素が既定の id 構成になります。

 `<identityConfiguration>`要素で指定された設定の一部は、セキュリティトークンハンドラーコレクションの設定、または個々のセキュリティトークンハンドラーの設定によって上書きできます。

> [!IMPORTANT]
> クラスまたは<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>クラスを使用して、コードにクレームベースのアクセス制御を提供する場合、 `<federationConfiguration>`要素によって参照される id 構成によって、要求承認マネージャーと、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>承認の決定。 これは、Windows Communication Foundation (WCF) アプリケーションや Web ベースではないアプリケーションなど、パッシブな Web シナリオではないシナリオでも当てはまります。 アプリケーションがパッシブな Web アプリケーション[ \<](claimsauthorizationmanager.md)でない場合は、参照される id 構成の claimsAuthorizationManager > 要素 (およびその子ポリシー要素が存在する場合) が適用される唯一の設定です。 その他の設定はすべて無視されます。 詳細については、「 [ \<federationConfiguration >](federationconfiguration.md)要素」を参照してください。

要素は、 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>クラスによって表されます。 `<identityConfiguration>` Id 構成セクションは、 <xref:System.IdentityModel.Configuration.IdentityConfiguration>クラスによって表されます。

> [!IMPORTANT]
> `<identityConfiguration>`要素の子要素として次の要素を指定することは非推奨とされますが、旧バージョンとの互換性のために動作は引き続きサポートされています。 代わりに、これらの要素を[ \<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)要素の下に指定する必要があります。
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry >](issuernameregistry.md)
> - [\<issuerTokenResolver >](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

## <a name="example"></a>例

次の例では、"alternateConfiguration" という名前の id 構成を作成します。 Id 構成では、既定の設定を指定します。

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
