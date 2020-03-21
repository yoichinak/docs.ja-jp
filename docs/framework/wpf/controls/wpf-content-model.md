---
title: コンテンツ モデル
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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187405"
---
# <a name="wpf-content-model"></a>WPF のコンテンツ モデル
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、多くのコントロールやコントロールのような型を提供する表示プラットフォームで、その主な目的は、異なる種類のコンテンツを表示することです。 使用するコントロールまたは派生元のコントロールを判断するには、特定のコントロールが最適に表示できるオブジェクトの種類を理解する必要があります。  
  
 このトピックは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールとコントロールのような型に関するコンテンツ モデルのまとめです。 コンテンツ モデルは、どのようなコンテンツをコントロールで使用できるかについて説明します。 このトピックは、各コンテンツ モデルのコンテンツのプロパティもリストします。 コンテンツのプロパティは、オブジェクトのコンテンツの格納に使用されるプロパティです。  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a>任意のコンテンツを含むクラス  
 一部のコントロールには、文字列、<xref:System.DateTime>オブジェクト、追加<xref:System.Windows.UIElement>項目のコンテナーであるなど、任意の型のオブジェクトを含めることができます。 たとえば、 a<xref:System.Windows.Controls.Button>にはイメージとテキストを含めることができます。または、<xref:System.Windows.Controls.CheckBox>の値を含<xref:System.DateTime.Now%2A?displayProperty=nameWithType>めることができます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、任意のコンテンツを含めることができる 4 つのクラスがあります。 次の表は、から<xref:System.Windows.Controls.Control>継承するクラスの一覧です。  
  
