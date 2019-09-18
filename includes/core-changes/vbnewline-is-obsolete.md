---
ms.openlocfilehash: 2a0ebcf61fd96df6d2235962c1f1e9cac3fb22e6
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988499"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft.VisualBasic.Constants.vbNewLine は古い

.NET Framework の <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 定数は[廃止](xref:System.ObsoleteAttribute)とマークされていますが、この属性は以前の .NET Core 3.0 ライブラリには存在していませんでした。

#### <a name="version-introduced"></a>導入されたバージョン

.NET Core 3.0 Preview 8

#### <a name="details"></a>説明

.NET Core 3.0 Preview 8 以降では、.NET Framework の `vbNewLine` に準拠するため、[廃止](xref:System.ObsoleteAttribute)属性が <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 定数に適用されています。 `vbNewLine` 定数を使用すると、コンパイラの警告が発生します。 

以前のバージョンの .NET Core では、`vbNewLine` によりコンパイラの警告は発生しませんでした。

#### <a name="recommended-action"></a>推奨される操作

`vbNewLine` に対する[廃止](xref:System.ObsoleteAttribute)属性メッセージには、次の推奨事項が含まれています。

> キャリッジ リターンとライン フィードの場合は、[vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf) を使用します。 現在のプラットフォームの改行の場合は、<xref:System.Environment.NewLine?displayProperty=nameWithType> を使用します。

#### <a name="category"></a>カテゴリ

Visual Basic

#### <a name="affected-apis"></a>影響を受ける API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

