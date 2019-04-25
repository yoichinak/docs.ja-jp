---
title: WPF のコンテンツ モデル
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: 4f866e0366a7781c287b3ebae7b668c2b296a5cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134609"
---
# <a name="wpf-content-model"></a>WPF のコンテンツ モデル
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、多くのコントロールやコントロールのような型を提供する表示プラットフォームで、その主な目的は、異なる種類のコンテンツを表示することです。 使用するコントロールまたは派生元のコントロールを判断するには、特定のコントロールが最適に表示できるオブジェクトの種類を理解する必要があります。  
  
 このトピックは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールとコントロールのような型に関するコンテンツ モデルのまとめです。 コンテンツ モデルは、どのようなコンテンツをコントロールで使用できるかについて説明します。 このトピックは、各コンテンツ モデルのコンテンツのプロパティもリストします。 コンテンツのプロパティは、オブジェクトのコンテンツの格納に使用されるプロパティです。  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>任意のコンテンツを含むクラス  
 一部のコントロールは、文字列などの任意の型のオブジェクトを含めることができます、<xref:System.DateTime>オブジェクト、または<xref:System.Windows.UIElement>追加項目のコンテナーであります。 たとえば、<xref:System.Windows.Controls.Button>イメージと任意のテキストに含めることができます、<xref:System.Windows.Controls.CheckBox>の値を含めることができます<xref:System.DateTime.Now%2A?displayProperty=nameWithType>します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、任意のコンテンツを含めることができる 4 つのクラスがあります。 次の表から継承するクラス、<xref:System.Windows.Controls.Control>します。  
  
