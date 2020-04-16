---
title: コントロールのスタイルを作成する
description: Windows プレゼンテーション ファンデーションおよび .NET Core でコントロール スタイルを作成して参照する方法について説明します。
author: thraka
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2956dbf93a1d34feca31d3ab10536f5089010189
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "81432558"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>WPF でコントロールのスタイルを作成する

Windows プレゼンテーションファンデーション (WPF) を使用すると、独自の再利用可能なスタイルで既存のコントロールの外観をカスタマイズできます。 スタイルは、アプリ、ウィンドウ、ページにグローバルに適用することも、コントロールに直接適用することもできます。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>スタイルの作成

プロパティ<xref:System.Windows.Style>値のセットを 1 つ以上の要素に適用する便利な方法と考えることができます。 <xref:System.Windows.FrameworkElement>スタイルは、 または<xref:System.Windows.FrameworkContentElement>など<xref:System.Windows.Window>から派生する任意の要素に対して<xref:System.Windows.Controls.Button>使用できます。

スタイルを宣言する最も一般的な方法は、XAML`Resources`ファイルのセクション内のリソースとして使用することです。 スタイルはリソースであるため、すべてのリソースに適用されるのと同じスコープルールに従います。 簡単に言うと、スタイルを宣言する場所は、スタイルを適用できる場所に影響します。 たとえば、アプリ定義 XAML ファイルのルート要素でスタイルを宣言すると、アプリ内の任意の場所でスタイルを使用できます。

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

アプリの XAML ファイルのいずれかでスタイルを宣言した場合、スタイルはその XAML ファイルでのみ使用できます。 リソースのスコープの規則の詳細については、「[XAML Resources](xaml-resources-define.md)」を参照してください。

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

スタイルは、スタイルが適用`<Setter>`される要素のプロパティを設定する子要素で構成されます。 上の例では、スタイルが属性を通じて型に適用`TextBlock`されるように設定されていること`TargetType`に注意してください。 スタイルは、 と<xref:System.Windows.Controls.Control.FontSize%2A>`15`に設定<xref:System.Windows.Controls.Control.FontWeight%2A>され`ExtraBold`、 にします。 スタイルが`<Setter>`変更されるプロパティごとに a を追加します。

## <a name="apply-a-style-implicitly"></a>スタイルを暗黙的に適用する

