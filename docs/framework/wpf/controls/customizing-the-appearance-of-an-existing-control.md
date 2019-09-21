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
ms.openlocfilehash: 63a0b724b71c4a4901c2dedcf502045a75ec405c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933731"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>ControlTemplate の作成による既存のコントロールの外観のカスタマイズ
<a name="introduction"></a>は<xref:System.Windows.Controls.ControlTemplate> 、コントロールの視覚的な構造と視覚的な動作を指定します。 コントロールの外観は、新しい<xref:System.Windows.Controls.ControlTemplate>を指定することによってカスタマイズできます。 を<xref:System.Windows.Controls.ControlTemplate>作成すると、既存のコントロールの外観は、その機能を変更せずに置き換えることができます。 たとえば、既定の四角形の形ではなく、アプリケーションのボタンを丸めることができますが、ボタンはイベントを<xref:System.Windows.Controls.Primitives.ButtonBase.Click>発生させます。  
  
 このトピック<xref:System.Windows.Controls.ControlTemplate>では、のさまざまな部分について説明し、 <xref:System.Windows.Controls.Button>の簡単<xref:System.Windows.Controls.ControlTemplate>なを作成する方法と、コントロールのコントロールコントラクトを理解してその外観をカスタマイズできるようにする方法について説明します。 <xref:System.Windows.Controls.ControlTemplate> で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を作成するので、コードを記述することなく、コントロールの外観を変更できます。 また、カスタム コントロール テンプレートを作成するために、Microsoft Expression Blend などのデザイナーを使用することもできます。 このトピックでは、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の外観<xref:System.Windows.Controls.Button>をカスタマイズするの例を示し、トピックの最後にある完全な例を示します。 Expression Blend の使用方法の詳細については、「[テンプレートをサポートするコントロールのスタイル処理](https://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。  
  
 次の図は、 <xref:System.Windows.Controls.Button>このトピックで<xref:System.Windows.Controls.ControlTemplate>作成したを使用するを示しています。  
  
 ![カスタムコントロールテンプレートを持つボタン。](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
カスタム コントロール テンプレートを使用しているボタン  
  
 ![赤い枠線付きのボタン。](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
カスタム コントロール テンプレートを使用したボタンにマウス ポインターを置いた状態  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、「[コントロール](index.md)」で説明したコントロールとスタイルの作成方法および使用方法を理解していることを前提としています。 このトピックで説明する概念は、 <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.UserControl>を除き、クラスを継承する要素に適用されます。 <xref:System.Windows.Controls.ControlTemplate> を<xref:System.Windows.Controls.UserControl>に適用することはできません。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>ControlTemplate の作成が必要な場合  
 コントロールには<xref:System.Windows.Controls.Border.Background%2A>、、 <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontFamily%2A>、などの多くのプロパティがあり、コントロールの外観のさまざまな側面を指定するように設定できますが、これらのプロパティを設定することによって行うことができる変更は制限されます。 たとえば、で<xref:System.Windows.Controls.Control.Foreground%2A> は、<xref:System.Windows.Controls.Control.FontStyle%2A>プロパティを blue に、italic を italic に設定できます。<xref:System.Windows.Controls.CheckBox>  
  
 コントロール用の新しい<xref:System.Windows.Controls.ControlTemplate>を作成する機能がない場合、すべてのベースのアプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のすべてのコントロールの全般的な外観は同じになります。これにより、カスタムのルックアンドフィールでアプリケーションを作成する機能が制限されます。 既定では、 <xref:System.Windows.Controls.CheckBox>すべての特性が類似しています。 たとえば、の<xref:System.Windows.Controls.CheckBox>コンテンツは常に選択インジケーターの右側にあり、チェックマークはが選択されて<xref:System.Windows.Controls.CheckBox>いることを示すために常に使用されます。  
  
 コントロールの他<xref:System.Windows.Controls.ControlTemplate>のプロパティが行う設定よりも、コントロールの外観をカスタマイズする場合は、を作成します。 の<xref:System.Windows.Controls.CheckBox>例では、チェックボックスの内容を選択インジケーターの上に配置し、 <xref:System.Windows.Controls.CheckBox>が選択されていることを示す X を使用するとします。 これら<xref:System.Windows.Controls.ControlTemplate>の変更は、 <xref:System.Windows.Controls.CheckBox>ので指定します。  
  
 次の図は、 <xref:System.Windows.Controls.CheckBox>既定値<xref:System.Windows.Controls.ControlTemplate>を使用するを示しています。  
  
 ![既定のコントロールテンプレートを含むチェックボックス。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
既定のコントロール テンプレートを使用する CheckBox  
  
 次の図は、 <xref:System.Windows.Controls.CheckBox>カスタム<xref:System.Windows.Controls.ControlTemplate>を使用して、選択インジケーターの<xref:System.Windows.Controls.CheckBox>上に上の内容を配置し、 <xref:System.Windows.Controls.CheckBox>が選択されている場合に X を表示するを示しています。  
  
 ![カスタムコントロールテンプレートを含むチェックボックス。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
カスタム コントロール テンプレートを使用する CheckBox  
  
 このサンプルののは<xref:System.Windows.Controls.ControlTemplate>比較的複雑であるため、このトピックでは<xref:System.Windows.Controls.ControlTemplate> 、のを作成するため<xref:System.Windows.Controls.Button>の簡単な例を使用します。 <xref:System.Windows.Controls.CheckBox>  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>コントロールの視覚的な構造の変更  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、多くの場合、コントロール<xref:System.Windows.FrameworkElement>は複合オブジェクトです。 を作成<xref:System.Windows.Controls.ControlTemplate>するときに、オブジェクト<xref:System.Windows.FrameworkElement>を結合して1つのコントロールを作成します。 に<xref:System.Windows.Controls.ControlTemplate>は、ルート要素<xref:System.Windows.FrameworkElement>として1つだけを指定する必要があります。 ルート要素には、通常<xref:System.Windows.FrameworkElement> 、他のオブジェクトが含まれます。 複数のオブジェクトを組み合わせて、コントロールの視覚的な構造を構成します。  
  
 次の例では、 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>のカスタムを作成します。 によって、 <xref:System.Windows.Controls.Button>のビジュアル構造が作成されます。<xref:System.Windows.Controls.ControlTemplate> この例では、ボタンの上にマウス ポインターを移動しても、ボタンをクリックしても、その外観は変化しません。 状態に応じて外観が変化するボタンについては、このトピックで後述します。  
  
 この例では、以下のパーツで視覚的な構造を構成しています。  
  
- テンプレート<xref:System.Windows.Controls.Border>の`RootElement` ルート<xref:System.Windows.FrameworkElement>として機能するという名前の。  
  
- <xref:System.Windows.Controls.Grid> の`RootElement`子である。  
  
- ボタンの内容を表示する。<xref:System.Windows.Controls.ContentPresenter> を<xref:System.Windows.Controls.ContentPresenter>使用すると、任意の型のオブジェクトを表示できます。  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>TemplateBinding を使用してコントロールのプロパティの機能を維持する方法  
 新しい<xref:System.Windows.Controls.ControlTemplate>を作成する場合でも、パブリックプロパティを使用してコントロールの外観を変更することをお勧めします。 [TemplateBinding](../advanced/templatebinding-markup-extension.md)マークアップ拡張機能は、にある要素のプロパティを、 <xref:System.Windows.Controls.ControlTemplate>コントロールで定義されているパブリックプロパティにバインドします。 [TemplateBinding](../advanced/templatebinding-markup-extension.md) を使用すると、コントロールのプロパティをテンプレートのパラメーターとして機能させることができます。 つまり、コントロールのプロパティを設定すると、その値は [TemplateBinding](../advanced/templatebinding-markup-extension.md) が機能している要素に渡されます。  
  
 次の例では、前の例の部分を繰り返します。この例では、 [TemplateBinding](../advanced/templatebinding-markup-extension.md)マークアップ拡張機能<xref:System.Windows.Controls.ControlTemplate>を使用して、にある要素のプロパティを、ボタンで定義されているパブリックプロパティにバインドしています。  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 この例では、 <xref:System.Windows.Controls.Grid>の<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>プロパティテンプレートがに<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>バインドされています。 は<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>テンプレートにバインドされているため、同じ<xref:System.Windows.Controls.ControlTemplate>を使用する複数のボタン<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>を作成し、各ボタンでを異なる値に設定できます。 が<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>の<xref:System.Windows.Controls.ControlTemplate>要素のプロパティにテンプレートバインドされていない場合、ボタン<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>のを設定しても、ボタンの外観には影響しません。  
  
 2 つのプロパティの名前は同じである必要はありません。 前の例<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>では、の<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>プロパティ<xref:System.Windows.Controls.Button>は、 <xref:System.Windows.Controls.ContentPresenter>のプロパティにバインドされています。 これにより、ボタンのコンテンツを水平方向に配置できます。 <xref:System.Windows.Controls.ContentPresenter>にはという名前`HorizontalContentAlignment`のプロパティはありませんが<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> 、にバインドできます。 プロパティをテンプレート バインディングするときは、ターゲットとソースのプロパティが同じ型であることを確認してください。  
  
 クラス<xref:System.Windows.Controls.Control>は、コントロールテンプレートが設定されたときにコントロールに影響を与えるために使用する必要があるいくつかのプロパティを定義します。 が<xref:System.Windows.Controls.ControlTemplate>プロパティを使用する方法は、プロパティによって異なります。 では、次のいずれかの方法でプロパティを使用する必要があります。<xref:System.Windows.Controls.ControlTemplate>  
  
- <xref:System.Windows.Controls.ControlTemplate>テンプレート内の要素は、プロパティにバインドされます。  
  
- の<xref:System.Windows.Controls.ControlTemplate>要素は、親<xref:System.Windows.FrameworkElement>からプロパティを継承します。  
  
 次の表に、 <xref:System.Windows.Controls.Control>クラスからコントロールによって継承されるビジュアルプロパティの一覧を示します。 また、コントロールの既定のコントロール テンプレートで継承されたプロパティ値を使用するかどうか、テンプレート バインディングする必要があるかどうかも示します。  
  
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
  
 このテーブルには、 <xref:System.Windows.Controls.Control>クラスから継承されたビジュアルプロパティのみが表示されます。 テーブルに示されているプロパティとは別に、コントロールは<xref:System.Windows.FrameworkElement.DataContext%2A>、 <xref:System.Windows.FrameworkElement.Language%2A>、、および<xref:System.Windows.Controls.TextBlock.TextDecorations%2A>の各プロパティを親フレームワーク要素から継承することもあります。  
  
 また<xref:System.Windows.Controls.ContentPresenter> 、 <xref:System.Windows.Controls.ContentControl.Content%2A>が<xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>の<xref:System.Windows.Controls.ContentControl>である場合、はプロパティとプロパティに自動的にバインドされます。<xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ItemsControl.Items%2A>同様に、 <xref:System.Windows.Controls.ItemsPresenter> の<xref:System.Windows.Controls.ItemsControl>に含まれるは、プロパティとプロパティに自動的にバインドされます。<xref:System.Windows.Controls.ItemsPresenter>  
  
 次の例では、前の例<xref:System.Windows.Controls.ControlTemplate>で定義したを使用する2つのボタンを作成します。 この例では<xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>各ボタン<xref:System.Windows.Controls.Control.FontSize%2A>の、、およびの各プロパティを設定します。 プロパティの<xref:System.Windows.Controls.Control.Background%2A>設定は、 <xref:System.Windows.Controls.ControlTemplate>テンプレートがにバインドされているため、効果があります。 <xref:System.Windows.Controls.Control.Foreground%2A>プロパティと<xref:System.Windows.Controls.Control.FontSize%2A>プロパティがテンプレートにバインドされていない場合でも、値が継承されるため、設定が影響を受けます。  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 前の例では、次の図のような出力を生成します。  
  
 ![青と紫色の2つのボタン。](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
背景色が異なる 2 つのボタン  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>状態に応じたコントロールの外観の変化  
 既定の外観のボタンと前の例のボタンの違いは、既定のボタンが別の状態になったときにわずかに変化することです。 たとえば、ボタンをクリックしたときやマウス ポインターをボタンの上に置いたときに、既定のボタンは外観が変化します。 <xref:System.Windows.Controls.ControlTemplate>はコントロールの機能を変更しませんが、コントロールの視覚的な動作を変更します。 視覚的な動作とは、コントロールが特定の状態にあるときの外観を指しています。 コントロールの機能と視覚的な動作の違いを理解するために、ボタンの例について考えてみます。 ボタンの機能は、クリックされ<xref:System.Windows.Controls.Primitives.ButtonBase.Click>たときにイベントを発生させますが、ボタンの視覚的な動作は、ポイントまたは押されたときの外観を変更することです。  
  
 オブジェクトを<xref:System.Windows.VisualState>使用して、コントロールが特定の状態にあるときの外観を指定します。 には、 <xref:System.Windows.Media.Animation.Storyboard>内の<xref:System.Windows.Controls.ControlTemplate>要素の外観を変更するが含まれています。<xref:System.Windows.VisualState> コントロールのロジックがを使用<xref:System.Windows.VisualStateManager>して状態を変更するため、このようなコードを記述する必要はありません。 コントロールが<xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>プロパティによって指定された状態になると<xref:System.Windows.Media.Animation.Storyboard> 、が開始されます。 コントロールが状態を終了すると、 <xref:System.Windows.Media.Animation.Storyboard>は停止します。  
  
 次の例は、 <xref:System.Windows.VisualState>マウスポインターが上にある<xref:System.Windows.Controls.Button>ときのの外観を変更するを示しています。 は<xref:System.Windows.Media.Animation.Storyboard> 、`BorderBrush`の色を変更することによって、ボタンの境界線の色を変更します。 このトピックの冒頭に<xref:System.Windows.Controls.ControlTemplate>ある例を参照すると、 <xref:System.Windows.Media.SolidColorBrush>がのに<xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Border>割り当てら`BorderBrush`れているの名前であることを思い出してください。  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 このコントロールは、コントロール コントラクトの一部として状態を定義する役割を果たします。詳細については、このトピックの「[コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法](#customizing_other_controls_by_understanding_the_control_contract)」で後述します。 に指定されている状態を次の表<xref:System.Windows.Controls.Button>に示します。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|押されている|CommonStates|コントロールが押されています。|  
|Disabled|CommonStates|コントロールが無効になっています。|  
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|  
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|  
  
 は<xref:System.Windows.Controls.Button> 2 つの状態グループを`CommonStates`定義します`Normal`。 `MouseOver` `Pressed`グループには`Disabled` 、、、およびの各状態が含まれます。 `FocusStates` グループには、`Focused` 状態と `Unfocused` 状態が含まれます。 同じ状態グループ内の状態を同時に複数指定することはできません。 コントロールが取り得る状態は、常に 1 グループにつき 1 つです。 <xref:System.Windows.Controls.Button>たとえば、は、マウスポインターが上にない場合でもフォーカスを持つことができるので`Focused` 、状態の<xref:System.Windows.Controls.Button>は`MouseOver`、 `Pressed`、のいずれ`Normal`かの状態になります。  
  
 オブジェクトに<xref:System.Windows.VisualState>オブジェクトを<xref:System.Windows.VisualStateGroup>追加します。 添付<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>プロパティ<xref:System.Windows.VisualStateGroup>にオブジェクトを追加します。 次の例では<xref:System.Windows.VisualState> 、 `Normal`、 `MouseOver` `Pressed` 、`CommonStates`およびの各状態のオブジェクトを定義しています。これらはすべてグループに含まれています。 <xref:System.Windows.VisualState.Name%2A> それぞれ<xref:System.Windows.VisualState>のは、前の表の名前と一致します。 `Disabled` の状態および `FocusStates` グループの状態は、例を簡潔にするために省略していますが、このトピックの最後で紹介している完全なコード例には含まれています。  
  
> [!NOTE]
> の<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> ルート<xref:System.Windows.FrameworkElement>で添付プロパティを必ず設定してください。 <xref:System.Windows.Controls.ControlTemplate>  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 前の例では、次の図のような出力を生成します。  
  
 ![カスタムコントロールテンプレートを持つボタン。](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
通常状態のカスタム コントロール テンプレートを使用しているボタン  
  
 ![赤い枠線付きのボタン。](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
マウス オーバー状態のカスタム コントロール テンプレートを使用しているボタン  
  
 ![押されたボタンでは、境界線は透明になります。](./media/ndp-buttonpressed.png "NDP_ButtonPressed")  
押された状態のカスタム コントロール テンプレートを使用しているボタン  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールの視覚的な状態については、「[コントロールのスタイルとテンプレート](control-styles-and-templates.md)」を参照してください。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>状態間を遷移するときのコントロールの動作の指定  
 前の例では、ボタンをクリックしたときにもボタンの外観が変化しましたが、ボタンを 1 秒間押したままにしない限り、効果を確認できません。 既定では、アニメーションが開始されるまでに 1 秒かかります。 ユーザーがボタンをクリックしてすぐに解放する可能性が高いため、を既定の状態<xref:System.Windows.Controls.ControlTemplate>のままにしておくと、視覚的なフィードバックが有効になりません。  
  
 にオブジェクトを追加<xref:System.Windows.VisualTransition>することによって、 <xref:System.Windows.Controls.ControlTemplate>コントロールをある状態から別の状態にスムーズに遷移させるために、アニメーションが発生するまでの時間を指定できます。 を作成<xref:System.Windows.VisualTransition>するときは、次のいずれかまたは複数を指定します。  
  
- 状態間の遷移を開始するまでに要する時間。  
  
- 遷移時に発生するコントロールの外観への追加の変更。  
  
- <xref:System.Windows.VisualTransition>がに適用される状態。  
  
### <a name="specifying-the-duration-of-a-transition"></a>遷移の継続時間の指定  
 遷移の実行時間を指定するには、 <xref:System.Windows.VisualTransition.GeneratedDuration%2A>プロパティを設定します。 前の例には<xref:System.Windows.VisualState> 、ボタンが押されたときにボタンの境界線が透明になることを指定するがありますが、ボタンがすぐに押されて解放されると、アニメーションの処理に時間がかかりすぎます。 を<xref:System.Windows.VisualTransition>使用すると、コントロールが押された状態に遷移するまでの時間を指定できます。 次の例では、コントロールが押された状態になるのに要する時間を 1/100 秒に指定しています。  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>遷移時にコントロールの外観の変更を指定する方法  
 は<xref:System.Windows.VisualTransition> 、コントロール<xref:System.Windows.Media.Animation.Storyboard>が状態間を遷移するときに開始するを格納します。 たとえば、コントロールが `MouseOver` 状態から `Normal` 状態に遷移する場合に、特定のアニメーションが実行されるように指定できます。 次の例では<xref:System.Windows.VisualTransition> 、ユーザーがマウスポインターをボタンの上に移動したときに、ボタンの境界線が青に変わり、黄色の場合は1.5 秒で黒に変更されることを指定するを作成します。  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>VisualTransition を適用するタイミングの指定  
 は<xref:System.Windows.VisualTransition>特定の状態にのみ適用されるように制限できます。また、コントロールが状態間を遷移するたびに適用することもできます。 <xref:System.Windows.VisualTransition>前の例では、コントロールが状態`Normal` `MouseOver`から状態になると、が適用されます<xref:System.Windows.VisualTransition> 。その前の例では、コントロール`Pressed`が状態になるとが適用されます。 <xref:System.Windows.VisualTransition>が適用されるタイミングを制限するに<xref:System.Windows.VisualTransition.To%2A>は<xref:System.Windows.VisualTransition.From%2A> 、プロパティとプロパティを設定します。 次の表では、制限が最も厳しいレベルから最も緩いレベルまでを一覧にして示しています。  
  
|制限の種類|からの値|の値|  
|-------------------------|-------------------|-----------------|  
|指定した状態から別の指定した状態まで|の名前<xref:System.Windows.VisualState>|の名前<xref:System.Windows.VisualState>|  
|任意の状態から指定された状態まで|未設定|の名前<xref:System.Windows.VisualState>|  
|指定した状態から任意の状態まで|の名前<xref:System.Windows.VisualState>|未設定|  
|任意の状態から他の状態へ|未設定|未設定|  
  
 同じ状態を参照<xref:System.Windows.VisualTransition>している<xref:System.Windows.VisualStateGroup>内に複数のオブジェクトを含めることができますが、これらは、前の表で指定した順序で使用されます。 次の例では、2つ<xref:System.Windows.VisualTransition>のオブジェクトがあります。 `Pressed`コントロールが<xref:System.Windows.VisualTransition.To%2A>状態から`MouseOver`状態に遷移すると、との<xref:System.Windows.VisualTransition>両方<xref:System.Windows.VisualTransition.From%2A>を持つが使用されます。 コントロールが `Pressed` ではない状態から `MouseOver` 状態に遷移するときには、別の状態を使用します。  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualState> <xref:System.Windows.VisualStateGroup.Transitions%2A> <xref:System.Windows.VisualTransition>には、のオブジェクトに適用される<xref:System.Windows.VisualStateGroup>オブジェクトを含むプロパティがあります。<xref:System.Windows.VisualStateGroup> 作成者<xref:System.Windows.Controls.ControlTemplate>は自由に好きな<xref:System.Windows.VisualTransition>ものを含めることができます。 ただし、プロパティ<xref:System.Windows.VisualTransition.To%2A>と<xref:System.Windows.VisualTransition.From%2A>プロパティがに存在<xref:System.Windows.VisualStateGroup>し<xref:System.Windows.VisualTransition>ない状態名に設定されている場合、は無視されます。  
  
 次の例は、 <xref:System.Windows.VisualStateGroup>のを`CommonStates`示しています。 この例では<xref:System.Windows.VisualTransition> 、ボタンの次の遷移のそれぞれに対してを定義します。  
  
- `Pressed` 状態への遷移。  
  
- `MouseOver` 状態への遷移。  
  
- `Pressed` 状態から `MouseOver` 状態への遷移。  
  
- `MouseOver` 状態から `Normal` 状態への遷移。  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法  
 を<xref:System.Windows.Controls.ControlTemplate>使用してビジュアル構造 (オブジェクトを使用<xref:System.Windows.FrameworkElement> ) を指定し、ビジュアル動作 (オブジェクトを使用<xref:System.Windows.VisualState> ) を使用するコントロールは、パーツコントロールモデルを使用します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 に含まれるコントロールの多くは、このモデルを採用しています。 <xref:System.Windows.Controls.ControlTemplate>作成者が認識する必要があるパーツは、コントロールコントラクトを通じて伝達されます。 コントロール コントラクトのパーツについて理解すると、パーツ コントロール モデルを採用するあらゆるコントロールの外観をカスタマイズできます。  
  
 コントロール コントラクトには、次の 3 つの要素があります。  
  
- コントロールのロジックが使用する視覚的要素。  
  
- コントロールの状態および各状態が所属するグループ。  
  
- コントロールに対して視覚的に作用するパブリック プロパティ。  
  
### <a name="visual-elements-in-the-control-contract"></a>コントロール コントラクトの視覚的要素  
 コントロールのロジックが、 <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>にあると対話することがあります。 たとえば、コントロールがその要素のイベントを処理する場合などです。 コントロール<xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>で特定のを検索する場合は、その情報を作成者に伝える必要があります。 <xref:System.Windows.Controls.ControlTemplate> コントロールは、 <xref:System.Windows.TemplatePartAttribute>を使用して、想定される要素の型と、要素の名前を伝達します。 の<xref:System.Windows.Controls.Button>コントロールコントラクトに<xref:System.Windows.FrameworkElement>はパーツがありませんが、などの他の<xref:System.Windows.Controls.ComboBox>コントロールは、を実行します。  
  
 次の例は、 <xref:System.Windows.TemplatePartAttribute> <xref:System.Windows.Controls.ComboBox>クラスで指定されたオブジェクトを示しています。 <xref:System.Windows.Controls.ComboBox>のロジックでは、 `PART_Popup` <xref:System.Windows.Controls.Primitives.Popup>内の<xref:System.Windows.Controls.TextBox> という`PART_EditableTextBox`名前のとを検索する必要があります。<xref:System.Windows.Controls.ControlTemplate>  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 次<xref:System.Windows.Controls.ControlTemplate>の例は、 <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ComboBox>クラスの<xref:System.Windows.TemplatePartAttribute>オブジェクトによって指定された要素を含むの簡略化されたを示しています。  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>コントロール コントラクトの状態  
 コントロールの状態もコントロール コントラクトの一部です。 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>のを作成する例は、の状態に応じての外観を指定する方法を示しています。<xref:System.Windows.Controls.Button> このトピックの<xref:System.Windows.VisualState> 「[状態に応じてコントロールの外観を変更](#changing_the_appearance_of_a_control_depending_on_its_state)する」で<xref:System.Windows.VisualStateGroup>説明されているように、指定した各状態に対してを作成し、を共有<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A>するすべて<xref:System.Windows.VisualState>のオブジェクトをに格納します。 サードパーティ製のコントロールでは、 <xref:System.Windows.TemplateVisualStateAttribute>を使用して状態を指定する必要があります。これにより、Expression Blend などのデザイナーツールで、コントロールテンプレートの作成用のコントロールの状態を公開できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールのコントロール コントラクトについては、「[コントロールのスタイルとテンプレート](control-styles-and-templates.md)」を参照してください。  
  
### <a name="properties-in-the-control-contract"></a>コントロール コントラクトのプロパティ  
 コントロールに視覚的な影響を与えるパブリック プロパティも、コントロール コントラクトに含まれています。 新しい<xref:System.Windows.Controls.ControlTemplate>を作成せずに、コントロールの外観を変更するには、これらのプロパティを設定します。 また、 [TemplateBinding](../advanced/templatebinding-markup-extension.md)マークアップ拡張機能を使用して、に含ま<xref:System.Windows.Controls.ControlTemplate>れる要素のプロパティを、 <xref:System.Windows.Controls.Button>で定義されているパブリックプロパティにバインドすることもできます。  
  
 次の例では、ボタンのコントロール コントラクトを示します。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 を作成<xref:System.Windows.Controls.ControlTemplate>するときは、多くの場合、既存<xref:System.Windows.Controls.ControlTemplate>のを使用して変更を加えるのが最も簡単です。 既存<xref:System.Windows.Controls.ControlTemplate>のを変更するには、次のいずれかの操作を行います。  
  
- Expression Blend などのデザイナーを使用します。デザイナーには、コントロール テンプレートを作成するためのグラフィカル ユーザー インターフェイスが用意されています。 詳細については、「[テンプレートをサポートするコントロールのスタイル処理](https://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。  
  
- 既定値<xref:System.Windows.Controls.ControlTemplate>を取得して編集します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属する既定のコントロール テンプレートについては、「[デフォルトの WPF テーマ](https://go.microsoft.com/fwlink/?LinkID=158252)」を参照してください。  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>コード例全体  
 このトピックで説明する完全<xref:System.Windows.Controls.Button>な<xref:System.Windows.Controls.ControlTemplate>例を次に示します。  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>関連項目

- [スタイルとテンプレート](styling-and-templating.md)
