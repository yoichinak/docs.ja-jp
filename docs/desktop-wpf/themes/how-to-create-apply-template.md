---
title: WPF でテンプレートを作成する - .NET デスクトップ
description: Windows プレゼンテーション ファンデーションおよび .NET Core でコントロール テンプレートを作成して参照する方法について説明します。
author: thraka
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "81432540"
---
# <a name="create-a-template-for-a-control"></a>コントロールのテンプレートを作成する

Windows プレゼンテーションファンデーション (WPF) を使用すると、独自の再利用可能なテンプレートを使用して、既存のコントロールの視覚的な構造と動作をカスタマイズできます。 テンプレートは、アプリケーション、ウィンドウ、ページにグローバルに適用することも、コントロールに直接適用することもできます。 新しいコントロールを作成する必要があるほとんどのシナリオは、既存のコントロールの新しいテンプレートを作成する代わりに対応できます。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

この記事では、コントロールの新しい<xref:System.Windows.Controls.ControlTemplate>作成について説明します。 <xref:System.Windows.Controls.Button>

## <a name="when-to-create-a-controltemplate"></a>コントロール テンプレートを作成する場合

コントロールには、 、 <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>、および<xref:System.Windows.Controls.Control.FontFamily%2A>などの多くのプロパティがあります。 これらのプロパティは、コントロールの外観のさまざまな側面を制御しますが、これらのプロパティを設定することによって行うことができる変更は制限されます。 たとえば、プロパティを<xref:System.Windows.Controls.Control.Foreground%2A>青に設定し、<xref:System.Windows.Controls.Control.FontStyle%2A>プロパティに斜体を<xref:System.Windows.Controls.CheckBox>設定できます。 コントロールの他のプロパティを設定する以外に、コントロールの外観をカスタマイズする場合は、 を作成します<xref:System.Windows.Controls.ControlTemplate>。

ほとんどのユーザー インターフェイスでは、ボタンは同じ一般的な外観を持ちます: いくつかのテキストを持つ四角形。 丸みを帯びたボタンを作成する場合は、ボタンから継承する新しいコントロールを作成するか、ボタンの機能を再作成します。 さらに、新しいユーザー コントロールは、円形のビジュアルを提供します。

既存のコントロールの視覚的なレイアウトをカスタマイズすることで、新しいコントロールを作成しないようにできます。 丸みを帯びたボタンを使用して<xref:System.Windows.Controls.ControlTemplate>、目的のビジュアルレイアウトを持つ を作成します。

一方、新しい機能、異なるプロパティ、および新しい設定を持つコントロールが必要な場合は、新<xref:System.Windows.Controls.UserControl>しい を作成します。

## <a name="prerequisites"></a>前提条件

新しい WPF アプリケーションを作成し *、MainWindow.xaml* (または選択した別のウィンドウ) で**\<、Window>** 要素に次のプロパティを設定します。

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

**\<ウィンドウ>** 要素の内容を次の XAML に設定します。

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

最終的には *、MainWindow.xaml*ファイルは次のようになります。

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

アプリケーションを実行すると、次のようになります。

![2 つのスタイルなしボタンを持つ WPF ウィンドウ](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>ControlTemplate の作成

を<xref:System.Windows.Controls.ControlTemplate>宣言する最も一般的な方法は、XAML`Resources`ファイルのセクション内のリソースとしてです。 テンプレートはリソースであるため、すべてのリソースに適用されるのと同じスコープルールに従います。 簡単に言うと、テンプレートを宣言する場所は、テンプレートを適用できる場所に影響します。 たとえば、アプリケーション定義 XAML ファイルのルート要素でテンプレートを宣言すると、アプリケーション内の任意の場所でテンプレートを使用できます。 テンプレートをウィンドウで定義した場合、そのウィンドウ内のコントロールだけがテンプレートを使用できます。

まず`Window.Resources`*、MainWindow.xaml*ファイルに要素を追加します。

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

次のプロパティを設定して、新しい**\<ControlTemplate>** を作成します。

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

このコントロール テンプレートは、次の簡単な方法で作成できます。

- コントロールのルート要素、<xref:System.Windows.Controls.Grid>
- ボタン<xref:System.Windows.Shapes.Ellipse>の丸みを帯びた外観を描く
- ユーザー<xref:System.Windows.Controls.ContentPresenter>指定のボタンの内容を表示する

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

新<xref:System.Windows.Controls.ControlTemplate>しい を作成する場合でも、パブリック プロパティを使用してコントロールの外観を変更できます。 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)マークアップ拡張機能は、内にある要素のプロパティ<xref:System.Windows.Controls.ControlTemplate>を、コントロールによって定義されているパブリック プロパティにバインドします。 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)を使用すると、コントロールのプロパティがテンプレートのパラメーターとして機能するように設定できます。 つまり、コントロールのプロパティを設定すると、その値は [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) が機能している要素に渡されます。

### <a name="ellipse"></a>楕円形

Ellipse>**:::no-loc text="Fill":::** 要素**:::no-loc text="Stroke":::** の**\<** プロパティと プロパティは、コントロール<xref:System.Windows.Controls.Control.Foreground>のプロパティと<xref:System.Windows.Controls.Control.Background>プロパティにバインドされていることに注意してください。

### <a name="contentpresenter"></a>ContentPresenter

