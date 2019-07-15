---
ms.openlocfilehash: 794e43826af8f443a2cbb43b41f233766adc9dfd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802950"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant または Contract.Requires\<TException> が String.IsNullOrEmpty の純粋性を考慮しない

|   |   |
|---|---|
|説明|.NET Framework 4.6.1 が対象のアプリでは、<xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> の不変コントラクトまたは <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> の実行前の状態のコントラクトが <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> メソッドを呼び出した場合、リライターはコンパイラの警告 CC1036:&quot;Detected call to method 'System.String.IsNullOrWhiteSpace(System.String)' without [Pure] in method.&quot; を生成します。これはコンパイラ エラーではなく、コンパイラ警告です。|
|提案される解決策|この動作については [GitHubの問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) で報告されています。 この警告が表示されないようにするには、コード コントラクト ツールのソース コードの更新バージョンを [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) からダウンロードしてコンパイルします。 ページ下部から情報をダウンロードできます。|
|スコープ|マイナー|
|Version|4.6.1|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

