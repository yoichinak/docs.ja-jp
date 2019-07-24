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
ms.openlocfilehash: 556ce7b42f13d7c5ba7fba36b09277cda9bcae5d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400664"
---
# <a name="data-templating-overview"></a>データ テンプレートの概要
WPF のデータ テンプレート モデルは、データのプレゼンテーションを定義する優れた柔軟性を提供します。 WPF のコントロールには、データ プレゼンテーションのカスタマイズをサポートする組み込み機能があります。 このトピックでは、まずを<xref:System.Windows.DataTemplate>定義し、カスタムロジックに基づいてテンプレートを選択し、階層データの表示をサポートするなど、その他のデータテンプレート機能について説明します。  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、データ テンプレートの機能に関するものであり、データ バインディングの概念の紹介ではありません。 データ バインディングの基本概念については、「[データ バインディングの概要](data-binding-overview.md)」をご覧ください。  
  
 <xref:System.Windows.DataTemplate>は、データの表示に関するものであり、WPF のスタイルとテンプレートモデルによって提供される多くの機能の1つです。 を<xref:System.Windows.Style>使用してコントロールのプロパティを設定する方法など、WPF のスタイルとテンプレートモデルの概要については、「[スタイルとテンプレート](../controls/styling-and-templating.md)」のトピックを参照してください。  
  
 また、基本的には、 `Resources` <xref:System.Windows.Style>や<xref:System.Windows.DataTemplate>などのオブジェクトを再利用できるようにすることを理解しておくことが重要です。 リソースについて詳しくは、「[XAML リソース](../advanced/xaml-resources.md)」をご覧ください。  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>データ テンプレートの基礎  
  
 が重要な<xref:System.Windows.DataTemplate>理由を示すために、データバインディングの例を見てみましょう。 この例では、オブジェクトの<xref:System.Windows.Controls.ListBox> `Task`リストにバインドされたがあります。 各 `Task` オブジェクトには `TaskName` (string)、`Description` (string)、`Priority` (int)、および `TaskType` 型のプロパティがあり、これは値が `Home` と `Work` の `Enum` です。  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>DataTemplate がない場合  
 を<xref:System.Windows.DataTemplate>使用<xref:System.Windows.Controls.ListBox>しない場合、現在は次のようになります。  
  
 ![データテンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 具体的には、特定の命令がなければ、 <xref:System.Windows.Controls.ListBox>はコレクション内`ToString`のオブジェクトを表示しようとしたときに既定でを呼び出します。 したがって、オブジェクト`Task`が`ToString`メソッドをオーバーライドする場合、 <xref:System.Windows.Controls.ListBox>は、基になるコレクション内の各ソースオブジェクトの文字列形式を表示します。  
  
 たとえば、`Task` クラスが `ToString` メソッドを次のようにオーバーライドするものとします。`name` は `TaskName` プロパティのフィールドです。  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 その後<xref:System.Windows.Controls.ListBox> 、は次のようになります。  
  
 ![データテンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 ただし、これは制限があり、柔軟性ではありません。 また、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データにバインドしている場合、`ToString` をオーバーライドすることはできません。  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>簡単な DataTemplate の定義  
 これを解決するには<xref:System.Windows.DataTemplate>、を定義します。 これを行う1つの方法は、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>のプロパティをに設定することです。 に指定した内容<xref:System.Windows.DataTemplate>は、データオブジェクトの視覚的な構造になります。 以下<xref:System.Windows.DataTemplate>は非常に単純です。 各項目が<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel>内に3つの要素として表示されるように指示しています。 各<xref:System.Windows.Controls.TextBlock>要素は、 `Task`クラスのプロパティにバインドされます。  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 このトピックの例の基になるデータは、CLR オブジェクトのコレクションです。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] のデータにバインドしている場合は、基本的な概念は同じですが、構文がわずかに違います。 たとえば、を使用するの`Path=TaskName`ではなく、 <xref:System.Windows.Data.Binding.XPath%2A>を`@TaskName`に設定`TaskName`します (が[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ノードの属性の場合)。  
  
 <xref:System.Windows.Controls.ListBox>次のようになります。  
  
 ![データテンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>リソースとしての DataTemplate の作成  
 上の例では<xref:System.Windows.DataTemplate> 、インラインを定義しています。 再利用可能なオブジェクトになるように、リソース セクションで定義する方が一般的です。次に例を示します。  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 これで、次の例のように、`myTaskTemplate` をリソースとして使用できるようになります。  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 はリソースなので、型を<xref:System.Windows.DataTemplate>受け取るプロパティを持つ他のコントロールで使用できるようになりました。 `myTaskTemplate` 上に示すように<xref:System.Windows.Controls.ItemsControl> 、などのオブジェクト<xref:System.Windows.Controls.ListBox>については、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>プロパティが使用されます。 オブジェクト<xref:System.Windows.Controls.ContentControl>の場合<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>は、プロパティです。  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>DataType プロパティ  
 クラスには、 <xref:System.Windows.DataTemplate.DataType%2A> クラス<xref:System.Windows.Style>のプロパティと非常によく似たプロパティがあります。 <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.DataTemplate> したがって、上の例`x:Key`のに<xref:System.Windows.DataTemplate>を指定する代わりに、次の操作を行うことができます。  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 これ<xref:System.Windows.DataTemplate>は、すべて`Task`のオブジェクトに自動的に適用されます。 この場合、`x:Key` は暗黙的に設定されることに注意してください。 <xref:System.Windows.DataTemplate>したがって、この`x:Key`値を割り当てた場合、暗黙的`x:Key`なをオーバーライドすること<xref:System.Windows.DataTemplate>になり、は自動的には適用されません。  
  
 を<xref:System.Windows.Controls.ContentControl>オブジェクト`Task` のコレクション<xref:System.Windows.DataTemplate>にバインドする場合、は上記のを自動的には使用しません。 <xref:System.Windows.Controls.ContentControl> これは、のバインディング<xref:System.Windows.Controls.ContentControl>によって、コレクション全体と個々のオブジェクトのどちらにバインドするかを区別するために、より多くの情報が必要になるためです。 が<xref:System.Windows.Controls.ContentControl> `/` <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Data.Binding.Path%2A>型の選択を追跡している場合は、バインディングのプロパティを "" に設定して、現在の項目に関心があることを示すことができます。 <xref:System.Windows.Controls.ItemsControl> この例については、「[コレクションにバインドして選択に基づく情報を表示する](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)」をご覧ください。 それ以外の場合は、 <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティを設定して明示的にを指定する必要があります。  
  
 プロパティは、 <xref:System.Windows.Data.CompositeCollection>さまざまな種類のデータオブジェクトがある場合に特に便利です。 <xref:System.Windows.DataTemplate.DataType%2A> 例については、「[CompositeCollection を実装する](how-to-implement-a-compositecollection.md)」をご覧ください。  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>DataTemplate へのその他の追加  
 現在、データでは必要な情報が表示されますが、間違いなく改善の余地があります。 表示されるデータを記述する<xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Grid>、、、および<xref:System.Windows.Controls.TextBlock>要素を追加して、プレゼンテーションを改良してみましょう。  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 次のスクリーンショットは<xref:System.Windows.Controls.ListBox> 、このが<xref:System.Windows.DataTemplate>変更されたを示しています。  
  
 ![データテンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 で<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch>をに設定して、項目の幅が領域全体を占めるようにすることができます。 <xref:System.Windows.Controls.ListBox>  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 プロパティをに設定する<xref:System.Windows.HorizontalAlignment.Stretch>と、 <xref:System.Windows.Controls.ListBox>は次のようになります。 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>  
  
 ![データテンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>DataTrigger を使ってプロパティ値を適用する  
 現在のプレゼンテーションでは、`Task` が家のタスクか会社のタスクかわかりません。 `Task` オブジェクトには `TaskType` 型の `TaskType` プロパティがあり、これは値が `Home` と `Work` の列挙であることを思い出してください。  
  
 次の例では、 <xref:System.Windows.DataTrigger> `TaskType`プロパティが<xref:System.Windows.Controls.Border.BorderBrush%2A> `border` `Yellow` の場合、はという名前の要素のをに`TaskType.Home`設定します。  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 これで、アプリケーションの表示は次のようになります。 家のタスクは黄色の境界線で、会社のタスクは水色の境界線で示されます。  
  
 ![データテンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 この例では<xref:System.Windows.DataTrigger> 、を<xref:System.Windows.Setter>使用してプロパティ値を設定します。 トリガークラスには、アニメーション<xref:System.Windows.TriggerBase.EnterActions%2A>など<xref:System.Windows.TriggerBase.ExitActions%2A>の一連のアクションを開始できるプロパティとプロパティもあります。 また、複数のデータバインドプロパティ<xref:System.Windows.MultiDataTrigger>値に基づいて変更を適用できるクラスもあります。  
  
 同じ効果を実現する別の方法として、 <xref:System.Windows.Controls.Border.BorderBrush%2A>プロパティ`TaskType`をプロパティにバインドし、値コンバーターを使用して`TaskType`値に基づいて色を返すこともできます。 コンバーターを使って上の効果を作成するのは、パフォーマンスに関して若干効率的です。 さらに、独自のコンバーターを作成すると、独自のロジックを提供できるので柔軟性が向上します。 最終的に、どの手法を選ぶかは、シナリオと設定に依存します。 コンバーターを記述する方法の詳細について<xref:System.Windows.Data.IValueConverter>は、「」を参照してください。  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>DataTemplate に含まれるもの  

前の例では、を<xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate>使用して、トリガーを内に配置しています。<xref:System.Windows.DataTemplate.Triggers%2A> プロパティを使用する方法を示します。 トリガー <xref:System.Windows.Setter>のは、内にある要素<xref:System.Windows.Controls.Border> (要素<xref:System.Windows.DataTemplate>) のプロパティの値を設定します。 ただし、関心の`Setters`あるプロパティが、現在<xref:System.Windows.DataTemplate>の内にある要素のプロパティではない場合は、 <xref:System.Windows.Controls.ListBoxItem>クラス用のを<xref:System.Windows.Style>使用してプロパティを設定する方が適切な場合があります (バインドしているコントロールは<xref:System.Windows.Controls.ListBox>です)。 たとえば、マウスが項目をポイント<xref:System.Windows.Trigger>したとき<xref:System.Windows.UIElement.Opacity%2A>にで項目の値をアニメーション化する場合は、 <xref:System.Windows.Controls.ListBoxItem>スタイル内でトリガーを定義します。 例については、「[Introduction to Styling and Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)」(スタイルとテンプレートのサンプルの概要) をご覧ください。
  
 一般に、は、生成<xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ListBoxItem>されたそれぞれに適用されることに注意してください ( <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>実際に適用される方法と場所の詳細については、「」を参照してください)。 で<xref:System.Windows.DataTemplate>は、データオブジェクトのプレゼンテーションと外観のみが考慮されます。 ほとんどの場合、項目が選択されたときの外観や項目の<xref:System.Windows.Controls.ListBox>レイアウト方法など、プレゼンテーションの他のすべての側面は、 <xref:System.Windows.DataTemplate>の定義に属していません。 例については、「[ItemsControl のスタイルとテンプレートの設定](#DataTemplating_ItemsControl)」セクションをご覧ください。  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>データ オブジェクトのプロパティに基づく DataTemplate の選択  
 「[DataType プロパティ](#Styling_DataType)」セクションでは、異なるデータ オブジェクトに対して異なるデータ テンプレートを定義できることを説明しました。 これは、 <xref:System.Windows.Data.CompositeCollection>さまざまな型またはコレクションに異なる型の項目が含まれている場合に特に便利です。 [ [DataTriggers を使用してプロパティ値を適用する](#DataTrigger_to_Apply_Property_Values)] セクションでは、同じ型のデータオブジェクトのコレクションがある場合に、を<xref:System.Windows.DataTemplate>作成し、トリガーを使用して各データオブジェクトのプロパティ値に基づいて変更を適用できることを示しています。 ただし、トリガーではプロパティ値を適用したりアニメーションを開始することはできますが、データ オブジェクトの構造を再構築できるような柔軟性はありません。 場合によっては、同じ種類の<xref:System.Windows.DataTemplate>データオブジェクトに対して異なるを作成する必要がありますが、プロパティは異なります。  
  
 たとえば、`Task` オブジェクトの `Priority` の値が `1` のときは、自分用の警告としてまったく異なる外観にしたいような場合です。 その場合は、優先度<xref:System.Windows.DataTemplate> `Task`の高いオブジェクトを表示するためのを作成します。 Resources セクションに次<xref:System.Windows.DataTemplate>の項目を追加してみましょう。  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 この例では、 <xref:System.Windows.DataTemplate>を使用しています。<xref:System.Windows.FrameworkTemplate.Resources%2A> プロパティを使用する方法を示します。 このセクションで定義されているリソースは、 <xref:System.Windows.DataTemplate>内の要素によって共有されます。  
  
 データオブジェクトの`Priority`値に基づい<xref:System.Windows.DataTemplate>て使用するロジックを指定するには、の<xref:System.Windows.Controls.DataTemplateSelector> <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>サブクラスを作成し、メソッドをオーバーライドします。 次の例では、 <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>メソッドは、 `Priority`プロパティの値に基づいて適切なテンプレートを返すロジックを提供します。 返されるテンプレートは、エンベロープ<xref:System.Windows.Window>要素のリソースにあります。  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 その後、リソースとして `TaskListDataTemplateSelector` を宣言できます。  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 テンプレートセレクターリソースを使用するには<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> <xref:System.Windows.Controls.ListBox>、のプロパティに割り当てます。 は<xref:System.Windows.Controls.ListBox> 、基<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>になるコレクション`TaskListDataTemplateSelector`内の各項目について、のメソッドを呼び出します。 呼び出しでは、項目パラメーターとしてデータ オブジェクトを渡します。 その<xref:System.Windows.DataTemplate>後、メソッドによって返されたが、そのデータオブジェクトに適用されます。  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 テンプレートセレクターを配置すると、は<xref:System.Windows.Controls.ListBox>次のようになります。  
  
 ![データテンプレートのサンプルのスクリーンショット](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

これがこの例の結論です。 完全なサンプルについては、「[Introduction to Data Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro)」(データ テンプレート サンプルの概要) をご覧ください。

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>ItemsControl のスタイルとテンプレートの設定  
 は、 <xref:System.Windows.DataTemplate>と共に使用できる唯一のコントロール型で<xref:System.Windows.Controls.ItemsControl> はありませんが、をコレクションにバインドするのは非常に一般的なシナリオです。<xref:System.Windows.Controls.ItemsControl> 「 [System.windows.datatemplate> に属し](#what_belongs_in_datatemplate)ているもの」セクションでは、の<xref:System.Windows.DataTemplate>定義は、データの表示のみを考慮する必要があることを説明しました。 を使用<xref:System.Windows.DataTemplate>するのが適切でない場合には、 <xref:System.Windows.Controls.ItemsControl>によって提供されるさまざまなスタイルとテンプレートプロパティを理解することが重要です。 次の例は、これらの各プロパティの機能がわかるように設計されています。 この<xref:System.Windows.Controls.ItemsControl>例のは、前の例と`Tasks`同じコレクションにバインドされています。 わかりやすいように、この例のスタイルとテンプレートはすべてインラインで宣言されています。  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 次に示すのは、この例がレンダリングされたときのスクリーンショットです。  
  
 ![ItemsControl の例のスクリーンショット](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 を使用する代わり<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>に、を<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>使用することもできます。 例については、前のセクションをご覧ください。 同様に、を使用する<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>代わりに、を<xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>使用するオプションもあります。  
  
 ここでは示されていない<xref:System.Windows.Controls.ItemsControl>の2つのスタイル関連<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>の<xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>プロパティは、とです。  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>階層データのサポート  
 これまでは、1 つのコレクションにバインドして表示する方法のみを説明してきました。 場合によっては、コレクションに他のコレクションが含まれることがあります。 クラス<xref:System.Windows.HierarchicalDataTemplate>は、そのようなデータを<xref:System.Windows.Controls.HeaderedItemsControl>表示するために型と共に使用するように設計されています。 次の例で、`ListLeagueList` は `League` オブジェクトのリストです。 各 `League` オブジェクトには、`Name` と、`Division` オブジェクトのコレクションがあります。 各 `Division` には、`Name` と `Team` オブジェクトのコレクションがあり、各 `Team` オブジェクトには `Name` があります。  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 この例では、を使用<xref:System.Windows.HierarchicalDataTemplate>して、他のリストを含むリストデータを簡単に表示できることを示しています。 次に示すのは、この例のスクリーンショットです。  
  
 ![HierarchicalDataTemplate サンプルスクリーンショット](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>関連項目

- [データ バインディング](../advanced/optimizing-performance-data-binding.md)
- [DataTemplate によって生成された要素を検索する](how-to-find-datatemplate-generated-elements.md)
- [スタイルとテンプレート](../controls/styling-and-templating.md)
- [データ バインディングの概要](data-binding-overview.md)
- [GridView の列ヘッダー スタイルおよびテンプレートの概要](../controls/gridview-column-header-styles-and-templates-overview.md)