コンテンツプレゼンター>要素もテンプレートに追加されます。 [ \<](xref:System.Windows.Controls.ContentPresenter) このテンプレートはボタン用に設計されているため、ボタンが から<xref:System.Windows.Controls.ContentControl>継承することを考慮する。 ボタンは要素の内容を表示します。 プレーン テキストや別のコントロールなど、ボタン内の設定を行うことができます。 次の両方が有効なボタンです。

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

上記の両方の例では、テキストとチェックボックスが[Button.Content](xref:System.Windows.Controls.ContentControl.Content)プロパティとして設定されています。 コンテンツとして設定されているものは**\<、ContentPresenter>** を通じて表示できます。

などの<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.ContentControl>型に a が適用されている場合`Button`<xref:System.Windows.Controls.ContentPresenter>は、要素ツリーで a が検索されます。 が`ContentPresenter`見つかった場合、テンプレートはコントロールの<xref:System.Windows.Controls.ContentControl.Content>プロパティを . `ContentPresenter`

## <a name="use-the-template"></a>テンプレートを使用する

この記事の冒頭で宣言したボタンを見つけます。

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

2 番目のボタンの<xref:System.Windows.Controls.Control.Template>プロパティをリソース`roundbutton`に設定します。

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

プロジェクトを実行して結果を確認すると、ボタンの背景が丸くなっていることがわかります。

![テンプレートの楕円形ボタンが 1 つある WPF ウィンドウ](media/create-apply-template/styled-button.png)

ボタンが円ではなく、ゆがんでいることに気づいたかもしれません。 **\<楕円>** 要素の動作方法により、常に使用可能なスペースを埋めるために拡張されます。 ボタン**:::no-loc text="width":::** と**:::no-loc text="height":::** プロパティを同じ値に変更して、円を均一にします。

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![1 つのテンプレートの循環ボタンを持つ WPF ウィンドウ](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>トリガーの追加

テンプレートが適用されたボタンの外観は異なりますが、他のボタンと同じように動作します。 ボタンを押すと、イベントが<xref:System.Windows.Controls.Primitives.ButtonBase.Click>発生します。 ただし、ボタンの上にマウスを移動しても、ボタンのビジュアルは変更されないことに気付いたかもしれません。 これらの視覚的な相互作用はすべてテンプレートによって定義されます。

WPFWPF が提供する動的イベントおよびプロパティ システムでは、値の特定のプロパティを監視し、必要に応じてテンプレートのスタイルを変更できます。 この例では、ボタンの<xref:System.Windows.UIElement.IsMouseOver>プロパティを確認します。 マウスをコントロールの上に置き、**\<楕円>** を新しい色でスタイル設定します。 この種類のトリガは、*プロパティトリガー*と呼ばれます。

これを行うには、参照できる**\<楕円>** に名前を追加する必要があります。 **背景**要素の名前を付けます。

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

次に、新<xref:System.Windows.Trigger>しいを追加[ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers)します。 トリガは、値`IsMouseOver``true`のイベントを監視します。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

次に、新しい色に**\<楕円>** の**\<****Fill****\<** Fill プロパティを変更するトリガー>にセッター>を追加します。

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

プロジェクトを実行します。 マウスをボタンの上に移動すると、**\<楕円>** の色が変わります。

![マウスを WPF ボタンの上に移動して塗りつぶしの色を変更する](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>ビジュアルステートを使用する

表示状態は、コントロールによって定義およびトリガされます。 たとえば、マウスをコントロールの上に移動すると、`CommonStates.MouseOver`状態がトリガーされます。 コントロールの現在の状態に基づいて、プロパティの変更をアニメーション化できます。 前のセクションでは**\<、PropertyTrigger>** を使用して、`IsMouseOver`ボタンの前景を`true`プロパティ`AliceBlue`が . 代わりに、この色の変化をアニメーション化する表示状態を作成し、スムーズな遷移を提供します。 *VisualStates*の詳細については、「 [WPF のスタイルとテンプレート](../fundamentals/styles-templates-overview.md#visual-states)」を参照してください。

**\<プロパティ トリガー>** をアニメーション表示状態に変換するには、まず、**\<テンプレートから ControlTemplate.Triggers>** 要素を削除します。

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

次に、コントロール テンプレートの**\<グリッド>** ルートに**\<、>要素を** ** \<>追加**`CommonStates`します。 2 つの状態`Normal`を`MouseOver`定義し、 と を使用します。

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

VisualState>で定義されたアニメーションは、その状態がトリガーされたときに適用されます。 ** \<** 各状態のアニメーションを作成します。 アニメーションは、**\<ストーリーボード>** 要素の内部に配置されます。 ストーリーボードの詳細については、「ストーリーボードの[概要](../../framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。

- Normal

  この状態は、楕円の塗りつぶしをアニメーション化し、コントロールの`Background`色に戻します。

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  この状態は、楕円`Background`の色を新しい色に`Yellow`アニメーション化します。

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

コントロール テンプレート>は、次のようになります。 ** \<**

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

プロジェクトを実行します。 マウスをボタンの上に移動すると、**\<楕円**の色>アニメーションに変わります。

![マウスを WPF ボタンの上に移動して塗りつぶしの色を変更する](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>次のステップ

- [WPF でコントロールのスタイルを作成する](../fundamentals/styles-templates-create-apply-style.md)
- [WPF のスタイルとテンプレート](../fundamentals/styles-templates-overview.md)
- [XAML リソースの概要](../fundamentals/xaml-resources-define.md)