|任意のコンテンツを含むクラス|コンテンツ|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|1 つの任意のオブジェクト。|  
|<xref:System.Windows.Controls.HeaderedContentControl>|ヘッダーと 1 つの項目。両方とも任意のオブジェクトです。|  
|<xref:System.Windows.Controls.ItemsControl>|任意のオブジェクトのコレクション。|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|ヘッダーと項目のコレクション。すべて任意のオブジェクトです。|  
  
 これらのクラスから継承するコントロールは、同じ種類のコンテンツを格納でき、同じ方法でコンテンツを処理することができます。 次の図は、イメージとテキストを含む各コンテンツ モデルのコントロールを示しています。  
  
 ![各コンテンツ モデルから 1 つずつ、4 つの異なるコントロールを示すスクリーンショット。](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>任意の 1 つのオブジェクトを格納しているコントロール  
 この<xref:System.Windows.Controls.ContentControl>クラスには、任意のコンテンツが 1 つ含まれています。 そのコンテンツ プロパティ<xref:System.Windows.Controls.ContentControl.Content%2A>は です。 次のコントロールは、<xref:System.Windows.Controls.ContentControl>そのコンテンツ モデルから継承して使用します。  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 次の<xref:System.Windows.Controls.ContentControl.Content%2A>図は、文字列、<xref:System.DateTime>オブジェクト、および を含む<xref:System.Windows.Shapes.Rectangle>の 4 つの<xref:System.Windows.Controls.Panel>ボタン、<xref:System.Windows.Shapes.Ellipse>および<xref:System.Windows.Controls.TextBlock>を含む を示しています。  
  
 ![コンテンツ タイプが異なる 4 つのボタンを示すスクリーンショット。](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>プロパティの設定方法の例については、「」を参照<xref:System.Windows.Controls.ContentControl>してください。  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>ヘッダーと任意の 1 つのオブジェクトを格納しているコントロール  
 この<xref:System.Windows.Controls.HeaderedContentControl>クラスは、ヘッダー<xref:System.Windows.Controls.ContentControl>を持つコンテンツを継承し、表示します。 content プロパティ<xref:System.Windows.Controls.ContentControl.Content%2A>を継承<xref:System.Windows.Controls.ContentControl>し、型<xref:System.Windows.Controls.HeaderedContentControl.Header%2A><xref:System.Object>のプロパティを定義します。したがって、両方とも任意のオブジェクトにすることができます。  
  
 次のコントロールは、<xref:System.Windows.Controls.HeaderedContentControl>そのコンテンツ モデルから継承して使用します。  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 次の図は、2 つのオブジェクトを<xref:System.Windows.Controls.TabItem>示しています。 最初<xref:System.Windows.Controls.TabItem>のオブジェクト<xref:System.Windows.UIElement>は、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>および<xref:System.Windows.Controls.ContentControl.Content%2A>として. は<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>、<xref:System.Windows.Controls.StackPanel><xref:System.Windows.Shapes.Ellipse>と を含む に<xref:System.Windows.Controls.TextBlock>設定されます。 は<xref:System.Windows.Controls.ContentControl.Content%2A>、<xref:System.Windows.Controls.StackPanel><xref:System.Windows.Controls.TextBlock>と を含む に<xref:System.Windows.Controls.Label>設定されます。 2<xref:System.Windows.Controls.TabItem>つ目の場合は<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>、<xref:System.Windows.Controls.TextBlock>に文字列<xref:System.Windows.Controls.ContentControl.Content%2A>が含まれ、 に a が含まれます。  
  
 ![プロパティ内の異なる型を使用するタブ コントロール。](./media/wpf-content-model/control-content-model-tab.png)  
  
 オブジェクトの作成<xref:System.Windows.Controls.TabItem>方法の例については、を参照<xref:System.Windows.Controls.HeaderedContentControl>してください。  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>任意のオブジェクトのコレクションを格納しているコントロール  
 この<xref:System.Windows.Controls.ItemsControl>クラスは、文字列<xref:System.Windows.Controls.Control>、オブジェクト、その他の要素など、複数の項目を継承し、含めることができます。 そのコンテンツ プロパティ<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>は<xref:System.Windows.Controls.ItemsControl.Items%2A>、 および です。 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>は通常、データ コレクション<xref:System.Windows.Controls.ItemsControl>を設定するために使用されます。 コレクションを使用して を設定しない場合は<xref:System.Windows.Controls.ItemsControl>、 プロパティを使用して項目を<xref:System.Windows.Controls.ItemsControl.Items%2A>追加できます。  
  
 次のコントロールは、<xref:System.Windows.Controls.ItemsControl>そのコンテンツ モデルから継承して使用します。  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 次の図は、<xref:System.Windows.Controls.ListBox>次の種類のアイテムを含むを示しています。  
  
- 文字列。  
  
- <xref:System.DateTime> オブジェクト。  
  
- <xref:System.Windows.UIElement> です。  
  
- と<xref:System.Windows.Controls.Panel>を<xref:System.Windows.Shapes.Ellipse>含む<xref:System.Windows.Controls.TextBlock>。  
  
 ![4 種類のコンテンツを含む ListBox を示すスクリーンショット。](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>ヘッダーと任意のオブジェクトのコレクションを含むコントロール  
 この<xref:System.Windows.Controls.HeaderedItemsControl>クラスは、文字列<xref:System.Windows.Controls.ItemsControl>、オブジェクト、その他の要素、ヘッダーなど、複数の項目を継承し、含めることができます。 このクラスは、<xref:System.Windows.Controls.ItemsControl>コンテンツ プロパティ<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>、 <xref:System.Windows.Controls.ItemsControl.Items%2A>、および を<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>継承し、任意のオブジェクトにできるプロパティを定義します。  
  
 次のコントロールは、<xref:System.Windows.Controls.HeaderedItemsControl>そのコンテンツ モデルから継承して使用します。  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>UIElement オブジェクトのコレクションを含むクラス  
 クラス<xref:System.Windows.Controls.Panel>は子<xref:System.Windows.UIElement>オブジェクトを配置し、配置します。 そのコンテンツ プロパティ<xref:System.Windows.Controls.Panel.Children%2A>は です。  
  
 次のクラスは<xref:System.Windows.Controls.Panel>クラスから継承され、そのコンテンツ モデルを使用します。  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 詳細については、「[Panels Overview](panels-overview.md)」を参照してください。  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>UIElement の外観に影響を与えるクラス  
 この<xref:System.Windows.Controls.Decorator>クラスは、視覚効果を 1 つの子<xref:System.Windows.UIElement>に適用するか、または 1 つの子の周囲に適用します。 そのコンテンツ プロパティ<xref:System.Windows.Controls.Decorator.Child%2A>は です。 次のクラスは、<xref:System.Windows.Controls.Decorator>そのコンテンツ モデルから継承し、使用します。  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 次の図は<xref:System.Windows.Controls.TextBox>、周囲に a が付いている<xref:System.Windows.Controls.Border>(装飾されている) を示しています。  
  
 ![境界線が黒の TextBox](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
境界がある TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>UIElement についての視覚的なフィードバックを提供するクラス  
 クラス<xref:System.Windows.Documents.Adorner>は、ユーザーに視覚的な手掛かりを提供します。 たとえば、 を<xref:System.Windows.Documents.Adorner>使用して、要素に機能ハンドルを追加したり、コントロールに関する状態情報を提供したりできます。 クラス<xref:System.Windows.Documents.Adorner>は、独自の装飾を作成できるようにフレームワークを提供します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は実装された装飾は提供しません。 詳しくは、[Adorners Overview](adorners-overview.md)をご覧ください。  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a>ユーザーがテキストを入力できるようにするクラス  
 WPF は、ユーザーがテキストを入力できるようにする 3 つの主なコントロールを提供します。 各コントロールは、異なる方法で、テキストを表示します。 次の表は、これら 3 つのテキスト関連のコントロール、テキストを表示するときのそれぞれの機能、およびコントロールのテキストを格納するそれぞれのプロパティの一覧です。  
  
|コントロール|テキストの表示形態|コンテンツのプロパティ|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|プレーンテキスト ファイル|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|書式付きテキスト|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|非表示のテキスト (文字はマスクされます)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a>テキストを表示するクラス  
 いくつかのクラスを使用して、プレーン テキストまたは書式設定されたテキストを表示できます。 を使用<xref:System.Windows.Controls.TextBlock>して、少量のテキストを表示できます。 大量のテキストを表示する場合は、 、<xref:System.Windows.Controls.FlowDocumentReader><xref:System.Windows.Controls.FlowDocumentPageViewer>または<xref:System.Windows.Controls.FlowDocumentScrollViewer>コントロールを使用します。  
  
 には<xref:System.Windows.Controls.TextBlock>、 と の<xref:System.Windows.Controls.TextBlock.Text%2A><xref:System.Windows.Controls.TextBlock.Inlines%2A>2 つのコンテンツ プロパティがあります。 一貫性のある書式を使用するテキストを表示する場合<xref:System.Windows.Controls.TextBlock.Text%2A>、多くの場合、プロパティが最適な選択肢になります。 テキスト全体で異なる書式を使用する場合は、<xref:System.Windows.Controls.TextBlock.Inlines%2A>プロパティを使用します。 プロパティ<xref:System.Windows.Controls.TextBlock.Inlines%2A>は、テキストの書式設定<xref:System.Windows.Documents.Inline>方法を指定するオブジェクトのコレクションです。  
  
 次の表は、 、 <xref:System.Windows.Controls.FlowDocumentReader>、<xref:System.Windows.Controls.FlowDocumentPageViewer>および<xref:System.Windows.Controls.FlowDocumentScrollViewer>クラスのコンテンツ プロパティの一覧です。  
  
|コントロール|コンテンツのプロパティ|コンテンツのプロパティの型|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|ドキュメント|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|ドキュメント|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|ドキュメント|<xref:System.Windows.Documents.FlowDocument>|  
  
 は<xref:System.Windows.Documents.FlowDocument>インターフェイスを実装<xref:System.Windows.Documents.IDocumentPaginatorSource>します。したがって、3 つのクラスはすべてコンテンツ<xref:System.Windows.Documents.FlowDocument>として受け取ることができます。  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a>テキストを書式設定するクラス  
 <xref:System.Windows.Documents.TextElement>また、関連するクラスを使用してテキストの書式を設定できます。 <xref:System.Windows.Documents.TextElement>オブジェクトには、テキストとオブジェクト<xref:System.Windows.Controls.TextBlock>が<xref:System.Windows.Documents.FlowDocument>含まれ、書式設定されます。 オブジェクトの<xref:System.Windows.Documents.TextElement>2 つの主要<xref:System.Windows.Documents.Block>な型<xref:System.Windows.Documents.Inline>は、要素と要素です。 要素<xref:System.Windows.Documents.Block>は、段落やリストなどのテキストのブロックを表します。 要素<xref:System.Windows.Documents.Inline>は、ブロック内のテキストの一部を表します。 多<xref:System.Windows.Documents.Inline>くのクラスでは、適用するテキストの書式を指定します。 それぞれに<xref:System.Windows.Documents.TextElement>独自のコンテンツ モデルがあります。 詳細については、「[TextElement Content Model Overview](../advanced/textelement-content-model-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [[詳細設定](../advanced/index.md)]
