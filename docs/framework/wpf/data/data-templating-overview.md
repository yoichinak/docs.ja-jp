---
title: データ テンプレートの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
ms.openlocfilehash: 9287656349f2a10619bfe76a36ee7855d3861cba
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376105"
---
# <a name="data-templating-overview"></a>データ テンプレートの概要
WPF のデータ テンプレート モデルは、データのプレゼンテーションを定義する優れた柔軟性を提供します。 WPF のコントロールには、データ プレゼンテーションのカスタマイズをサポートする組み込み機能があります。 このトピックでは最初に定義する方法を示します、<xref:System.Windows.DataTemplate>し、カスタム ロジックと階層データを表示するためのサポートに基づくテンプレートの選択など、他のデータ テンプレート機能を紹介します。  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、データ テンプレートの機能に関するものであり、データ バインディングの概念の紹介ではありません。 データ バインディングの基本概念については、「[データ バインディングの概要](data-binding-overview.md)」をご覧ください。  
  
 <xref:System.Windows.DataTemplate> データのプレゼンテーションについては、WPF のスタイルとテンプレート モデルによって提供される多くの機能の 1 つ。 使用する方法など、WPF のスタイルとテンプレート モデルの概要については、<xref:System.Windows.Style>コントロールのプロパティを設定するを参照してください。、[スタイルとテンプレート](../controls/styling-and-templating.md)トピック。  
  
 さらに、理解しておく必要が`Resources`などのオブジェクトを使用できるようは基本的に<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>再利用できるようにします。 リソースについて詳しくは、「[XAML リソース](../advanced/xaml-resources.md)」をご覧ください。  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>データ テンプレートの基礎  
  
 その理由を説明するために<xref:System.Windows.DataTemplate>ことが重要ですが、データ バインディングの例に説明します。 この例である、<xref:System.Windows.Controls.ListBox>の一覧にバインドされている`Task`オブジェクト。 各 `Task` オブジェクトには `TaskName` (string)、`Description` (string)、`Priority` (int)、および `TaskType` 型のプロパティがあり、これは値が `Home` と `Work` の `Enum` です。  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>DataTemplate がない場合  
 なし、 <xref:System.Windows.DataTemplate>、<xref:System.Windows.Controls.ListBox>現在次に示します。  
  
 ![データ テンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 何が起こっているかがないと、特定の指示、<xref:System.Windows.Controls.ListBox>既定の呼び出しによって`ToString`コレクション内のオブジェクトを表示しようとしています。 そのため場合、`Task`オブジェクトの上書き、`ToString`メソッド、<xref:System.Windows.Controls.ListBox>基になるコレクション内の各ソース オブジェクトの文字列表現を表示します。  
  
 たとえば、`Task` クラスが `ToString` メソッドを次のようにオーバーライドするものとします。`name` は `TaskName` プロパティのフィールドです。  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 次に、<xref:System.Windows.Controls.ListBox>次のようになります。  
  
 ![データ テンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 ただし、これは制限があり、柔軟性ではありません。 また、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データにバインドしている場合、`ToString` をオーバーライドすることはできません。  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>簡単な DataTemplate の定義  
 ソリューションは、定義する、<xref:System.Windows.DataTemplate>します。 1 つの簡単な方法を設定するのには、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>を<xref:System.Windows.DataTemplate>します。 指定した、<xref:System.Windows.DataTemplate>データ オブジェクトの視覚的な構造になります。 次<xref:System.Windows.DataTemplate>は非常に単純です。 ように 3 つの各項目が表示される指示しています<xref:System.Windows.Controls.TextBlock>内の要素を<xref:System.Windows.Controls.StackPanel>します。 各<xref:System.Windows.Controls.TextBlock>要素がのプロパティにバインドされている、`Task`クラス。  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 このトピックの例の基になるデータは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトのコレクションです。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] のデータにバインドしている場合は、基本的な概念は同じですが、構文がわずかに違います。 例ではなく`Path=TaskName`、設定は<xref:System.Windows.Data.Binding.XPath%2A>に`@TaskName`(場合`TaskName`の属性です、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ノード)。  
  
 これで、<xref:System.Windows.Controls.ListBox>次のようになります。  
  
 ![データ テンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>リソースとしての DataTemplate の作成  
 上記の例では、<xref:System.Windows.DataTemplate>インラインです。 再利用可能なオブジェクトになるように、リソース セクションで定義する方が一般的です。次に例を示します。  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 これで、次の例のように、`myTaskTemplate` をリソースとして使用できるようになります。  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 `myTaskTemplate`リソースを受け取るプロパティを持つ他のコントロールで使用することができますようになりました、<xref:System.Windows.DataTemplate>型。 上に示す<xref:System.Windows.Controls.ItemsControl>などのオブジェクト、<xref:System.Windows.Controls.ListBox>は、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>プロパティ。 <xref:System.Windows.Controls.ContentControl>オブジェクトの場合に、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティ。  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>DataType プロパティ  
 <xref:System.Windows.DataTemplate>クラスには、<xref:System.Windows.DataTemplate.DataType%2A>プロパティによく似ていますが、<xref:System.Windows.Style.TargetType%2A>のプロパティ、<xref:System.Windows.Style>クラス。 指定する代わりに、そのため、`x:Key`の<xref:System.Windows.DataTemplate>上記の例では、次を行うことができます。  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 これは、<xref:System.Windows.DataTemplate>すべてに自動的に適用される`Task`オブジェクト。 この場合、`x:Key` は暗黙的に設定されることに注意してください。 そのため、これを割り当てた場合<xref:System.Windows.DataTemplate>、`x:Key`値、暗黙的なをオーバーライドする`x:Key`、<xref:System.Windows.DataTemplate>自動的に適用されなくなります。  
  
 バインドしている場合、<xref:System.Windows.Controls.ContentControl>のコレクションに`Task`、オブジェクト、<xref:System.Windows.Controls.ContentControl>上記を使用しません<xref:System.Windows.DataTemplate>自動的にします。 これは、ためのバインディングを<xref:System.Windows.Controls.ContentControl>コレクション全体または個々 のオブジェクトにバインドするかどうかを区別するために詳細情報を必要があります。 場合、<xref:System.Windows.Controls.ContentControl>の選択の追跡は、<xref:System.Windows.Controls.ItemsControl>の種類を設定できます、<xref:System.Windows.Data.Binding.Path%2A>のプロパティ、<xref:System.Windows.Controls.ContentControl>へのバインド"`/`"を現在の項目に興味のあることを示します。 この例については、「[コレクションにバインドして選択に基づく情報を表示する](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)」をご覧ください。 それ以外の場合、指定する必要があります、<xref:System.Windows.DataTemplate>を設定して明示的に、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティ。  
  
 <xref:System.Windows.DataTemplate.DataType%2A>がある場合、プロパティが特に便利ですが、<xref:System.Windows.Data.CompositeCollection>さまざまな種類のデータ オブジェクト。 例については、「[CompositeCollection を実装する](how-to-implement-a-compositecollection.md)」をご覧ください。  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>DataTemplate へのその他の追加  
 現在、データでは必要な情報が表示されますが、間違いなく改善の余地があります。 追加することで、プレゼンテーションを改善しましょう、 <xref:System.Windows.Controls.Border>、 <xref:System.Windows.Controls.Grid>、およびいくつか<xref:System.Windows.Controls.TextBlock>表示されているデータを記述する要素。  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 次のスクリーン ショット、<xref:System.Windows.Controls.ListBox>で修正された<xref:System.Windows.DataTemplate>:  
  
 ![データ テンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 設定することが<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>に<xref:System.Windows.HorizontalAlignment.Stretch>上、<xref:System.Windows.Controls.ListBox>項目の幅がスペース全体を占めることを確認します。  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>プロパティに設定<xref:System.Windows.HorizontalAlignment.Stretch>、<xref:System.Windows.Controls.ListBox>今すぐ次に示します。  
  
 ![データ テンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>DataTrigger を使ってプロパティ値を適用する  
 現在のプレゼンテーションでは、`Task` が家のタスクか会社のタスクかわかりません。 `Task` オブジェクトには `TaskType` 型の `TaskType` プロパティがあり、これは値が `Home` と `Work` の列挙であることを思い出してください。  
  
 次の例では、<xref:System.Windows.DataTrigger>設定、<xref:System.Windows.Controls.Border.BorderBrush%2A>という名前の要素の`border`に`Yellow`場合、`TaskType`プロパティは`TaskType.Home`します。  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 これで、アプリケーションの表示は次のようになります。 家のタスクは黄色の境界線で、会社のタスクは水色の境界線で示されます。  
  
 ![データ テンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 この例では、<xref:System.Windows.DataTrigger>を使用して、<xref:System.Windows.Setter>プロパティ値を設定します。 トリガー クラスにもがある、<xref:System.Windows.TriggerBase.EnterActions%2A>と<xref:System.Windows.TriggerBase.ExitActions%2A>アニメーションなどのアクションのセットを開始するためのプロパティ。 さらに、<xref:System.Windows.MultiDataTrigger>クラスを使用すると、変更を適用する複数のデータ バインドされたプロパティ値に基づいています。  
  
 同じ効果を実現するために別の方法は、バインドする、<xref:System.Windows.Controls.Border.BorderBrush%2A>プロパティを`TaskType`プロパティと色を返す値コンバーターがに基づいて、`TaskType`値。 コンバーターを使って上の効果を作成するのは、パフォーマンスに関して若干効率的です。 さらに、独自のコンバーターを作成すると、独自のロジックを提供できるので柔軟性が向上します。 最終的に、どの手法を選ぶかは、シナリオと設定に依存します。 コンバーターを作成する方法については、次を参照してください。<xref:System.Windows.Data.IValueConverter>します。  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>DataTemplate に含まれるもの  

内でトリガーを配置しました。 前の例では、<xref:System.Windows.DataTemplate>を使用して、<xref:System.Windows.DataTemplate>します。<xref:System.Windows.DataTemplate.Triggers%2A> プロパティを使用する方法を示します。 <xref:System.Windows.Setter>トリガーの要素のプロパティの値を設定します (、<xref:System.Windows.Controls.Border>要素) 内にある、<xref:System.Windows.DataTemplate>します。 ただし場合、プロパティを`Setters`に不安が現在内にある要素のプロパティではない<xref:System.Windows.DataTemplate>を使用してプロパティを設定するより適切な場合があります、<xref:System.Windows.Style>については、<xref:System.Windows.Controls.ListBoxItem>クラス (場合、コントロールにバインドしているが、 <xref:System.Windows.Controls.ListBox>)。 する場合など、<xref:System.Windows.Trigger>をアニメーション化する、<xref:System.Windows.UIElement.Opacity%2A>値、項目の項目をマウスがポイントするとトリガーを定義する内で、<xref:System.Windows.Controls.ListBoxItem>スタイル。 例については、「[Introduction to Styling and Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)」(スタイルとテンプレートのサンプルの概要) をご覧ください。
  
 一般に、注意、 <xref:System.Windows.DataTemplate> 、生成された各に適用されている<xref:System.Windows.Controls.ListBoxItem>(が実際に適用される方法と場所の詳細については、次を参照してください。、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>ページです。)。 <xref:System.Windows.DataTemplate>プレゼンテーションとデータ オブジェクトの外観を気がします。 ほとんどの場合、プレゼンテーションでは、どのようなアイテムなどの他のすべての側面次のように選択されている方法、または<xref:System.Windows.Controls.ListBox>lays、項目のレイアウトの定義に属していない、<xref:System.Windows.DataTemplate>します。 例については、「[ItemsControl のスタイルとテンプレートの設定](#DataTemplating_ItemsControl)」セクションをご覧ください。  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>データ オブジェクトのプロパティに基づく DataTemplate の選択  
 「[DataType プロパティ](#Styling_DataType)」セクションでは、異なるデータ オブジェクトに対して異なるデータ テンプレートを定義できることを説明しました。 ある場合に特に便利です、<xref:System.Windows.Data.CompositeCollection>さまざまな種類のさまざまな種類の項目を含むコレクション。 [プロパティ値を適用する Datatrigger](#DataTrigger_to_Apply_Property_Values)セクションに示したよう、同じ種類のデータ オブジェクトのコレクションがある場合は、作成、<xref:System.Windows.DataTemplate>のプロパティの値に基づいて変更を適用するトリガーを使用して各データ オブジェクト。 ただし、トリガーではプロパティ値を適用したりアニメーションを開始することはできますが、データ オブジェクトの構造を再構築できるような柔軟性はありません。 一部のシナリオには、別に作成する必要があります<xref:System.Windows.DataTemplate>データは同じであるオブジェクトに入力はさまざまなプロパティがあります。  
  
 たとえば、`Task` オブジェクトの `Priority` の値が `1` のときは、自分用の警告としてまったく異なる外観にしたいような場合です。 この場合は、作成、<xref:System.Windows.DataTemplate>高優先度のディスプレイの`Task`オブジェクト。 次のコードを追加してみましょう<xref:System.Windows.DataTemplate>リソース セクションに。  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 この例では使用に注意してください、<xref:System.Windows.DataTemplate>します。<xref:System.Windows.FrameworkTemplate.Resources%2A> プロパティを使用する方法を示します。 内の要素が共有セクションで定義されているリソース、<xref:System.Windows.DataTemplate>します。  
  
 選択するためのロジックを提供する<xref:System.Windows.DataTemplate>に基づいて使用するのには、`Priority`値のサブクラスを作成、データ オブジェクトの<xref:System.Windows.Controls.DataTemplateSelector>をオーバーライドし、<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>メソッド。 次の例では、<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>メソッドの値に基づいて適切なテンプレートを返すロジックを提供する、`Priority`プロパティ。 返すテンプレートは、エンベロープのリソースで見つかった<xref:System.Windows.Window>要素。  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 その後、リソースとして `TaskListDataTemplateSelector` を宣言できます。  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 テンプレート セレクター リソースを使用するには、それを割り当てる、<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>します。 <xref:System.Windows.Controls.ListBox>呼び出し、<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>のメソッド、`TaskListDataTemplateSelector`の基になるコレクション内の項目ごとにします。 呼び出しでは、項目パラメーターとしてデータ オブジェクトを渡します。 <xref:System.Windows.DataTemplate>によって返される、メソッドはそのデータ オブジェクトに適用されます。  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 インプレースでのテンプレート セレクター、<xref:System.Windows.Controls.ListBox>次のように表示されます。  
  
 ![データ テンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

これがこの例の結論です。 完全なサンプルについては、「[Introduction to Data Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro)」(データ テンプレート サンプルの概要) をご覧ください。

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>ItemsControl のスタイルとテンプレートの設定  
 場合でも、<xref:System.Windows.Controls.ItemsControl>使用できる唯一のコントロール型ではない、<xref:System.Windows.DataTemplate>にバインドする非常に一般的なシナリオが使用すると、<xref:System.Windows.Controls.ItemsControl>コレクションにします。 [DataTemplate に](#what_belongs_in_datatemplate)を説明したセクションの定義、<xref:System.Windows.DataTemplate>データのプレゼンテーションを考慮する必要がありますのみです。 ない場合の使用に適したを知るために、<xref:System.Windows.DataTemplate>によって提供されるさまざまなスタイルとテンプレートのプロパティを理解することが重要、<xref:System.Windows.Controls.ItemsControl>します。 次の例は、これらの各プロパティの機能がわかるように設計されています。 <xref:System.Windows.Controls.ItemsControl>この例では、同じバインドされている`Tasks`前の例のようにコレクション。 わかりやすいように、この例のスタイルとテンプレートはすべてインラインで宣言されています。  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 次に示すのは、この例がレンダリングされたときのスクリーンショットです。  
  
 ![ItemsControl の例のスクリーンショット](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 注意して使用する代わりに、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、使用することができます、<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>します。 例については、前のセクションをご覧ください。 使用する代わりに、同様に、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>を使用するオプションがある、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>します。  
  
 2 つの他のスタイル関連プロパティ、<xref:System.Windows.Controls.ItemsControl>ここでは表示されていない<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>と<xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>します。  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>階層データのサポート  
 これまでは、1 つのコレクションにバインドして表示する方法のみを説明してきました。 場合によっては、コレクションに他のコレクションが含まれることがあります。 <xref:System.Windows.HierarchicalDataTemplate>クラスがで使用するように設計<xref:System.Windows.Controls.HeaderedItemsControl>このようなデータを表示する型。 次の例で、`ListLeagueList` は `League` オブジェクトのリストです。 各 `League` オブジェクトには、`Name` と、`Division` オブジェクトのコレクションがあります。 各 `Division` には、`Name` と `Team` オブジェクトのコレクションがあり、各 `Team` オブジェクトには `Name` があります。  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 例を使用して示します<xref:System.Windows.HierarchicalDataTemplate>、他のリストを含むリストのデータを簡単に表示できます。 次に示すのは、この例のスクリーンショットです。  
  
 ![HierarchicalDataTemplate サンプルのスクリーンショット](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>関連項目
- [データ バインディング](../advanced/optimizing-performance-data-binding.md)
- [DataTemplate によって生成された要素を検索する](how-to-find-datatemplate-generated-elements.md)
- [スタイルとテンプレート](../controls/styling-and-templating.md)
- [データ バインディングの概要](data-binding-overview.md)
- [GridView の列ヘッダー スタイルおよびテンプレートの概要](../controls/gridview-column-header-styles-and-templates-overview.md)