|任意のコンテンツを含むクラス|Content|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|1 つの任意のオブジェクト。|  
|<xref:System.Windows.Controls.HeaderedContentControl>|ヘッダーと 1 つの項目。両方とも任意のオブジェクトです。|  
|<xref:System.Windows.Controls.ItemsControl>|任意のオブジェクトのコレクション。|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|ヘッダーと項目のコレクション。すべて任意のオブジェクトです。|  
  
 これらのクラスから継承するコントロールは、同じ種類のコンテンツを格納でき、同じ方法でコンテンツを処理することができます。 次の図は、イメージを含む各コンテンツ モデルといくつかのテキストから 1 つのコントロールを示しています。  
  
 ![各コンテンツ モデルから 1 つ、4 つの異なるコントロールを示すスクリーン ショット。](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>任意の 1 つのオブジェクトを格納しているコントロール  
 <xref:System.Windows.Controls.ContentControl>クラスには、1 つ任意のコンテンツにはが含まれています。 コンテンツのプロパティは<xref:System.Windows.Controls.ContentControl.Content%2A>します。 次のコントロールから継承<xref:System.Windows.Controls.ContentControl>とそのコンテンツ モデルを使用します。  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 次の図は 4 つのボタンが<xref:System.Windows.Controls.ContentControl.Content%2A>、文字列に設定されている、<xref:System.DateTime>オブジェクト、<xref:System.Windows.Shapes.Rectangle>と<xref:System.Windows.Controls.Panel>を格納している、<xref:System.Windows.Shapes.Ellipse>と<xref:System.Windows.Controls.TextBlock>:  
  
 ![さまざまなコンテンツ タイプの 4 つのボタンを示すスクリーン ショット。](./media/wpf-content-model/control-content-model-buttons.png)  
  
 設定する方法の例については、<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティを参照してください<xref:System.Windows.Controls.ContentControl>します。  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>ヘッダーと任意の 1 つのオブジェクトを格納しているコントロール  
 <xref:System.Windows.Controls.HeaderedContentControl>クラスから継承<xref:System.Windows.Controls.ContentControl>ヘッダーとコンテンツが表示されます。 コンテンツのプロパティを継承<xref:System.Windows.Controls.ContentControl.Content%2A>から<xref:System.Windows.Controls.ContentControl>を定義し、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>型のプロパティを<xref:System.Object>。 したがって、任意のオブジェクトはどちらもします。  
  
 次のコントロールから継承<xref:System.Windows.Controls.HeaderedContentControl>とそのコンテンツ モデルを使用します。  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 次の図は 2 つ<xref:System.Windows.Controls.TabItem>オブジェクト。 最初の<xref:System.Windows.Controls.TabItem>が<xref:System.Windows.UIElement>としてオブジェクト、 <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> 、<xref:System.Windows.Controls.ContentControl.Content%2A>します。 <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>に設定されている、<xref:System.Windows.Controls.StackPanel>を格納している、<xref:System.Windows.Shapes.Ellipse>と<xref:System.Windows.Controls.TextBlock>します。 <xref:System.Windows.Controls.ContentControl.Content%2A>に設定されている、<xref:System.Windows.Controls.StackPanel>を格納している、<xref:System.Windows.Controls.TextBlock>と<xref:System.Windows.Controls.Label>します。 2 番目の<xref:System.Windows.Controls.TabItem>に文字列を持つ、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>と<xref:System.Windows.Controls.TextBlock>で、<xref:System.Windows.Controls.ContentControl.Content%2A>します。  
  
 ![ヘッダー プロパティにさまざまな種類を使用する TabControl します。](./media/wpf-content-model/control-content-model-tab.png)  
  
 作成する方法の例については<xref:System.Windows.Controls.TabItem>、オブジェクトを参照してください<xref:System.Windows.Controls.HeaderedContentControl>します。  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>任意のオブジェクトのコレクションを格納しているコントロール  
 <xref:System.Windows.Controls.ItemsControl>クラスから継承<xref:System.Windows.Controls.Control>文字列、オブジェクト、またはその他の要素など、複数の項目を含めることができます。 そのコンテンツのプロパティは<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>と<xref:System.Windows.Controls.ItemsControl.Items%2A>します。 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 設定に通常使用、<xref:System.Windows.Controls.ItemsControl>データ コレクションを使用します。 設定するコレクションを使用しないかどうか、<xref:System.Windows.Controls.ItemsControl>を使用して項目を追加することができます、<xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティ。  
  
 次のコントロールから継承<xref:System.Windows.Controls.ItemsControl>とそのコンテンツ モデルを使用します。  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 次の図は、<xref:System.Windows.Controls.ListBox>この種類のアイテムを格納しています。  
  
-   文字列。  
  
-   <xref:System.DateTime> オブジェクト。  
  
-   <xref:System.Windows.UIElement>。  
  
-   A<xref:System.Windows.Controls.Panel>を格納している、<xref:System.Windows.Shapes.Ellipse>と<xref:System.Windows.Controls.TextBlock>します。  
  
 ![次の 4 つの種類のコンテンツがリスト ボックスを示すスクリーン ショット。](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>ヘッダーと任意のオブジェクトのコレクションを含むコントロール  
 <xref:System.Windows.Controls.HeaderedItemsControl>クラスから継承<xref:System.Windows.Controls.ItemsControl>文字列、オブジェクト、または他の要素やヘッダーなど、複数の項目を含めることができます。 継承、<xref:System.Windows.Controls.ItemsControl>コンテンツのプロパティを<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>と<xref:System.Windows.Controls.ItemsControl.Items%2A>、し、定義、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>ことができる任意のオブジェクト プロパティです。  
  
 次のコントロールから継承<xref:System.Windows.Controls.HeaderedItemsControl>とそのコンテンツ モデルを使用します。  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>UIElement オブジェクトのコレクションを含むクラス  
 <xref:System.Windows.Controls.Panel>クラスを配置し、子を整列<xref:System.Windows.UIElement>オブジェクト。 コンテンツのプロパティは<xref:System.Windows.Controls.Panel.Children%2A>します。  
  
 次のクラスから継承、<xref:System.Windows.Controls.Panel>クラスし、そのコンテンツ モデルを使用します。  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 詳細については、「[Panels Overview](panels-overview.md)」を参照してください。  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>UIElement の外観に影響を与えるクラス  
 <xref:System.Windows.Controls.Decorator>クラスまたは 1 つの子の周囲に視覚効果を適用する<xref:System.Windows.UIElement>します。 コンテンツのプロパティは<xref:System.Windows.Controls.Decorator.Child%2A>します。 次のクラスから継承<xref:System.Windows.Controls.Decorator>とそのコンテンツ モデルを使用します。  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 次の図は、<xref:System.Windows.Controls.TextBox>を持つ (で装飾が)、<xref:System.Windows.Controls.Border>周囲します。  
  
 ![境界線が黒の TextBox](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
境界がある TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>UIElement についての視覚的なフィードバックを提供するクラス  
 <xref:System.Windows.Documents.Adorner>クラスは、ユーザーに視覚的な手掛かりを提供します。 たとえば、使用して、<xref:System.Windows.Documents.Adorner>要素に機能ハンドルを追加またはコントロールに関する状態情報を提供します。 <xref:System.Windows.Documents.Adorner>クラスは、独自の装飾を作成できるようにするフレームワークを提供します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は実装された装飾は提供しません。 詳しくは、[Adorners Overview](adorners-overview.md)をご覧ください。  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>ユーザーがテキストを入力できるようにするクラス  
 WPF は、ユーザーがテキストを入力できるようにする 3 つの主なコントロールを提供します。 各コントロールは、異なる方法で、テキストを表示します。 次の表は、これら 3 つのテキスト関連のコントロール、テキストを表示するときのそれぞれの機能、およびコントロールのテキストを格納するそれぞれのプロパティの一覧です。  
  
|コントロール|テキストの表示形態|コンテンツのプロパティ|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|プレーンテキスト|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|書式付きテキスト|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|非表示のテキスト (文字はマスクされます)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>テキストを表示するクラス  
 いくつかのクラスを使用して、プレーン テキストまたは書式設定されたテキストを表示できます。 使用することができます<xref:System.Windows.Controls.TextBlock>少量のテキストを表示します。 大量のテキストを表示する場合は、使用、 <xref:System.Windows.Controls.FlowDocumentReader>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、または<xref:System.Windows.Controls.FlowDocumentScrollViewer>コントロール。  
  
 <xref:System.Windows.Controls.TextBlock>は 2 つのコンテンツ プロパティがあります:<xref:System.Windows.Controls.TextBlock.Text%2A>と<xref:System.Windows.Controls.TextBlock.Inlines%2A>します。 一貫した書式設定を使用するテキストを表示するときに、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティは、多くの場合、最適な選択肢です。 テキスト全体でさまざまな書式設定を使用する場合を使用して、<xref:System.Windows.Controls.TextBlock.Inlines%2A>プロパティ。 <xref:System.Windows.Controls.TextBlock.Inlines%2A>プロパティのコレクションである<xref:System.Windows.Documents.Inline>オブジェクトで、テキストの書式設定する方法を指定します。  
  
 次の表に、コンテンツのプロパティの<xref:System.Windows.Controls.FlowDocumentReader>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、および<xref:System.Windows.Controls.FlowDocumentScrollViewer>クラス。  
  
|コントロール|コンテンツのプロパティ|コンテンツのプロパティの型|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|ドキュメント|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|ドキュメント|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|ドキュメント|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument>実装、<xref:System.Windows.Documents.IDocumentPaginatorSource>インターフェイス。 したがって、3 つすべてのクラスがかかることができます、<xref:System.Windows.Documents.FlowDocument>コンテンツとして。  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>テキストを書式設定するクラス  
 <xref:System.Windows.Documents.TextElement> およびその関連クラスは、テキストの書式設定できます。 <xref:System.Windows.Documents.TextElement> オブジェクトが含まれてし、に書式を<xref:System.Windows.Controls.TextBlock>と<xref:System.Windows.Documents.FlowDocument>オブジェクト。 2 つの主な種類の<xref:System.Windows.Documents.TextElement>オブジェクトが<xref:System.Windows.Documents.Block>要素と<xref:System.Windows.Documents.Inline>要素。 A<xref:System.Windows.Documents.Block>要素は、段落やリストなどのテキストのブロックを表します。 <xref:System.Windows.Documents.Inline>要素ブロック内のテキストの一部を表します。 多く<xref:System.Windows.Documents.Inline>クラスは、適用先のテキストの書式を指定します。 各<xref:System.Windows.Documents.TextElement>独自のコンテンツ モデルがあります。 詳細については、「[TextElement Content Model Overview](../advanced/textelement-content-model-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [詳細設定](../advanced/index.md)