A<xref:System.Windows.Style>は、複数の要素に一連のプロパティ値を適用する便利な方法です。 たとえば、次<xref:System.Windows.Controls.TextBlock>の要素と、ウィンドウ内の既定の外観を考えます。

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![スタイリングサンプルスクリーンショット](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

既定の外観は、各<xref:System.Windows.Controls.Control.FontSize%2A><xref:System.Windows.Controls.Control.FontFamily%2A><xref:System.Windows.Controls.TextBlock>要素の プロパティや 、 などの プロパティを直接設定することで変更できます。 ただし、要素で一部<xref:System.Windows.Controls.TextBlock>のプロパティを共有する場合は、次に<xref:System.Windows.Style>示すように`Resources`、XAML ファイルのセクションに を作成できます。

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

スタイル<xref:System.Windows.Style.TargetType%2A>の を<xref:System.Windows.Controls.TextBlock>型に設定し、属性を`x:Key`省略すると、スタイルはスタイルのスコープ内のすべての<xref:System.Windows.Controls.TextBlock>要素 (通常は XAML ファイル自体) に適用されます。

要素は<xref:System.Windows.Controls.TextBlock>次のように表示されます。

![スタイリングサンプルスクリーンショット](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>スタイルを明示的に適用する

値を持つ`x:Key`属性をスタイルに追加すると、スタイルが の要素すべてに暗黙的に適用されなくなります<xref:System.Windows.Style.TargetType%2A>。 スタイルを明示的に参照する要素だけが、スタイルを適用します。

前のセクションのスタイルを次に示しますが、属性`x:Key`で宣言します。

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

スタイルを適用するには、次に<xref:System.Windows.FrameworkElement.Style%2A>示すように`x:Key`[、StaticResource マークアップ拡張機能](../../framework/wpf/advanced/staticresource-markup-extension.md)を使用して、要素のプロパティを値に設定します。

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

最初<xref:System.Windows.Controls.TextBlock>の要素にはスタイルが適用され、2 番目の TextBlock 要素は変更されません。 前のセクションの暗黙的なスタイルは、`x:Key`属性を宣言したスタイルに変更されました。

![スタイリングサンプルスクリーンショット](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "スタイルを作成する - 明示的なテキストブロック")

スタイルが適用されると、明示的または暗黙的にシールされ、変更できなくなります。 適用されているスタイルを変更する場合は、既存のスタイルを置き換える新しいスタイルを作成します。 詳細については、<xref:System.Windows.Style.IsSealed%2A> プロパティを参照してください。

カスタム ロジックに基づいて適用するスタイルを選択するオブジェクトを作成できます。 例については、クラスに用意されている例を<xref:System.Windows.Controls.StyleSelector>参照してください。

## <a name="apply-a-style-programmatically"></a>プログラムでスタイルを適用する

名前付きスタイルを要素にプログラムで割り当てるには、リソース コレクションからスタイルを取得し、要素<xref:System.Windows.FrameworkElement.Style%2A>のプロパティに割り当てます。 リソース コレクション内の項目の種類<xref:System.Object>は です。 したがって、`Style`取得したスタイルを プロパティに割り<xref:System.Windows.Style?displayProperty=fullName>当てる前に、 にキャストする必要があります。 たとえば、次のコードでは、名前付き`TextBlock``textblock1`のスタイルを定義されたスタイル`TitleText`に設定します。

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>スタイルを拡張する

2 つの<xref:System.Windows.Controls.TextBlock>要素で、<xref:System.Windows.Controls.Control.FontFamily%2A>と 中央の などのプロパティ値を共有する必要<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>がある場合があります。 しかし、テキスト **[マイ ピクチャ]** には追加のプロパティを設定することもできます。 これを行うには、最初のスタイルに基づく新しいスタイルを作成します( 以下を参照)。

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

この`TextBlock`スタイルは中央揃えになり、サイズ`Comic Sans MS``26`が のフォントを使用し、前景色が例に<xref:System.Windows.Media.LinearGradientBrush>示すように設定されています。 基本スタイルの値が<xref:System.Windows.Controls.Control.FontSize%2A>オーバーライドされることに注意してください。 で同じプロパティを<xref:System.Windows.Setter>指す複数のプロパティがある場合は<xref:System.Windows.Style>、最後に`Setter`宣言された が優先されます。

次に、要素の<xref:System.Windows.Controls.TextBlock>外観を示します。

![スタイル設定された TextBlocks](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

この`TitleText`スタイルは、型に対して作成されたスタイル<xref:System.Windows.Controls.TextBlock>を拡張`BasedOn="{StaticResource {x:Type TextBlock}}"`します。 スタイルの を使用`x:Key``x:Key`して、 を持つスタイルを拡張することもできます。 たとえば、という名前`Header1`のスタイルがあり、そのスタイルを拡張する場合は、 を使用`BasedOn="{StaticResource Header1}"`します。

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>プロパティと x:キー属性の関係

前に示したように、スタイル<xref:System.Windows.Style.TargetType%2A>を割`TextBlock`り当てずに`x:Key`プロパティを に設定すると、スタイル<xref:System.Windows.Controls.TextBlock>はすべての要素に適用されます。 ここでは、`x:Key` は暗黙的に `{x:Type TextBlock}` に設定されます。 つまり、値`x:Key`を明示的に`{x:Type TextBlock}`以外の値に設定した場合、すべての<xref:System.Windows.Style>`TextBlock`要素に自動的に適用されるわけではありません。 代わりに、(値を使用して) 要素`x:Key`にスタイルを明示的`TextBlock`に適用する必要があります。 スタイルがリソース セクションにあり、スタイルにプロパティを`TargetType`設定していない場合は、属性を設定する`x:Key`必要があります。

の既定値`x:Key`を提供するだけでなく、プロパティは`TargetType`、セッター プロパティを適用する型を指定します。 `TargetType`を指定しない場合は、 構文`Property="ClassName.Property"`を使用して<xref:System.Windows.Setter>、オブジェクトのプロパティをクラス名で修飾する必要があります。 たとえば、 を`Property="FontSize"`設定する代わりに、<xref:System.Windows.Setter.Property%2A>または`"TextBlock.FontSize"``"Control.FontSize"`に設定する必要があります。

また、多くの WPF コントロールは、他の WPF コントロールの組み合わせで構成されています。 型のすべてのコントロールに適用されるスタイルを作成する場合、予期しない結果になる可能性があります。 たとえば<xref:System.Windows.Controls.TextBlock>、 の型を対象とするスタイルを<xref:System.Windows.Window>作成すると、 などの他のコントロールの一部`TextBlock``TextBlock`である場合でも、そのスタイルはウィンドウ内のすべてのコントロールに<xref:System.Windows.Controls.ListBox>適用されます。

## <a name="see-also"></a>関連項目

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [XAML リソースの概要](xaml-resources-define.md)
- [XAML の概要 (WPF & .NET コア)](xaml.md)
