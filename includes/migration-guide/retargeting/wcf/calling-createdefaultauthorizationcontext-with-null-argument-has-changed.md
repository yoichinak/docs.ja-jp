---
ms.openlocfilehash: 9ec5fa379556dedeaa7a35e34f004340ab47a39c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234418"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>null 引数を指定した CreateDefaultAuthorizationContext の呼び出しが変更されました

|   |   |
|---|---|
|説明|null の authorizationPolicies 引数を指定した <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> の呼び出しによって返される <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> の実装が、.NET Framework 4.6 で変更されました。|
|提案される解決策|まれに、カスタム認証を使用する WCF アプリの動作に違いが生じる可能性があります。 このような場合は、2 つの方法のいずれかで、以前の動作を復元できます。<ol><li>4.6 よりも前のバージョンの .NET Framework を対象とするようにアプリを再コンパイルする。 IIS でホストされるサービスの場合、&lt;httpRuntime targetFramework=&quot;x.x&quot; /&gt; 要素を使用して、以前のバージョンの .NET Framework を対象とする。</li><li>app.config ファイルの <code>&lt;appSettings&gt;</code> セクションに以下の行を追加します。 <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|スコープ|マイナー|
|Version|4.6|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|
