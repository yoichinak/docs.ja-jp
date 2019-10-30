---
title: ControlTemplate の作成による既存のコントロールの外観のカスタマイズ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
ms.openlocfilehash: 0c79ba3dd42f2e65eb241409946e921577ced5f1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920048"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>ControlTemplate の作成による既存のコントロールの外観のカスタマイズ
<a name="introduction"></a>コントロールの視覚的な構造と視覚的な動作を指定 <xref:System.Windows.Controls.ControlTemplate>。 コントロールの外観をカスタマイズするには、新しい <xref:System.Windows.Controls.ControlTemplate>を指定します。 <xref:System.Windows.Controls.ControlTemplate>を作成すると、その機能を変更せずに既存のコントロールの外観を置き換えることができます。 たとえば、既定の四角形の形ではなく、アプリケーションのボタンを丸めることができますが、ボタンをクリックすると <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントが発生します。

 このトピックでは、<xref:System.Windows.Controls.ControlTemplate>のさまざまな部分について説明し、<xref:System.Windows.Controls.Button>の単純な <xref:System.Windows.Controls.ControlTemplate> を作成する方法と、コントロールのコントロールコントラクトを理解してその外観をカスタマイズできるようにする方法について説明します。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]に <xref:System.Windows.Controls.ControlTemplate> を作成するため、コードを記述することなく、コントロールの外観を変更できます。 Blend for Visual Studio などのデザイナーを使用して、カスタムコントロールテンプレートを作成することもできます。 このトピックでは、<xref:System.Windows.Controls.Button> の外観をカスタマイズする [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例を示し、トピックの最後にある完全な例を示します。 Blend for Visual Studio の使用方法の詳細については、「[テンプレートをサポートするコントロールのスタイル](https://go.microsoft.com/fwlink/?LinkId=161153)を設定する」を参照してください。

 次の図は、このトピックで作成した <xref:System.Windows.Controls.ControlTemplate> を使用する <xref:System.Windows.Controls.Button> を示しています。

 ![カスタム コントロール テンプレートを使用したボタン](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
カスタム コントロール テンプレートを使用しているボタン

 ![赤い境界線付きのボタン](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
カスタム コントロール テンプレートを使用したボタンにマウス ポインターを置いた状態

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要条件
 このトピックは、「[コントロール](index.md)」で説明したコントロールとスタイルの作成方法および使用方法を理解していることを前提としています。 このトピックで説明する概念は、<xref:System.Windows.Controls.Control> クラスを継承する要素に適用されます。ただし、<xref:System.Windows.Controls.UserControl>は除きます。 <xref:System.Windows.Controls.UserControl>に <xref:System.Windows.Controls.ControlTemplate> を適用することはできません。

<a name="when_you_should_create_a_controltemplate"></a>
## <a name="when-you-should-create-a-controltemplate"></a>ControlTemplate の作成が必要な場合
 コントロールには <xref:System.Windows.Controls.Border.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A>、<xref:System.Windows.Controls.Control.FontFamily%2A>などの多くのプロパティがあります。このプロパティを設定すると、コントロールの外観のさまざまな側面を指定できますが、これらのプロパティを設定することによって行うことができる変更は制限されます。 たとえば、<xref:System.Windows.Controls.CheckBox>では、<xref:System.Windows.Controls.Control.Foreground%2A> プロパティを blue に、<xref:System.Windows.Controls.Control.FontStyle%2A> を斜体に設定できます。

 コントロール用の新しい <xref:System.Windows.Controls.ControlTemplate> を作成する機能がないと、すべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ベースのアプリケーションのすべてのコントロールの全般的な外観は同じになります。これにより、カスタムの外観でアプリケーションを作成する機能が制限されます。 既定では、すべての <xref:System.Windows.Controls.CheckBox> に同様の特性があります。 たとえば、<xref:System.Windows.Controls.CheckBox> の内容は常に選択インジケーターの右側にあり、チェックマークは、<xref:System.Windows.Controls.CheckBox> が選択されていることを示すために常に使用されます。

 コントロールの他のプロパティが行う設定よりも、コントロールの外観をカスタマイズする必要がある場合は、<xref:System.Windows.Controls.ControlTemplate> を作成します。 <xref:System.Windows.Controls.CheckBox>の例では、チェックボックスの内容を選択インジケーターの上に配置し、<xref:System.Windows.Controls.CheckBox> が選択されていることを X で示す必要があるとします。 これらの変更は、<xref:System.Windows.Controls.CheckBox>の <xref:System.Windows.Controls.ControlTemplate> で指定します。

 次の図は、既定の <xref:System.Windows.Controls.ControlTemplate>を使用する <xref:System.Windows.Controls.CheckBox> を示しています。

 ![既定のコントロール テンプレートを使用するチェックボックス。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
既定のコントロール テンプレートを使用する CheckBox

 次の図は、カスタム <xref:System.Windows.Controls.ControlTemplate> を使用して <xref:System.Windows.Controls.CheckBox> の内容を選択インジケーターの上に配置し、<xref:System.Windows.Controls.CheckBox> を選択したときに X を表示する <xref:System.Windows.Controls.CheckBox> を示しています。

 ![カスタム コントロール テンプレートを使用するチェックボックス。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
カスタム コントロール テンプレートを使用する CheckBox

 このサンプルの <xref:System.Windows.Controls.CheckBox> の <xref:System.Windows.Controls.ControlTemplate> は比較的複雑であるため、このトピックでは <xref:System.Windows.Controls.Button>の <xref:System.Windows.Controls.ControlTemplate> を作成する簡単な例を使用します。

<a name="changing_the_visual_structure_of_a_control"></a>
## <a name="changing-the-visual-structure-of-a-control"></a>コントロールの視覚的な構造の変更
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、多くの場合、コントロールは複合 <xref:System.Windows.FrameworkElement> オブジェクトです。 <xref:System.Windows.Controls.ControlTemplate>を作成するときに、<xref:System.Windows.FrameworkElement> オブジェクトを組み合わせて1つのコントロールを作成します。 <xref:System.Windows.Controls.ControlTemplate> には、ルート要素として <xref:System.Windows.FrameworkElement> が1つだけ必要です。 ルート要素には、通常、他の <xref:System.Windows.FrameworkElement> オブジェクトが含まれます。 複数のオブジェクトを組み合わせて、コントロールの視覚的な構造を構成します。

 次の例では、<xref:System.Windows.Controls.Button>のカスタム <xref:System.Windows.Controls.ControlTemplate> を作成します。 <xref:System.Windows.Controls.ControlTemplate> によって、<xref:System.Windows.Controls.Button>のビジュアル構造が作成されます。 この例では、ボタンの上にマウス ポインターを移動しても、ボタンをクリックしても、その外観は変化しません。 状態に応じて外観が変化するボタンについては、このトピックで後述します。

 この例では、以下のパーツで視覚的な構造を構成しています。

- テンプレートのルート <xref:System.Windows.FrameworkElement>として機能する `RootElement` という名前の <xref:System.Windows.Controls.Border>。

- `RootElement`の子である <xref:System.Windows.Controls.Grid>。

- ボタンの内容を表示する <xref:System.Windows.Controls.ContentPresenter>。 <xref:System.Windows.Controls.ContentPresenter> を使用すると、任意の型のオブジェクトを表示できます。

 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]

### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>TemplateBinding を使用してコントロールのプロパティの機能を維持する方法
 新しい <xref:System.Windows.Controls.ControlTemplate>を作成する場合でも、パブリックプロパティを使用してコントロールの外観を変更することをお勧めします。 [TemplateBinding](../advanced/templatebinding-markup-extension.md)マークアップ拡張機能は、<xref:System.Windows.Controls.ControlTemplate> 内の要素のプロパティを、コントロールで定義されているパブリックプロパティにバインドします。 [TemplateBinding](../advanced/templatebinding-markup-extension.md) を使用すると、コントロールのプロパティをテンプレートのパラメーターとして機能させることができます。 つまり、コントロールのプロパティを設定すると、その値は [TemplateBinding](../advanced/templatebinding-markup-extension.md) が機能している要素に渡されます。

 次の例では、前の例の一部を繰り返します。この例では、 [TemplateBinding](../advanced/templatebinding-markup-extension.md)マークアップ拡張機能を使用して、<xref:System.Windows.Controls.ControlTemplate> 内の要素のプロパティを、ボタンで定義されているパブリックプロパティにバインドしています。

 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]

 この例では、<xref:System.Windows.Controls.Grid> の <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> プロパティテンプレートが <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>にバインドされています。 <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> がテンプレートにバインドされているため、同じ <xref:System.Windows.Controls.ControlTemplate> を使用する複数のボタンを作成し、各ボタンの <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> を異なる値に設定することができます。 <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> が <xref:System.Windows.Controls.ControlTemplate>内の要素のプロパティにテンプレートバインドされていない場合、ボタンの <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> を設定しても、ボタンの外観には影響しません。

 2 つのプロパティの名前は同じである必要はありません。 前の例では、<xref:System.Windows.Controls.Button> の [<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>] プロパティは <xref:System.Windows.Controls.ContentPresenter>の <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> プロパティにバインドされています。 これにより、ボタンのコンテンツを水平方向に配置できます。 <xref:System.Windows.Controls.ContentPresenter> には `HorizontalContentAlignment`という名前のプロパティはありませんが、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> を <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>にバインドすることはできます。 プロパティをテンプレート バインディングするときは、ターゲットとソースのプロパティが同じ型であることを確認してください。

 <xref:System.Windows.Controls.Control> クラスは、コントロールテンプレートが設定されたときにコントロールに影響を与えるために使用する必要があるいくつかのプロパティを定義します。 <xref:System.Windows.Controls.ControlTemplate> でのプロパティの使用方法は、プロパティによって異なります。 <xref:System.Windows.Controls.ControlTemplate> では、次のいずれかの方法でプロパティを使用する必要があります。

- <xref:System.Windows.Controls.ControlTemplate> テンプレート内の要素は、プロパティにバインドされます。

- <xref:System.Windows.Controls.ControlTemplate> 内の要素は、親 <xref:System.Windows.FrameworkElement>からプロパティを継承します。

 次の表に、<xref:System.Windows.Controls.Control> クラスからコントロールによって継承されるビジュアルプロパティの一覧を示します。 また、コントロールの既定のコントロール テンプレートで継承されたプロパティ値を使用するかどうか、テンプレート バインディングする必要があるかどうかも示します。

|property|使用するメソッド|
|--------------|------------------|
|<xref:System.Windows.Controls.Control.Background%2A>|テンプレート バインディング|
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|テンプレート バインディング|
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|テンプレート バインディング|
|<xref:System.Windows.Controls.Control.FontFamily%2A>|プロパティの継承またはテンプレート バインディング|
|<xref:System.Windows.Controls.Control.FontSize%2A>|プロパティの継承またはテンプレート バインディング|
|<xref:System.Windows.Controls.Control.FontStretch%2A>|プロパティの継承またはテンプレート バインディング|
|<xref:System.Windows.Controls.Control.FontWeight%2A>|プロパティの継承またはテンプレート バインディング|
|<xref:System.Windows.Controls.Control.Foreground%2A>|プロパティの継承またはテンプレート バインディング|
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|テンプレート バインディング|
|<xref:System.Windows.Controls.Control.Padding%2A>|テンプレート バインディング|
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|テンプレート バインディング|

 このテーブルには、<xref:System.Windows.Controls.Control> クラスから継承されたビジュアルプロパティのみが表示されます。 コントロールは、表に示されているプロパティとは別に、<xref:System.Windows.FrameworkElement.DataContext%2A>、<xref:System.Windows.FrameworkElement.Language%2A>、および <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> の各プロパティを親フレームワーク要素から継承することもあります。

 また、<xref:System.Windows.Controls.ContentPresenter> が <xref:System.Windows.Controls.ContentControl>の <xref:System.Windows.Controls.ControlTemplate> にある場合、<xref:System.Windows.Controls.ContentPresenter> は自動的に <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> および <xref:System.Windows.Controls.ContentControl.Content%2A> のプロパティにバインドされます。 同様に、<xref:System.Windows.Controls.ItemsControl> の <xref:System.Windows.Controls.ControlTemplate> にある <xref:System.Windows.Controls.ItemsPresenter> は、<xref:System.Windows.Controls.ItemsControl.Items%2A> および <xref:System.Windows.Controls.ItemsPresenter> のプロパティに自動的にバインドされます。

 次の例では、前の例で定義した <xref:System.Windows.Controls.ControlTemplate> を使用する2つのボタンを作成します。 この例では、各ボタンの <xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A>、および <xref:System.Windows.Controls.Control.FontSize%2A> の各プロパティを設定します。 <xref:System.Windows.Controls.Control.Background%2A> プロパティの設定は、<xref:System.Windows.Controls.ControlTemplate>でテンプレートにバインドされているため、効果があります。 <xref:System.Windows.Controls.Control.Foreground%2A> プロパティと <xref:System.Windows.Controls.Control.FontSize%2A> プロパティがテンプレートにバインドされていない場合でも、値が継承されるため、設定が有効になります。

 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]

 前の例では、次の図のような出力を生成します。

 ![2 つのボタン (青色のボタンと紫色のボタン)](./media/ndp-buttontwo.png "NDP_ButtonTwo")
背景色が異なる 2 つのボタン

<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>状態に応じたコントロールの外観の変化
 既定の外観のボタンと前の例のボタンの違いは、既定のボタンが別の状態になったときにわずかに変化することです。 たとえば、ボタンをクリックしたときやマウス ポインターをボタンの上に置いたときに、既定のボタンは外観が変化します。 <xref:System.Windows.Controls.ControlTemplate> はコントロールの機能を変更しませんが、コントロールの視覚的な動作を変更します。 視覚的な動作とは、コントロールが特定の状態にあるときの外観を指しています。 コントロールの機能と視覚的な動作の違いを理解するために、ボタンの例について考えてみます。 ボタンの機能は、クリックされると <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを発生させることですが、ボタンの視覚的な動作は、ポイントまたは押されたときの外観を変更することです。

 <xref:System.Windows.VisualState> オブジェクトを使用して、コントロールが特定の状態にあるときのコントロールの外観を指定します。 <xref:System.Windows.VisualState> には、<xref:System.Windows.Controls.ControlTemplate>内の要素の外観を変更する <xref:System.Windows.Media.Animation.Storyboard> が含まれています。 コントロールのロジックが <xref:System.Windows.VisualStateManager>を使用して状態を変更するため、このようなコードを記述する必要はありません。 コントロールが <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> プロパティによって指定された状態になると、<xref:System.Windows.Media.Animation.Storyboard> が開始されます。 コントロールが状態を終了すると、<xref:System.Windows.Media.Animation.Storyboard> が停止します。

 次の例は、マウスポインターが上にあるときの <xref:System.Windows.Controls.Button> の外観を変更する <xref:System.Windows.VisualState> を示しています。 <xref:System.Windows.Media.Animation.Storyboard> は、`BorderBrush`の色を変更して、ボタンの境界線の色を変更します。 このトピックの冒頭にある <xref:System.Windows.Controls.ControlTemplate> の例を参照している場合は、`BorderBrush` が <xref:System.Windows.Controls.Border>の <xref:System.Windows.Controls.Border.Background%2A> に割り当てられている <xref:System.Windows.Media.SolidColorBrush> の名前であることを思い出してください。

 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]

 このコントロールは、コントロール コントラクトの一部として状態を定義する役割を果たします。詳細については、このトピックの「[コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法](#customizing_other_controls_by_understanding_the_control_contract)」で後述します。 次の表に、<xref:System.Windows.Controls.Button>に対して指定されている状態を示します。

|VisualState 名|VisualStateGroup 名|説明|
|----------------------|---------------------------|-----------------|
|標準|CommonStates|既定の状態です。|
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されます。|
|押されている|CommonStates|コントロールが押されています。|
|Disabled|CommonStates|コントロールが無効になっています。|
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|

 <xref:System.Windows.Controls.Button> は2つの状態グループを定義します。 `CommonStates` グループには、`Normal`、`MouseOver`、`Pressed`、および `Disabled` の各状態が含まれます。 `FocusStates` グループには、`Focused` 状態と `Unfocused` 状態が含まれます。 同じ状態グループ内の状態を同時に複数指定することはできません。 コントロールが取り得る状態は、常に 1 グループにつき 1 つです。 たとえば、<xref:System.Windows.Controls.Button> は、マウスポインターが上にない場合でもフォーカスを持つことができるので、`Focused` 状態の <xref:System.Windows.Controls.Button> は `MouseOver`、`Pressed`、または `Normal` 状態になります。

 <xref:System.Windows.VisualStateGroup> オブジェクトに <xref:System.Windows.VisualState> オブジェクトを追加します。 <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> 添付プロパティに <xref:System.Windows.VisualStateGroup> オブジェクトを追加します。 次の例では、`Normal`、`MouseOver`、および `Pressed` の状態の <xref:System.Windows.VisualState> オブジェクトを定義しています。これらはすべて `CommonStates` グループに含まれています。 各 <xref:System.Windows.VisualState> の <xref:System.Windows.VisualState.Name%2A> は、前の表の名前と一致します。 `Disabled` の状態および `FocusStates` グループの状態は、例を簡潔にするために省略していますが、このトピックの最後で紹介している完全なコード例には含まれています。

> [!NOTE]
> <xref:System.Windows.Controls.ControlTemplate>のルート <xref:System.Windows.FrameworkElement> には、<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> 添付プロパティを必ず設定してください。

 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]

 前の例では、次の図のような出力を生成します。

 ![カスタム コントロール テンプレートを使用したボタン](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
通常状態のカスタム コントロール テンプレートを使用しているボタン

 ![赤い境界線付きのボタン](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
マウス オーバー状態のカスタム コントロール テンプレートを使用しているボタン

 ![ボタンが押されて境界線が透明になっている状態。](./media/ndp-buttonpressed.png "NDP_ButtonPressed")
押された状態のカスタム コントロール テンプレートを使用しているボタン

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールの視覚的な状態については、「[コントロールのスタイルとテンプレート](control-styles-and-templates.md)」を参照してください。

<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>状態間を遷移するときのコントロールの動作の指定
 前の例では、ボタンをクリックしたときにもボタンの外観が変化しましたが、ボタンを 1 秒間押したままにしない限り、効果を確認できません。 既定では、アニメーションが開始されるまでに 1 秒かかります。 多くの場合、ユーザーはボタンをクリックしてすぐに離すことができるので、<xref:System.Windows.Controls.ControlTemplate> を既定の状態のままにしておくと、視覚的なフィードバックが有効になりません。

 <xref:System.Windows.Controls.ControlTemplate>に <xref:System.Windows.VisualTransition> オブジェクトを追加することによって、コントロールをある状態から別の状態にスムーズに遷移させるために、アニメーションを実行する時間を指定できます。 <xref:System.Windows.VisualTransition>を作成する場合は、次のいずれかまたは複数を指定します。

- 状態間の遷移を開始するまでに要する時間。

- 遷移時に発生するコントロールの外観への追加の変更。

- <xref:System.Windows.VisualTransition> が適用される状態。

### <a name="specifying-the-duration-of-a-transition"></a>遷移の継続時間の指定
 移行にかかる時間を指定するには、<xref:System.Windows.VisualTransition.GeneratedDuration%2A> プロパティを設定します。 前の例には、ボタンが押されたときにボタンの境界線が透明になることを指定する <xref:System.Windows.VisualState> がありますが、ボタンがすぐに押されて解放されると、アニメーションの処理に時間がかかりすぎます。 <xref:System.Windows.VisualTransition> を使用すると、コントロールが押された状態に遷移するまでの時間を指定できます。 次の例では、コントロールが押された状態になるのに要する時間を 1/100 秒に指定しています。

 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]

### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>遷移時にコントロールの外観の変更を指定する方法
 <xref:System.Windows.VisualTransition> には、コントロールが状態間を遷移するときに開始される <xref:System.Windows.Media.Animation.Storyboard> が含まれています。 たとえば、コントロールが `MouseOver` 状態から `Normal` 状態に遷移する場合に、特定のアニメーションが実行されるように指定できます。 次の例では、ユーザーがマウスポインターをボタンの上に移動したときに、ボタンの境界線が青に変わり、黄色の場合は1.5 秒で黒に変更されることを指定する <xref:System.Windows.VisualTransition> を作成します。

 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]

### <a name="specifying-when-a-visualtransition-is-applied"></a>VisualTransition を適用するタイミングの指定
 <xref:System.Windows.VisualTransition> は、特定の状態にのみ適用されるように制限することも、コントロールが状態間を遷移するたびに適用することもできます。 前の例では、コントロールが `MouseOver` 状態から `Normal` 状態に移動したときに、<xref:System.Windows.VisualTransition> が適用されます。この前の例では、コントロールが `Pressed` 状態になると <xref:System.Windows.VisualTransition> が適用されます。 <xref:System.Windows.VisualTransition> が適用されるタイミングを制限するには、<xref:System.Windows.VisualTransition.To%2A> プロパティと <xref:System.Windows.VisualTransition.From%2A> プロパティを設定します。 次の表では、制限が最も厳しいレベルから最も緩いレベルまでを一覧にして示しています。

|制限の種類|からの値|の値|
|-------------------------|-------------------|-----------------|
|指定した状態から別の指定した状態まで|<xref:System.Windows.VisualState> の名前|<xref:System.Windows.VisualState> の名前|
|任意の状態から指定された状態まで|未設定|<xref:System.Windows.VisualState> の名前|
|指定した状態から任意の状態まで|<xref:System.Windows.VisualState> の名前|未設定|
|任意の状態から他の状態へ|未設定|未設定|

 <xref:System.Windows.VisualStateGroup> には、同じ状態を参照する複数の <xref:System.Windows.VisualTransition> オブジェクトを含めることができますが、これらは、前の表で指定した順序で使用されます。 次の例では、2つの <xref:System.Windows.VisualTransition> オブジェクトがあります。 コントロールが `Pressed` 状態から `MouseOver` 状態に遷移すると、<xref:System.Windows.VisualTransition.From%2A> と <xref:System.Windows.VisualTransition.To%2A> セットの両方を持つ <xref:System.Windows.VisualTransition> が使用されます。 コントロールが `Pressed` ではない状態から `MouseOver` 状態に遷移するときには、別の状態を使用します。

 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]

 <xref:System.Windows.VisualStateGroup> には、<xref:System.Windows.VisualStateGroup>内の <xref:System.Windows.VisualState> オブジェクトに適用される <xref:System.Windows.VisualTransition> オブジェクトを含む <xref:System.Windows.VisualStateGroup.Transitions%2A> プロパティがあります。 <xref:System.Windows.Controls.ControlTemplate> 作成者は、任意の <xref:System.Windows.VisualTransition> を自由に含めることができます。 ただし、<xref:System.Windows.VisualTransition.To%2A> プロパティと <xref:System.Windows.VisualTransition.From%2A> プロパティが <xref:System.Windows.VisualStateGroup>にない状態名に設定されている場合、<xref:System.Windows.VisualTransition> は無視されます。

 次の例は、`CommonStates`の <xref:System.Windows.VisualStateGroup> を示しています。 この例では、ボタンの次の遷移ごとに <xref:System.Windows.VisualTransition> を定義します。

- `Pressed` 状態への遷移。

- `MouseOver` 状態への遷移。

- `Pressed` 状態から `MouseOver` 状態への遷移。

- `MouseOver` 状態から `Normal` 状態への遷移。

 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]

