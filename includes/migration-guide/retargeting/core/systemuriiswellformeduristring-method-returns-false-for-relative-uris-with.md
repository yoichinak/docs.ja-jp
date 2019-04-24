---
ms.openlocfilehash: 734041f5921571cd11225a359e794526cbd8d0e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774476"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>最初のセグメントにコロン文字を含む相対 URI に対して System.Uri.IsWellFormedUriString メソッドが false を返す

|   |   |
|---|---|
|説明|.NET Framework 4.5 より、<xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> では、最初のセグメントに <code>:</code> を含む相対 URI が形式が正しくないとして処理されます。 これは .NET Framework 4.0 の <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> 動作からの変更であり、RFC3986 に準拠する目的で行われました。|
|提案される解決策|この変更は (他の多くの URI 変更と同様に) .NET Framework 4.5 (以降) を対象とするアプリケーションにのみ影響を与えます。 以前の動作を維持するには、アプリの対象を .NET Framework 4.0 にします。 あるいは、<xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> を呼び出す前に URI を調べて <code>:</code> 文字を探し、以前の動作が望ましければそれを削除し、正しい形式として処理させます。|
|スコープ|マイナー|
|Version|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType></li></ul>|
