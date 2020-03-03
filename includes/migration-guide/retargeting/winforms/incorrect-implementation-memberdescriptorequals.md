---
ms.openlocfilehash: 2413e1997b6e729b9d5889677e25254aaa24afea
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859338"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>MemberDescriptor.Equals の不適切な実装

|   |   |
|---|---|
|説明|<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> メソッドの元の実装によって、比較対象のオブジェクトからの 2 つの異なる文字列プロパティである、カテゴリ名と説明文字列が比較されます。 この修正は、最初のオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Category> と 2 番目のオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Category> を比較し、最初のオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Description> と 2 番目のオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Description> を比較するものです。|
|提案される解決策|記述子が等しいときに <code>false</code> を返すことがある <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> にアプリケーションが依存しているとき、.NET Framework のバージョン 4.6.2 以降を対象とする場合、いくつかの選択肢があります。<ol><li>コードを変更し、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> メソッドの呼び出しに加え、<xref:System.ComponentModel.MemberDescriptor.Category> フィールドと <xref:System.ComponentModel.MemberDescriptor.Description> フィールドを手動で比較します。</li><li>app.config ファイルに次の値を追加し、この変更を無効にします。</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>アプリケーションの対象が .NET Framework 4.6.1 以前であるが .NET Framework 4.6.2 以降で実行しているとき、この変更を有効にする場合、app.config ファイルに次の値を追加することで互換性スイッチを <code>false</code> に設定します。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.6.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