<a name="customizing_other_controls_by_understanding_the_control_contract"></a>
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法
 (<xref:System.Windows.FrameworkElement> オブジェクトを使用して) ビジュアル構造を指定するために <xref:System.Windows.Controls.ControlTemplate> を使用するコントロールと、(<xref:System.Windows.VisualState> オブジェクトを使用した) 視覚的な動作では、パーツコントロールモデルを使用します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 に含まれるコントロールの多くは、このモデルを採用しています。 <xref:System.Windows.Controls.ControlTemplate> 作成者が認識する必要があるパーツは、コントロールコントラクトを通じて伝達されます。 コントロール コントラクトのパーツについて理解すると、パーツ コントロール モデルを採用するあらゆるコントロールの外観をカスタマイズできます。

 コントロール コントラクトには、次の 3 つの要素があります。

- コントロールのロジックが使用する視覚的要素。

- コントロールの状態および各状態が所属するグループ。

- コントロールに対して視覚的に作用するパブリック プロパティ。

### <a name="visual-elements-in-the-control-contract"></a>コントロール コントラクトの視覚的要素
 場合によっては、コントロールのロジックが <xref:System.Windows.Controls.ControlTemplate>内の <xref:System.Windows.FrameworkElement> と対話します。 たとえば、コントロールがその要素のイベントを処理する場合などです。 コントロールが <xref:System.Windows.Controls.ControlTemplate>内の特定の <xref:System.Windows.FrameworkElement> を検索する場合は、その情報を <xref:System.Windows.Controls.ControlTemplate> 作成者に伝える必要があります。 コントロールは、<xref:System.Windows.TemplatePartAttribute> を使用して、想定される要素の型と、要素の名前を伝達します。 <xref:System.Windows.Controls.Button> には、コントロールコントラクトに <xref:System.Windows.FrameworkElement> パーツはありませんが、<xref:System.Windows.Controls.ComboBox>などの他のコントロールは実行されます。

 次の例は、<xref:System.Windows.Controls.ComboBox> クラスで指定されている <xref:System.Windows.TemplatePartAttribute> オブジェクトを示しています。 <xref:System.Windows.Controls.ComboBox> のロジックでは、`PART_EditableTextBox` という名前の <xref:System.Windows.Controls.TextBox> と `PART_Popup` 内の <xref:System.Windows.Controls.Primitives.Popup> を検索する必要があります。

 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]

 次の例は、<xref:System.Windows.Controls.ComboBox> クラスの <xref:System.Windows.TemplatePartAttribute> オブジェクトによって指定された要素を含む <xref:System.Windows.Controls.ComboBox> の簡略化された <xref:System.Windows.Controls.ControlTemplate> を示しています。

 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]

