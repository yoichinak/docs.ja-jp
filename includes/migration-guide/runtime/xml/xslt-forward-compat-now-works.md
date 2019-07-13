---
ms.openlocfilehash: 2dd97fcce13ed1ac7baf4cd02f5881d31d7a9c4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804363"
---
### <a name="xslt-forward-compat-now-works"></a>XSLT 上位互換が機能するようになった

|   |   |
|---|---|
|説明|.NET Framework 4 では、XSLT 1.0 の上位互換性に、次の問題がありました。<ul><li>バージョンが 2.0 に設定されているときに、パーサーが認識できない XSLT 1.0 コンストラクトに遭遇すると、スタイル シートの読み込みが失敗していました。</li><li>スタイル シートのバージョンが 1.1 に設定されている場合、<code>xsl:sort</code> コンストラクトでデータを並べ替えることができませんでした。</li></ul>.NET Framework 4.5 では、これらの問題は修正され、XSLT 1.0 の上位互換モードが正常に機能するようになりました。|
|提案される解決策|ほとんどのアプリには影響しませんが、xsl:sort が優先される場合は異なる方法でデータが並べ替えられます。 <code>xsl:sort</code> が 1.1 スタイル シートで使用されている場合は、アプリが並べ替えられていないデータの順序に依存していないことを確認してください。 アプリが 4.0 の並べ替え動作に依存している場合は、スタイル シートから <code>xsl:sort</code> を削除してください。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
