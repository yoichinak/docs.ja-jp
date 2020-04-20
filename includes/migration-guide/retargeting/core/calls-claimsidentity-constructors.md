---
ms.openlocfilehash: c10d617e07ca2fa0239298d449d93cf833b83fce
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274932"
---
### <a name="calls-to-claimsidentity-constructors"></a>ClaimsIdentity コンストラクターを呼び出す

|   |   |
|---|---|
|説明|.NET Framework 4.6.2 以降、<xref:System.Security.Claims.ClaimsIdentity> コンストラクターと <xref:System.Security.Principal.IIdentity?displayProperty=name> パラメーターの組み合わせで <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> プロパティが設定されるしくみに変更があります。 <xref:System.Security.Principal.IIdentity?displayProperty=name> 引数が <xref:System.Security.Claims.ClaimsIdentity> オブジェクトで、その <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> オブジェクトの <xref:System.Security.Claims.ClaimsIdentity> プロパティが <code>null</code> ではない場合、<xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> メソッドを使用して <xref:System.Security.Claims.ClaimsIdentity.Clone> プロパティがアタッチされます。 Framework 4.6.1 以前のバージョンでは、<xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> プロパティは既存の参照として付けられます。この変更によって、.NET Framework 4.6.2 以降、新しい <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> オブジェクトの <xref:System.Security.Claims.ClaimsIdentity> プロパティはコンストラクターの <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 引数の <xref:System.Security.Principal.IIdentity?displayProperty=name> プロパティとは等しくなくなります。 .NET Framework 4.6.1 以前のバージョンでは、等しくなります。|
|提案される解決策|この動作が望ましくない場合、アプリケーション構成ファイルで <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> スイッチを <code>true</code> に設定して以前の動作を復元することができます。 この場合、web.config ファイルの <code>&lt;runtime&gt;</code> セクションに次を追加します。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|バージョン|4.6.2|
|[種類]|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)></li></ul>|