### <a name="states-in-the-control-contract"></a>コントロール コントラクトの状態
 コントロールの状態もコントロール コントラクトの一部です。 <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.ControlTemplate> を作成する例は、状態に応じて <xref:System.Windows.Controls.Button> の外観を指定する方法を示しています。 このトピックの「[状態に応じてコントロールの外観を変更](#changing_the_appearance_of_a_control_depending_on_its_state)する」で説明されているように、指定した各状態の <xref:System.Windows.VisualState> を作成し、<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> を共有するすべての <xref:System.Windows.VisualState> オブジェクトを <xref:System.Windows.VisualStateGroup>に配置します。 サードパーティのコントロールでは、<xref:System.Windows.TemplateVisualStateAttribute>を使用して状態を指定する必要があります。これにより、Visual Studio や Blend for Visual Studio の[XAML デザイナー](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)などのデザイナーツールを使用して、コントロールテンプレートを作成するためのコントロールの状態を公開できます。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールのコントロール コントラクトについては、「[コントロールのスタイルとテンプレート](control-styles-and-templates.md)」を参照してください。

### <a name="properties-in-the-control-contract"></a>コントロール コントラクトのプロパティ
 コントロールに視覚的な影響を与えるパブリック プロパティも、コントロール コントラクトに含まれています。 これらのプロパティを設定して、新しい <xref:System.Windows.Controls.ControlTemplate>を作成せずにコントロールの外観を変更することができます。 また、 [TemplateBinding](../advanced/templatebinding-markup-extension.md)マークアップ拡張機能を使用して、<xref:System.Windows.Controls.ControlTemplate> 内の要素のプロパティを、<xref:System.Windows.Controls.Button>で定義されているパブリックプロパティにバインドすることもできます。

 次の例では、ボタンのコントロール コントラクトを示します。

 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]

 <xref:System.Windows.Controls.ControlTemplate>を作成する場合、多くの場合、既存の <xref:System.Windows.Controls.ControlTemplate> を使用して変更を加えるのが最も簡単です。 既存の <xref:System.Windows.Controls.ControlTemplate>を変更するには、次のいずれかの操作を行います。

- コントロールテンプレートを作成するためのグラフィカルユーザーインターフェイスを提供する、Blend for Visual Studio などのデザイナーを使用します。 詳細については、「[テンプレートをサポートするコントロールのスタイル処理](https://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。

- 既定の <xref:System.Windows.Controls.ControlTemplate> を取得して編集します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属する既定のコントロール テンプレートについては、「[デフォルトの WPF テーマ](https://go.microsoft.com/fwlink/?LinkID=158252)」を参照してください。

<a name="complete_example"></a>
## <a name="complete-example"></a>コード例全体
 次の例は、このトピックで説明する完全な <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate> を示しています。

 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]

## <a name="see-also"></a>関連項目

- [スタイルとテンプレート](styling-and-templating.md)
