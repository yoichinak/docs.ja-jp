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
ms.openlocfilehash: 563f4a9fefe86b58f0dc6f0a4aec5cb285630616
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593404"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>ControlTemplate の作成による既存のコントロールの外観のカスタマイズ
<a name="introduction"></a> A<xref:System.Windows.Controls.ControlTemplate>視覚的な構造とコントロールの視覚的な動作を指定します。 コントロールの外観をカスタマイズするには、新しい it 提供することにより<xref:System.Windows.Controls.ControlTemplate>します。 作成するときに、 <xref:System.Windows.Controls.ControlTemplate>、その機能を変更することがなく、既存のコントロールの外観を置き換えます。 たとえば、行うことができます、ボタン、アプリケーションで、既定の四角形から丸い形が、ボタンが引き続き発生、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
 このトピックでは、のさまざまな部分を説明します、 <xref:System.Windows.Controls.ControlTemplate>、単純な作成方法を示します<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>外観をカスタマイズできるように、コントロールのコントロール コントラクトを理解する方法について説明します。 作成するため、<xref:System.Windows.Controls.ControlTemplate>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コードを記述せず、コントロールの外観を変更することができます。 また、カスタム コントロール テンプレートを作成するために、Microsoft Expression Blend などのデザイナーを使用することもできます。 このトピックでの例では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の外観をカスタマイズする、<xref:System.Windows.Controls.Button>し、このトピックの最後に詳細な例を一覧表示します。 Expression Blend の使用方法の詳細については、「[テンプレートをサポートするコントロールのスタイル処理](https://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。  
  
 次の図に示す、<xref:System.Windows.Controls.Button>を使用して、<xref:System.Windows.Controls.ControlTemplate>このトピックで作成されます。  
  
 ![カスタム コントロール テンプレート付きのボタンをクリックします。](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
カスタム コントロール テンプレートを使用しているボタン  
  
 ![赤い境界線付きのボタンをクリックします。](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
カスタム コントロール テンプレートを使用したボタンにマウス ポインターを置いた状態  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、「[コントロール](index.md)」で説明したコントロールとスタイルの作成方法および使用方法を理解していることを前提としています。 継承する要素にこのトピックで説明する概念を適用、<xref:System.Windows.Controls.Control>クラスを除く、 <xref:System.Windows.Controls.UserControl>。 適用することはできません、<xref:System.Windows.Controls.ControlTemplate>を<xref:System.Windows.Controls.UserControl>します。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>ControlTemplate の作成が必要な場合  
 コントロールが、多くのプロパティをなどある<xref:System.Windows.Controls.Border.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>、および<xref:System.Windows.Controls.Control.FontFamily%2A>コントロールの外観のさまざまな側面を指定する設定できますが、これらのプロパティを設定して行うことができる変更は制限されています。 たとえば、設定、<xref:System.Windows.Controls.Control.Foreground%2A>プロパティを青と<xref:System.Windows.Controls.Control.FontStyle%2A>上に斜体、<xref:System.Windows.Controls.CheckBox>します。  
  
 新たに作成することはできません<xref:System.Windows.Controls.ControlTemplate>、コントロールでコントロールをすべてすべて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションは、カスタムのルック アンド フィールでアプリケーションを作成する機能が制限されることと同じ一般的な外観になります。 既定では、すべて<xref:System.Windows.Controls.CheckBox>はのような特徴があります。 コンテンツなど、<xref:System.Windows.Controls.CheckBox>選択インジケーターの右側には常にチェック マークは、常に示すために使用して、<xref:System.Windows.Controls.CheckBox>が選択されています。  
  
 作成する、<xref:System.Windows.Controls.ControlTemplate>は何がコントロールに他のプロパティを設定できないコントロールの外観をカスタマイズする場合。 例では、<xref:System.Windows.Controls.CheckBox>選択インジケーター上に配置する チェック ボックスのコンテンツをしながらすることを示すために、X、<xref:System.Windows.Controls.CheckBox>が選択されています。 これらの変更を指定する、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.CheckBox>します。  
  
 次の図は、 <xref:System.Windows.Controls.CheckBox> 、既定値を使用する<xref:System.Windows.Controls.ControlTemplate>します。  
  
 ![既定のコントロール テンプレートのチェック ボックスをオンします。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
既定のコントロール テンプレートを使用する CheckBox  
  
 次の図は、<xref:System.Windows.Controls.CheckBox>カスタムを使用する<xref:System.Windows.Controls.ControlTemplate>のコンテンツを配置する、<xref:System.Windows.Controls.CheckBox>選択インジケーター上に X が表示されますと、<xref:System.Windows.Controls.CheckBox>が選択されています。  
  
 ![カスタム コントロール テンプレートを使用してチェック ボックスをオンします。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
カスタム コントロール テンプレートを使用する CheckBox  
  
 <xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.CheckBox>このサンプルでは、比較的複雑なため、このトピックで作成する簡単な例を使用して、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>します。  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>コントロールの視覚的な構造の変更  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、通常、コントロールは複合<xref:System.Windows.FrameworkElement>オブジェクト。 作成するとき、 <xref:System.Windows.Controls.ControlTemplate>、結合する<xref:System.Windows.FrameworkElement>1 つのコントロールを構築するオブジェクト。 A<xref:System.Windows.Controls.ControlTemplate>が 1 つだけ必要<xref:System.Windows.FrameworkElement>のルート要素として。 ルート要素が、通常他を含む<xref:System.Windows.FrameworkElement>オブジェクト。 複数のオブジェクトを組み合わせて、コントロールの視覚的な構造を構成します。  
  
 次の例では、カスタム<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>します。 <xref:System.Windows.Controls.ControlTemplate>の視覚的な構造を作成し、<xref:System.Windows.Controls.Button>します。 この例では、ボタンの上にマウス ポインターを移動しても、ボタンをクリックしても、その外観は変化しません。 状態に応じて外観が変化するボタンについては、このトピックで後述します。  
  
 この例では、以下のパーツで視覚的な構造を構成しています。  
  
- A<xref:System.Windows.Controls.Border>という`RootElement`テンプレートのルートとして機能する<xref:System.Windows.FrameworkElement>します。  
  
- A<xref:System.Windows.Controls.Grid>の子である`RootElement`します。  
  
- A<xref:System.Windows.Controls.ContentPresenter>ボタンのコンテンツを表示します。 <xref:System.Windows.Controls.ContentPresenter>により、任意の種類のオブジェクトを表示できます。  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>TemplateBinding を使用してコントロールのプロパティの機能を維持する方法  
 新規に作成するときに<xref:System.Windows.Controls.ControlTemplate>、まだするパブリック プロパティを使用して、コントロールの外観を変更する可能性があります。 [TemplateBinding](../advanced/templatebinding-markup-extension.md)マークアップ拡張機能内にある要素のプロパティのバインド、<xref:System.Windows.Controls.ControlTemplate>コントロールによって定義されているパブリック プロパティにします。 [TemplateBinding](../advanced/templatebinding-markup-extension.md) を使用すると、コントロールのプロパティをテンプレートのパラメーターとして機能させることができます。 つまり、コントロールのプロパティを設定すると、その値は [TemplateBinding](../advanced/templatebinding-markup-extension.md) が機能している要素に渡されます。  
  
 次の例を使用する前の例の一部を繰り返す、 [TemplateBinding](../advanced/templatebinding-markup-extension.md)に含まれている要素のプロパティをバインドするマークアップ拡張機能、<xref:System.Windows.Controls.ControlTemplate>ボタンによって定義されているパブリック プロパティにします。  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 この例で、<xref:System.Windows.Controls.Grid>がその<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>プロパティ テンプレートにバインド<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>します。 <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>がテンプレート バインディングされて、同じを使用する複数のボタンを作成する<xref:System.Windows.Controls.ControlTemplate>設定と、<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>に異なる値の各ボタン。 場合<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>が内の要素のプロパティにバインドされたテンプレートは、<xref:System.Windows.Controls.ControlTemplate>で、設定、<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>ボタンがない影響ボタンの外観にします。  
  
 2 つのプロパティの名前は同じである必要はありません。 上記の例では、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>のプロパティ、<xref:System.Windows.Controls.Button>にテンプレートがバインド、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>のプロパティ、<xref:System.Windows.Controls.ContentPresenter>します。 これにより、ボタンのコンテンツを水平方向に配置できます。 <xref:System.Windows.Controls.ContentPresenter> という名前のプロパティはありません。 `HorizontalContentAlignment`、が<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>にバインドできる<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>します。 プロパティをテンプレート バインディングするときは、ターゲットとソースのプロパティが同じ型であることを確認してください。  
  
 <xref:System.Windows.Controls.Control>クラスに設定されている場合は、コントロールに影響を与える、コントロール テンプレートで使用する必要がありますをいくつかのプロパティを定義します。 どの<xref:System.Windows.Controls.ControlTemplate>使用して、プロパティ、プロパティに依存します。 <xref:System.Windows.Controls.ControlTemplate>で、次の方法のいずれかのプロパティを使用する必要があります。  
  
- 内の要素、<xref:System.Windows.Controls.ControlTemplate>テンプレートのプロパティにバインドします。  
  
- 内の要素、<xref:System.Windows.Controls.ControlTemplate>プロパティを親から継承<xref:System.Windows.FrameworkElement>します。  
  
 次の表に、コントロールから継承されるビジュアル プロパティ、<xref:System.Windows.Controls.Control>クラス。 また、コントロールの既定のコントロール テンプレートで継承されたプロパティ値を使用するかどうか、テンプレート バインディングする必要があるかどうかも示します。  
  
|プロパティ|使用するメソッド|  
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
  
 テーブルから継承されるビジュアル プロパティのみを一覧表示、<xref:System.Windows.Controls.Control>クラス。 別に、表に示したプロパティ、コントロールが継承される場合も、 <xref:System.Windows.FrameworkElement.DataContext%2A>、 <xref:System.Windows.FrameworkElement.Language%2A>、および<xref:System.Windows.Controls.TextBlock.TextDecorations%2A>親フレームワーク要素からのプロパティ。  
  
 また場合、<xref:System.Windows.Controls.ContentPresenter>では、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ContentControl>、<xref:System.Windows.Controls.ContentPresenter>に自動的にバインドされます、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>と<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティ。 同様に、<xref:System.Windows.Controls.ItemsPresenter>内にある、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ItemsControl>に自動的にバインドは、<xref:System.Windows.Controls.ItemsControl.Items%2A>と<xref:System.Windows.Controls.ItemsPresenter>プロパティ。  
  
 次の例を使用する 2 つのボタンの作成、<xref:System.Windows.Controls.ControlTemplate>前の例で定義されています。 例のセット、 <xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>、および<xref:System.Windows.Controls.Control.FontSize%2A>各ボタンのプロパティ。 設定、<xref:System.Windows.Controls.Control.Background%2A>プロパティは、これはテンプレートにバインドされているため、有効、<xref:System.Windows.Controls.ControlTemplate>します。 場合でも、<xref:System.Windows.Controls.Control.Foreground%2A>と<xref:System.Windows.Controls.Control.FontSize%2A>プロパティがテンプレート バインディングされて、その値が継承されるため、それらの設定には効果があります。  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 前の例では、次の図のような出力を生成します。  
  
 ![2 つのボタンの 1 つの blue と紫色です。](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
背景色が異なる 2 つのボタン  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>状態に応じたコントロールの外観の変化  
 既定の外観のボタンと前の例のボタンの違いは、既定のボタンが別の状態になったときにわずかに変化することです。 たとえば、ボタンをクリックしたときやマウス ポインターをボタンの上に置いたときに、既定のボタンは外観が変化します。 ですが、<xref:System.Windows.Controls.ControlTemplate>機能は変更されませんが、コントロールのコントロールの視覚的な動作は変更します。 視覚的な動作とは、コントロールが特定の状態にあるときの外観を指しています。 コントロールの機能と視覚的な動作の違いを理解するために、ボタンの例について考えてみます。 ボタンの機能を発生させる、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>がクリックされたときに、ボタンの視覚的な動作が指す、または次の押されたときに、その外観を変更します。  
  
 使用する<xref:System.Windows.VisualState>特定の状態にあるときに、コントロールの外観を指定するオブジェクト。 A<xref:System.Windows.VisualState>が含まれています、<xref:System.Windows.Media.Animation.Storyboard>含まれている要素の外観を変更する、<xref:System.Windows.Controls.ControlTemplate>します。 コントロールのロジックを使用して状態を変更するために発生するコードを記述する必要はありません、<xref:System.Windows.VisualStateManager>します。 コントロールがで指定されている状態に入ったとき、<xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>プロパティ、<xref:System.Windows.Media.Animation.Storyboard>が開始されます。 コントロールの状態、終了時に、<xref:System.Windows.Media.Animation.Storyboard>を停止します。  
  
 次の例は、<xref:System.Windows.VisualState>の外観を変更する、<xref:System.Windows.Controls.Button>上にマウス ポインターの場合します。 <xref:System.Windows.Media.Animation.Storyboard>の色を変更することで、ボタンの境界線の色を変更、`BorderBrush`します。 参照する場合、<xref:System.Windows.Controls.ControlTemplate>例をこのトピックの先頭には、前述のとおりです`BorderBrush`の名前を指定します、<xref:System.Windows.Media.SolidColorBrush>に割り当てられた、<xref:System.Windows.Controls.Border.Background%2A>の<xref:System.Windows.Controls.Border>します。  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 このコントロールは、コントロール コントラクトの一部として状態を定義する役割を果たします。詳細については、このトピックの「[コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法](#customizing_other_controls_by_understanding_the_control_contract)」で後述します。 次の表は、指定されている状態を一覧表示、<xref:System.Windows.Controls.Button>します。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|押されている|CommonStates|コントロールが押されています。|  
|無効|CommonStates|コントロールが無効になっています。|  
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|  
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|  
  
 <xref:System.Windows.Controls.Button> 2 つの状態グループを定義します。、`CommonStates`グループが含まれています、 `Normal`、 `MouseOver`、 `Pressed`、および`Disabled`状態。 `FocusStates` グループには、`Focused` 状態と `Unfocused` 状態が含まれます。 同じ状態グループ内の状態を同時に複数指定することはできません。 コントロールが取り得る状態は、常に 1 グループにつき 1 つです。 たとえば、<xref:System.Windows.Controls.Button>マウス ポインターがない場合でも、そのため、フォーカスを持つことができます、<xref:System.Windows.Controls.Button>で、`Focused`状態、 `MouseOver`、 `Pressed`、または`Normal`状態。  
  
 追加する<xref:System.Windows.VisualState>オブジェクトを<xref:System.Windows.VisualStateGroup>オブジェクト。 追加する<xref:System.Windows.VisualStateGroup>オブジェクトを<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>添付プロパティ。 次の例では、定義、<xref:System.Windows.VisualState>オブジェクトに対する、 `Normal`、 `MouseOver`、および`Pressed`はすべての状態、`CommonStates`グループ。 <xref:System.Windows.VisualState.Name%2A>それぞれの<xref:System.Windows.VisualState>上記の表に名前と一致します。 `Disabled` の状態および `FocusStates` グループの状態は、例を簡潔にするために省略していますが、このトピックの最後で紹介している完全なコード例には含まれています。  
  
> [!NOTE]
>  設定してください、<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>添付プロパティをルート<xref:System.Windows.FrameworkElement>の<xref:System.Windows.Controls.ControlTemplate>します。  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 前の例では、次の図のような出力を生成します。  
  
 ![カスタム コントロール テンプレート付きのボタンをクリックします。](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
通常状態のカスタム コントロール テンプレートを使用しているボタン  
  
 ![赤い境界線付きのボタンをクリックします。](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
マウス オーバー状態のカスタム コントロール テンプレートを使用しているボタン  
  
 ![罫線は、押されたボタンに透過的です。](./media/ndp-buttonpressed.png "NDP_ButtonPressed")  
押された状態のカスタム コントロール テンプレートを使用しているボタン  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールの視覚的な状態については、「[コントロールのスタイルとテンプレート](control-styles-and-templates.md)」を参照してください。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>状態間を遷移するときのコントロールの動作の指定  
 前の例では、ボタンをクリックしたときにもボタンの外観が変化しましたが、ボタンを 1 秒間押したままにしない限り、効果を確認できません。 既定では、アニメーションが開始されるまでに 1 秒かかります。 ユーザーは をクリックして、短時間でボタンをリリースする可能性が高いため、視覚的フィードバックがのままにする場合に有効になりませんが、<xref:System.Windows.Controls.ControlTemplate>既定の状態。  
  
 1 つの状態から別のコントロールを追加することでスムーズに移行するために発生するアニメーションが必要な時間の量を指定する<xref:System.Windows.VisualTransition>オブジェクトを<xref:System.Windows.Controls.ControlTemplate>します。 作成するときに、<xref:System.Windows.VisualTransition>次の 1 つ以上を指定します。  
  
- 状態間の遷移を開始するまでに要する時間。  
  
- 遷移時に発生するコントロールの外観への追加の変更。  
  
- どの状態、<xref:System.Windows.VisualTransition>に適用されます。  
  
### <a name="specifying-the-duration-of-a-transition"></a>遷移の継続時間の指定  
 設定の移行にかかる時間を指定することができます、<xref:System.Windows.VisualTransition.GeneratedDuration%2A>プロパティ。 上記の例では、<xref:System.Windows.VisualState>ボタンが押されたが、アニメーションがかかりすぎる場合、ボタンがすぐに押したときし、離したときに、ボタンの境界線が透明にことを指定します。 使用することができます、<xref:System.Windows.VisualTransition>押された状態に遷移するコントロールでは、時間数を指定します。 次の例では、コントロールが押された状態になるのに要する時間を 1/100 秒に指定しています。  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>遷移時にコントロールの外観の変更を指定する方法  
 <xref:System.Windows.VisualTransition>が含まれています、<xref:System.Windows.Media.Animation.Storyboard>コントロールの状態が遷移するときに開始します。 たとえば、コントロールが `MouseOver` 状態から `Normal` 状態に遷移する場合に、特定のアニメーションが実行されるように指定できます。 次の例では、作成、<xref:System.Windows.VisualTransition>こと、ユーザーがボタンからマウス ポインターを移動するとボタンの境界線の変更が青、し、黄、黒に 1.5 秒でを指定します。  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>VisualTransition を適用するタイミングの指定  
 A <xref:System.Windows.VisualTransition> 、特定の状態のみに適用する制限できるまたは適用することができますのどの時点の状態間の遷移を制御します。 上記の例では、<xref:System.Windows.VisualTransition>からコントロールになったときに適用、`MouseOver`状態、`Normal`状態を前に、の例で、<xref:System.Windows.VisualTransition>コントロールに入るときに適用されます、`Pressed`状態。 時間を制限する、<xref:System.Windows.VisualTransition>設定が適用される、<xref:System.Windows.VisualTransition.To%2A>と<xref:System.Windows.VisualTransition.From%2A>プロパティ。 次の表では、制限が最も厳しいレベルから最も緩いレベルまでを一覧にして示しています。  
  
|制限の種類|値します。|値|  
|-------------------------|-------------------|-----------------|  
|指定した状態から別の指定した状態まで|名前を <xref:System.Windows.VisualState>|名前を <xref:System.Windows.VisualState>|  
|任意の状態から指定された状態まで|未設定|名前を <xref:System.Windows.VisualState>|  
|指定した状態から任意の状態まで|名前を <xref:System.Windows.VisualState>|未設定|  
|他の状態の任意の状態から|未設定|未設定|  
  
 複数<xref:System.Windows.VisualTransition>内のオブジェクトを<xref:System.Windows.VisualStateGroup>を参照するのには同じ状態には、前の表に示す順序で使用されます。 次の例では、2 つ<xref:System.Windows.VisualTransition>オブジェクト。 コントロールが遷移するときに、`Pressed`状態、 `MouseOver` 、状態、<xref:System.Windows.VisualTransition>両方を持つ<xref:System.Windows.VisualTransition.From%2A>と<xref:System.Windows.VisualTransition.To%2A>セットが使用されます。 コントロールが `Pressed` ではない状態から `MouseOver` 状態に遷移するときには、別の状態を使用します。  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup>が、<xref:System.Windows.VisualStateGroup.Transitions%2A>プロパティを含む、<xref:System.Windows.VisualTransition>オブジェクトに適用される、<xref:System.Windows.VisualState>内のオブジェクト、<xref:System.Windows.VisualStateGroup>します。 として、<xref:System.Windows.Controls.ControlTemplate>をいずれかを含めることが、作成者、<xref:System.Windows.VisualTransition>します。 ただし場合、<xref:System.Windows.VisualTransition.To%2A>と<xref:System.Windows.VisualTransition.From%2A>プロパティに追加されていない状態の名前に設定されて、 <xref:System.Windows.VisualStateGroup>、<xref:System.Windows.VisualTransition>は無視されます。  
  
 次の例は、<xref:System.Windows.VisualStateGroup>の`CommonStates`します。 例では、定義、<xref:System.Windows.VisualTransition>のボタンの次の各遷移します。  
  
- `Pressed` 状態への遷移。  
  
- `MouseOver` 状態への遷移。  
  
- `Pressed` 状態から `MouseOver` 状態への遷移。  
  
- `MouseOver` 状態から `Normal` 状態への遷移。  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法  
 使用するコントロールを<xref:System.Windows.Controls.ControlTemplate>その視覚的な構造を指定する (を使用して<xref:System.Windows.FrameworkElement>オブジェクト) と視覚的な動作 (を使用して<xref:System.Windows.VisualState>オブジェクト)、パーツ コントロール モデルを使用します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 に含まれるコントロールの多くは、このモデルを採用しています。 各部分を<xref:System.Windows.Controls.ControlTemplate>作成者を認識する必要がありますが、コントロール コントラクトを通じて伝達されます。 コントロール コントラクトのパーツについて理解すると、パーツ コントロール モデルを採用するあらゆるコントロールの外観をカスタマイズできます。  
  
 コントロール コントラクトには、次の 3 つの要素があります。  
  
- コントロールのロジックが使用する視覚的要素。  
  
- コントロールの状態および各状態が所属するグループ。  
  
- コントロールに対して視覚的に作用するパブリック プロパティ。  
  
### <a name="visual-elements-in-the-control-contract"></a>コントロール コントラクトの視覚的要素  
 コントロールのロジックと対話することがあります、<xref:System.Windows.FrameworkElement>内にある、<xref:System.Windows.Controls.ControlTemplate>します。 たとえば、コントロールがその要素のイベントを処理する場合などです。 コントロールが特定の検索と<xref:System.Windows.FrameworkElement>で、 <xref:System.Windows.Controls.ControlTemplate>、その情報を伝える必要があります、<xref:System.Windows.Controls.ControlTemplate>作成者です。 コントロールを使用して、<xref:System.Windows.TemplatePartAttribute>を伝えるの種類が必要ですが、要素と要素の名前にする必要があります。 <xref:System.Windows.Controls.Button>が<xref:System.Windows.FrameworkElement>など、コントロール コントラクトが、他のコントロールのパーツ、 <xref:System.Windows.Controls.ComboBox>、操作を行います。  
  
 次の例は、<xref:System.Windows.TemplatePartAttribute>オブジェクトで指定されている、<xref:System.Windows.Controls.ComboBox>クラス。 ロジック<xref:System.Windows.Controls.ComboBox>が期待する、<xref:System.Windows.Controls.TextBox>という名前の`PART_EditableTextBox`と<xref:System.Windows.Controls.Primitives.Popup>という名前`PART_Popup`でその<xref:System.Windows.Controls.ControlTemplate>します。  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 次の例は、簡略化された<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ComboBox>で指定されている要素を含む、<xref:System.Windows.TemplatePartAttribute>でオブジェクトを<xref:System.Windows.Controls.ComboBox>クラス。  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>コントロール コントラクトの状態  
 コントロールの状態もコントロール コントラクトの一部です。 作成する例を<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>の外観を指定する方法を示しています、<xref:System.Windows.Controls.Button>状態に応じて。 作成する、<xref:System.Windows.VisualState>各状態を指定し、すべての<xref:System.Windows.VisualState>オブジェクトをその共有を<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A>で、 <xref:System.Windows.VisualStateGroup>」の説明に従って、[状態に応じたコントロールの外観を変更する](#changing_the_appearance_of_a_control_depending_on_its_state)この以前トピックです。 サードパーティ製のコントロールを使用して状態を指定する必要があります、 <xref:System.Windows.TemplateVisualStateAttribute>、コントロール テンプレートを作成するためのコントロールの状態を公開する、Expression Blend などのデザイナー ツールを有効にします。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールのコントロール コントラクトについては、「[コントロールのスタイルとテンプレート](control-styles-and-templates.md)」を参照してください。  
  
### <a name="properties-in-the-control-contract"></a>コントロール コントラクトのプロパティ  
 コントロールに視覚的な影響を与えるパブリック プロパティも、コントロール コントラクトに含まれています。 新しいを作成することがなく、コントロールの外観を変更するこれらのプロパティを設定する<xref:System.Windows.Controls.ControlTemplate>します。 使用することも、 [TemplateBinding](../advanced/templatebinding-markup-extension.md)に含まれている要素のプロパティをバインドするマークアップ拡張機能、<xref:System.Windows.Controls.ControlTemplate>で定義されているパブリック プロパティに、<xref:System.Windows.Controls.Button>します。  
  
 次の例では、ボタンのコントロール コントラクトを示します。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 作成するときに、 <xref:System.Windows.Controls.ControlTemplate>、既存の開始する最も簡単なことがよくあります<xref:System.Windows.Controls.ControlTemplate>に変更を加えるとします。 既存を変更するには、次のいずれかを行うことができます<xref:System.Windows.Controls.ControlTemplate>:  
  
- Expression Blend などのデザイナーを使用します。デザイナーには、コントロール テンプレートを作成するためのグラフィカル ユーザー インターフェイスが用意されています。 詳細については、「[テンプレートをサポートするコントロールのスタイル処理](https://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。  
  
- 既定値を取得<xref:System.Windows.Controls.ControlTemplate>して編集できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属する既定のコントロール テンプレートについては、「[デフォルトの WPF テーマ](https://go.microsoft.com/fwlink/?LinkID=158252)」を参照してください。  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>コード例全体  
 次の例は、完全な<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate>このトピックで説明しました。  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>関連項目

- [スタイルとテンプレート](styling-and-templating.md)
