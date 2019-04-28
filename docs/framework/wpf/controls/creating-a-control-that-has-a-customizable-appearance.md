---
title: 外観をカスタマイズできるコントロールの作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: a5d7c06502b66298d530d0180ffaf63862b9fc28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017792"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>外観をカスタマイズできるコントロールの作成
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 外観をカスタマイズできるコントロールを作成する機能を提供します。 たとえばの外観を変更することができます、<xref:System.Windows.Controls.CheckBox>どのような設定を超えるプロパティを新しいを作成して実行<xref:System.Windows.Controls.ControlTemplate>します。 次の図は、 <xref:System.Windows.Controls.CheckBox> 、既定値を使用する<xref:System.Windows.Controls.ControlTemplate>と<xref:System.Windows.Controls.CheckBox>カスタムを使用する<xref:System.Windows.Controls.ControlTemplate>します。  
  
 ![既定のコントロール テンプレートのチェック ボックスをオンします。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
既定のコントロール テンプレートを使用する CheckBox  
  
 ![カスタム コントロール テンプレートを使用してチェック ボックスをオンします。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
カスタム コントロール テンプレートを使用する CheckBox  
  
 コントロールを作成するときに、パーツと状態のモデルに従ってください場合、コントロールの外観はカスタマイズ可能になります。 Microsoft Expression Blend などのデザイナー ツールは、コントロールがこれらの種類のアプリケーションでカスタマイズ可能なするこのモデルに従うように、パーツと状態のモデルをサポートします。  このトピックでは、パーツと状態のモデルとに独自のコントロールを作成するときに実行する方法について説明します。 このトピックでは、カスタム コントロールの例を使用して`NumericUpDown`、このモデルの原理を説明するためにします。  `NumericUpDown`コントロール ユーザーを増やすまたは減らすコントロールのボタンをクリックして、数値の値を表示します。  次の図は、`NumericUpDown`このトピックで説明されているコントロール。  
  
 ![NumericUpDown カスタム コントロールです。](./media/ndp-numericupdown.png "NDP_NumericUPDown")  
カスタムの NumericUpDown コントロール  
  
 このトピックは、次のセクションで構成されています。  
  
- [必須コンポーネント](#prerequisites)  
  
- [パーツと状態モデル](#parts_and_states_model)  
  
- [ControlTemplate の視覚的な構造とコントロールの視覚的な動作の定義](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
- [コードで ControlTemplate のパーツを使用してください。](#using_parts_of_the_controltemplate_in_code)  
  
- [コントロール コントラクトを提供します。](#providing_the_control_contract)  
  
- [完全な例](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、新たに作成する方法がわかっている前提としています<xref:System.Windows.Controls.ControlTemplate>既存のコントロールはコントロール コントラクト上の要素が理解しで説明する概念を理解[によって既存のコントロールの外観のカスタマイズ。ControlTemplate の作成](customizing-the-appearance-of-an-existing-control.md)です。  
  
> [!NOTE]
>  外観をカスタマイズできるコントロールを作成するから継承するコントロールを作成する必要があります、<xref:System.Windows.Controls.Control>クラスまたはそのサブクラス以外のいずれかの<xref:System.Windows.Controls.UserControl>します。  継承するコントロール<xref:System.Windows.Controls.UserControl>をすばやく作成できるコントロールは使用されませんが、<xref:System.Windows.Controls.ControlTemplate>外観をカスタマイズすることはできません。  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>パーツと状態モデル  
 パーツと状態のモデルでは、視覚的な構造とコントロールの視覚的な動作を定義する方法を指定します。 パーツと状態のモデルを実行するには、次の操作を行う必要があります。  
  
- 視覚的な構造と視覚的な動作の定義、<xref:System.Windows.Controls.ControlTemplate>コントロール。  
  
- コントロールのロジックは、コントロール テンプレートのパーツと対話するとき、特定のベスト プラクティスに従ってください。  
  
- 何に含めるかを指定する、コントロール コントラクトの指定、<xref:System.Windows.Controls.ControlTemplate>します。  
  
 視覚的な構造とで視覚的な動作を定義するとき、 <xref:System.Windows.Controls.ControlTemplate> 、コントロールのアプリケーションの作成者を変更できます、視覚的な構造と、コントロールの視覚的な動作を作成する新しい<xref:System.Windows.Controls.ControlTemplate>コードを記述する代わりにします。   人の作成者がアプリケーションに指示するコントロール コントラクトを提供する必要があります<xref:System.Windows.FrameworkElement>では、オブジェクトと状態を定義する必要があります、<xref:System.Windows.Controls.ControlTemplate>します。 部分と対話する際のベスト プラクティスを従う必要があります、<xref:System.Windows.Controls.ControlTemplate>コントロールを適切に処理を完了していないように<xref:System.Windows.Controls.ControlTemplate>します。  アプリケーションの作成者が作成できる場合、これら 3 つの原則に従う、<xref:System.Windows.Controls.ControlTemplate>だけで、コントロールの同じくらい簡単にできるコントロールのと共に出荷[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  次のセクションでは、これらの推奨事項の詳細について説明します。  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>ControlTemplate の視覚的な構造とコントロールの視覚的な動作の定義  
 コントロールの視覚的な構造とで視覚的な動作を定義するパーツと状態のモデルを使用して、カスタム コントロールを作成するときにその<xref:System.Windows.Controls.ControlTemplate>の代わりにそのロジックにします。  コントロールの視覚的な構造は、合成の<xref:System.Windows.FrameworkElement>コントロールを構成するオブジェクト。  視覚的な動作は、特定の状態にあるときに、コントロールの表示方法です。   作成の詳細については、<xref:System.Windows.Controls.ControlTemplate>視覚的な構造とコントロールの視覚的な動作を指定しを参照してください[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)します。  
  
 例では、`NumericUpDown`コントロール、視覚的な構造には、2 つ<xref:System.Windows.Controls.Primitives.RepeatButton>コントロールと<xref:System.Windows.Controls.TextBlock>します。  コードでこれらのコントロールを追加する場合、`NumericUpDown`管理 - コンス トラクター、たとえば--でそれらのコントロールの位置は変更できません。  を、コード内のコントロールの視覚的な構造と視覚的な動作を定義するのではなくで定義する必要があります、<xref:System.Windows.Controls.ControlTemplate>します。  ボタンの位置をカスタマイズするアプリケーション開発者、および<xref:System.Windows.Controls.TextBlock>し、どのような動作が発生した指定と`Value`が負の値ため、<xref:System.Windows.Controls.ControlTemplate>置き換えることができます。  
  
 次の例の視覚的な構造を示しています、`NumericUpDown`のコントロールが、<xref:System.Windows.Controls.Primitives.RepeatButton>を増やす`Value`、<xref:System.Windows.Controls.Primitives.RepeatButton>を小さく`Value`と<xref:System.Windows.Controls.TextBlock>を表示する`Value`します。  
  
 [!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 視覚的な動作、`NumericUpDown`コントロールが負の場合、値が赤いフォントであります。  変更した場合、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>ときにコードで、`Value`は負の値、`NumericUpDown`赤い負の値を常に表示されます。 内のコントロールの視覚的な動作を指定する、<xref:System.Windows.Controls.ControlTemplate>を追加して<xref:System.Windows.VisualState>オブジェクトを<xref:System.Windows.Controls.ControlTemplate>します。  次の例は、<xref:System.Windows.VisualState>オブジェクトに対する、`Positive`と`Negative`状態。  `Positive` `Negative` (コントロールが常に 2 つのいずれか) は相互に排他的なので、この例では、<xref:System.Windows.VisualState>オブジェクト、1 つに<xref:System.Windows.VisualStateGroup>します。  コントロールに入るときに、 `Negative` 、状態、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>赤色に変わります。  コントロールが存在すると、 `Positive` 、状態、<xref:System.Windows.Controls.TextBlock.Foreground%2A>が戻された元の値。  定義する<xref:System.Windows.VisualState>内のオブジェクトを<xref:System.Windows.Controls.ControlTemplate>で詳しく説明は[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)します。  
  
> [!NOTE]
>  設定してください、<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>添付プロパティをルート<xref:System.Windows.FrameworkElement>の<xref:System.Windows.Controls.ControlTemplate>します。  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>コードで ControlTemplate のパーツを使用してください。  
 A<xref:System.Windows.Controls.ControlTemplate>作成者が省略<xref:System.Windows.FrameworkElement>または<xref:System.Windows.VisualState>オブジェクトの場合、意図的または誤ってが正常に機能するこれらのパーツをコントロールのロジックがあります。 パーツと状態のモデルでは、コントロールに対する回復力があることを指定します、<xref:System.Windows.Controls.ControlTemplate>は不足している<xref:System.Windows.FrameworkElement>または<xref:System.Windows.VisualState>オブジェクト。  コントロールがエラーをスローしません、例外またはレポート場合、 <xref:System.Windows.FrameworkElement>、 <xref:System.Windows.VisualState>、または<xref:System.Windows.VisualStateGroup>が表示されない、<xref:System.Windows.Controls.ControlTemplate>します。 このセクションと対話するための推奨される方法を説明します<xref:System.Windows.FrameworkElement>オブジェクトし、状態を管理します。  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>FrameworkElement オブジェクトの不足を予測します。  
 定義するときに<xref:System.Windows.FrameworkElement>内のオブジェクト、<xref:System.Windows.Controls.ControlTemplate>コントロールのロジックがその一部と対話する必要があります。  たとえば、`NumericUpDown`コントロールをサブスクライブするボタンの<xref:System.Windows.Controls.Primitives.ButtonBase.Click>増やしたり減らしたりするイベント`Value`設定と、<xref:System.Windows.Controls.TextBlock.Text%2A>のプロパティ、<xref:System.Windows.Controls.TextBlock>に`Value`します。 場合、カスタム<xref:System.Windows.Controls.ControlTemplate>省略、<xref:System.Windows.Controls.TextBlock>またはボタン、許容されるは、コントロールが、その機能の一部を失ったがコントロールには、エラーは発生しないことを確認しておく必要があることができます。 たとえば場合、<xref:System.Windows.Controls.ControlTemplate>を変更するボタンが含まれていない`Value`、`NumericUpDown`この機能が使用するアプリケーションが失う、<xref:System.Windows.Controls.ControlTemplate>は引き続き実行します。  
  
 次のプラクティスは、コントロールが不足しているに適切に応答することを確認<xref:System.Windows.FrameworkElement>オブジェクト。  
  
1. 設定、`x:Name`属性ごとに<xref:System.Windows.FrameworkElement>コード内で参照する必要があります。  
  
2. それぞれのプライベート プロパティを定義<xref:System.Windows.FrameworkElement>と対話する必要があります。  
  
3. サブスクライブし、コントロールで処理するイベントの登録を解除、<xref:System.Windows.FrameworkElement>プロパティがアクセサーを設定します。  
  
4. 設定、<xref:System.Windows.FrameworkElement>プロパティで定義されている手順 2、<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>メソッド。 これは、最も古いを<xref:System.Windows.FrameworkElement>で、<xref:System.Windows.Controls.ControlTemplate>はコントロールに使用できます。 使用して、`x:Name`の<xref:System.Windows.FrameworkElement>から取得する、<xref:System.Windows.Controls.ControlTemplate>します。  
  
5. いることを確認、<xref:System.Windows.FrameworkElement>ない`null`そのメンバーにアクセスする前にします。  場合は`null`エラーを報告しません。  
  
 次の例に示す方法、`NumericUpDown`コントロールとやり取り<xref:System.Windows.FrameworkElement>上記の推奨事項に従ってオブジェクト。  
  
 視覚的な構造を定義する例では、`NumericUpDown`を制御、 <xref:System.Windows.Controls.ControlTemplate>、<xref:System.Windows.Controls.Primitives.RepeatButton>を増加させる`Value`がその`x:Name`属性に設定`UpButton`します。  次の例と呼ばれるプロパティの宣言`UpButtonElement`を表す、<xref:System.Windows.Controls.Primitives.RepeatButton>で宣言されている、<xref:System.Windows.Controls.ControlTemplate>します。 `set`アクセサーを最初に、ボタンのアンサブスク ライブ<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント場合`UpDownElement`ない`null`、プロパティを設定およびにサブスクライブし、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。 プロパティ定義が、他のここでは、示されていませんがも<xref:System.Windows.Controls.Primitives.RepeatButton>という`DownButtonElement`します。  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 次の例は、<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>の`NumericUpDown`コントロール。  この例では、<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>を取得するメソッド、<xref:System.Windows.FrameworkElement>オブジェクトから、<xref:System.Windows.Controls.ControlTemplate>します。  あるをケースの例を防ぐことに注意してください<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>を検索、<xref:System.Windows.FrameworkElement>の予期される型が指定した名前にします。 またを持つ、指定した要素を無視することをお勧め`x:Name`が、型が正しくありません。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 コントロールの場合に実行し続けることを確認する前の例に示すようなプラクティスでは、<xref:System.Windows.Controls.ControlTemplate>がない、<xref:System.Windows.FrameworkElement>します。  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>VisualStateManager を使用して状態を管理するには  
 <xref:System.Windows.VisualStateManager>のコントロールの状態を追跡し、状態間の遷移に必要なロジックを実行します。 追加すると<xref:System.Windows.VisualState>オブジェクトを<xref:System.Windows.Controls.ControlTemplate>に追加する、<xref:System.Windows.VisualStateGroup>を追加し、<xref:System.Windows.VisualStateGroup>を<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>添付プロパティように、<xref:System.Windows.VisualStateManager>それにアクセスします。  
  
 次の例では、繰り返しの前の例を示す、<xref:System.Windows.VisualState>に対応するオブジェクト、`Positive`と`Negative`コントロールの状態。 <xref:System.Windows.Media.Animation.Storyboard>で、 `Negative` <xref:System.Windows.VisualState>オン、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>赤。   ときに、`NumericUpDown`コントロールが、`Negative`でストーリー ボードの状態、`Negative`状態が開始します。  次に、<xref:System.Windows.Media.Animation.Storyboard>で、`Negative`が停止状態のコントロールに戻ったとき、`Positive`状態。  `Positive` <xref:System.Windows.VisualState>を格納する必要はありません、<xref:System.Windows.Media.Animation.Storyboard>ためと、<xref:System.Windows.Media.Animation.Storyboard>の`Negative`停止すると、<xref:System.Windows.Controls.TextBlock.Foreground%2A>元の色を返します。  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 なお、 <xref:System.Windows.Controls.TextBlock> 、名前が付けが、<xref:System.Windows.Controls.TextBlock>のコントロール コントラクト内にない`NumericUpDown`コントロールのロジックを参照しないため、<xref:System.Windows.Controls.TextBlock>します。  参照される要素、<xref:System.Windows.Controls.ControlTemplate>名、コントロール コントラクトの一部であるためする必要はありませんが、新しい<xref:System.Windows.Controls.ControlTemplate>のコントロールがその要素を参照する必要はありません。  新しい人など<xref:System.Windows.Controls.ControlTemplate>の`NumericUpDown`することを示していないことで`Value`が変更することで、負の値、<xref:System.Windows.Controls.Control.Foreground%2A>します。  その場合、どちらのコードも<xref:System.Windows.Controls.ControlTemplate>参照、<xref:System.Windows.Controls.TextBlock>名前。  
  
 コントロールのロジックは、コントロールの状態を変更する責任を負います。 例を次に示します、`NumericUpDown`の制御呼び出し、<xref:System.Windows.VisualStateManager.GoToState%2A>メソッドに、`Positive`状態`Value`は 0 以上、`Negative`状態`Value`が 0 未満です。  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A>メソッドを起動し、ストーリー ボードを適切に停止するのに必要なロジックを実行します。 コントロールを呼び出すと<xref:System.Windows.VisualStateManager.GoToState%2A>の状態を変更する、<xref:System.Windows.VisualStateManager>は次の処理します。  
  
- 場合、<xref:System.Windows.VisualState>コントロールはしようとしているが、 <xref:System.Windows.Media.Animation.Storyboard>、ストーリー ボードが開始されます。 場合はその後、<xref:System.Windows.VisualState>からコントロールが送信されたことが、 <xref:System.Windows.Media.Animation.Storyboard>、ストーリー ボードが終了します。  
  
- コントロールが指定されている状態で既に場合<xref:System.Windows.VisualStateManager.GoToState%2A>は何も実行し、返します`true`します。  
  
- 指定されている状態が存在しない場合、<xref:System.Windows.Controls.ControlTemplate>の`control`、<xref:System.Windows.VisualStateManager.GoToState%2A>は何も実行し、返します`false`します。  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>VisualStateManager を操作するためのベスト プラクティス  
 コントロールの状態を維持するために、次を実行することをお勧めします。  
  
- プロパティを使用すると、その状態を追跡できます。  
  
- 状態間を移行するヘルパー メソッドを作成します。  
  
 `NumericUpDown`コントロール、`Value`内にあるかどうかを追跡するプロパティ、`Positive`または`Negative`状態。  `NumericUpDown`コントロールも定義、`Focused`と`UnFocused`状態、どのトラック、<xref:System.Windows.UIElement.IsFocused%2A>プロパティ。 コントロールのプロパティに対応する自然な状態を使用する場合は、状態を追跡するプライベート プロパティを定義できます。  
  
 すべての状態を更新する 1 つのメソッドの呼び出しを集中化、<xref:System.Windows.VisualStateManager>され、コードを管理しやすい状態に維持します。 次の例は、`NumericUpDown`コントロールのヘルパー メソッド、`UpdateStates`します。 ときに`Value`が 0 以上、<xref:System.Windows.Controls.Control>では、`Positive`状態。  ときに`Value`が 0 未満の値でのコントロールが、`Negative`状態。  ときに<xref:System.Windows.UIElement.IsFocused%2A>は`true`、コントロールが、`Focused`状態。 それ以外の場合、では、`Unfocused`状態。  コントロールが呼び出すことができます`UpdateStates`たびに、どのような状態の変更に関係なく、その状態を変更する必要があります。  
  
 [!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 状態の名前を渡す場合<xref:System.Windows.VisualStateManager.GoToState%2A>コントロールがその状態のとき<xref:System.Windows.VisualStateManager.GoToState%2A>コントロールの現在の状態を確認する必要はありませんので、何もしません。  たとえば場合、`Value`負の数を 1 つから別の負の値数のストーリー ボードへの変更、`Negative`状態は中断されず、ユーザーは、コントロールの変更は表示されません。  
  
 <xref:System.Windows.VisualStateManager>使用<xref:System.Windows.VisualStateGroup>オブジェクトを呼び出すときに終了するには、どの状態を判断する<xref:System.Windows.VisualStateManager.GoToState%2A>します。 コントロールごとに 1 つの状態は常に<xref:System.Windows.VisualStateGroup>で定義されているその<xref:System.Windows.Controls.ControlTemplate>し同じから別の状態になったときにのみ、状態のまま<xref:System.Windows.VisualStateGroup>します。 など、<xref:System.Windows.Controls.ControlTemplate>の`NumericUpDown`コントロールを定義、`Positive`と`Negative`<xref:System.Windows.VisualState>にあるオブジェクトの<xref:System.Windows.VisualStateGroup>と`Focused`と`Unfocused`<xref:System.Windows.VisualState>別のオブジェクト。 (確認できます、`Focused`と`Unfocused`<xref:System.Windows.VisualState>で定義されている、[完全な例](#complete_example)からコントロールになったときは、このトピックのセクション、`Positive`状態、`Negative`状態、またはその逆、コントロールのいずれかのまま、`Focused`または`Unfocused`状態。  
  
 コントロールの状態の変更可能性がありますが、3 つの一般的な場所があります。  
  
- ときに、<xref:System.Windows.Controls.ControlTemplate>に適用される、<xref:System.Windows.Controls.Control>します。  
  
- プロパティが変更されたとき。  
  
- イベントが発生します。  
  
 次の例の状態を更新、`NumericUpDown`このような場合のコントロール。  
  
 内のコントロールの状態を更新する必要があります、<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>メソッドが適切で、コントロールが表示されるように状態、<xref:System.Windows.Controls.ControlTemplate>が適用されます。 次の例では`UpdateStates`で<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>コントロールが、適切な状態であることを確認します。  たとえば、作成すること、`NumericUpDown`制御、および設定し、その<xref:System.Windows.Controls.Control.Foreground%2A>緑と`Value`-5 にします。  呼び出さない場合`UpdateStates`ときに、<xref:System.Windows.Controls.ControlTemplate>に適用される、`NumericUpDown`コントロール、コントロール内にない、`Negative`状態と、値が赤ではなく緑。  呼び出す必要があります`UpdateStates`にコントロールを配置する、`Negative`状態。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 多くの場合、プロパティが変更されたときのコントロールの状態を更新する必要があります。 次の例は、全体を示します`ValueChangedCallback`メソッド。 `ValueChangedCallback`時に呼び出される`Value`メソッドの呼び出しを変更します。`UpdateStates`場合`Value`に負の値、またはその逆正の値から変更されました。 呼び出しては`UpdateStates`とき`Value`変更が、その場合は、コントロールには状態変化しないために、正または負の値のままです。  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 また、イベントが発生したときに、状態を更新する必要があります。 例を次に示します、`NumericUpDown`呼び出し`UpdateStates`上、<xref:System.Windows.Controls.Control>処理するために、<xref:System.Windows.UIElement.GotFocus>イベント。  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager>コントロールの状態を管理するのに役立ちます。 使用して、<xref:System.Windows.VisualStateManager>コントロールが状態間で正しく移行することを確認します。  操作するためには、このセクションで説明されている推奨事項に従うかどうか、 <xref:System.Windows.VisualStateManager>、読みやすく、保守性の高いコントロールのコードが残ります。  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>コントロール コントラクトを提供します。  
 コントロール コントラクトを指定するように<xref:System.Windows.Controls.ControlTemplate>作成者、テンプレートに記述する内容がわかります。 コントロール コントラクトには、次の 3 つの要素があります。  
  
- コントロールのロジックが使用する視覚的要素。  
  
- コントロールの状態および各状態が所属するグループ。  
  
- コントロールに対して視覚的に作用するパブリック プロパティ。  
  
 ユーザーを作成する<xref:System.Windows.Controls.ControlTemplate>内容を確認する必要がある<xref:System.Windows.FrameworkElement>オブジェクトは、コントロールのロジックを使用して、各オブジェクトの種類し、どのような名前が。 A<xref:System.Windows.Controls.ControlTemplate>も作成者をコントロールで使用される各状態との名前を知っている必要があります<xref:System.Windows.VisualStateGroup>です。  
  
 返す、`NumericUpDown`例では、コントロールが必要ですが、<xref:System.Windows.Controls.ControlTemplate>次のものを<xref:System.Windows.FrameworkElement>オブジェクト。  
  
- A<xref:System.Windows.Controls.Primitives.RepeatButton>と呼ばれる`UpButton`します。  
  
- A<xref:System.Windows.Controls.Primitives.RepeatButton>と呼ばれる `DownButton.`  
  
 コントロールは、次の状態にできます。  
  
- の `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    - `Positive`  
  
    - `Negative`  
  
- の `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    - `Focused`  
  
    - `Unfocused`  
  
 内容を指定する<xref:System.Windows.FrameworkElement>オブジェクト、コントロールが必要ですが、使用する、 <xref:System.Windows.TemplatePartAttribute>、予測される要素の型と名前を指定します。  使用するコントロールの状態を指定する、<xref:System.Windows.TemplateVisualStateAttribute>と状態の名前を指定する<xref:System.Windows.VisualStateGroup>に属しています。  配置、<xref:System.Windows.TemplatePartAttribute>と<xref:System.Windows.TemplateVisualStateAttribute>コントロールのクラス定義でします。  
  
 コントロールの外観に影響を与えるパブリック プロパティは、コントロール コントラクトの一部をもできます。  
  
 次の例を指定します、<xref:System.Windows.FrameworkElement>オブジェクトと状態を`NumericUpDown`コントロール。  
  
 [!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>コード例全体  
 次の例は、全体<xref:System.Windows.Controls.ControlTemplate>の`NumericUpDown`コントロール。  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 次の例では、ロジックを`NumericUpDown`します。  
  
 [!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>関連項目

- [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)
- [コントロールのカスタマイズ](control-customization.md)
