---
ms.openlocfilehash: 01bbc49cb0febc5a29dafc7c311b848387a4094a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803521"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>TextBox/PasswordBox の非装飾選択に SelectionTextBrush パブリック プロパティを追加する

|   |   |
|---|---|
|説明|<xref:System.Windows.Controls.TextBox> と <xref:System.Windows.Controls.PasswordBox> の[非装飾ベースのテキスト選択](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md)を使用する WPF アプリケーションでは、開発者は、選択されたテキストのレンダリングを変更するために、新しく追加された SelectionTextBrush プロパティを設定できるようになりました。  既定では、<xref:System.Windows.SystemColors.HighlightTextBrushKey> でこの色が変更されます。  非装飾ベースのテキスト選択が有効でない場合は、このプロパティで何も行われません。|
|提案される解決策|非装飾ベースのテキスト選択が有効になったら、<xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> および <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> プロパティを使用して、選択されたテキストの外観を変更することができます。 これは XAML を使用して実行できます。<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|スコープ|Major|
|Version|4.8|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|

