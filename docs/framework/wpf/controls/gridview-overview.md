---
title: GridView の概要
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 6da556296679de1161f609a7731c6fbf14e94730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966468"
---
# <a name="gridview-overview"></a>GridView の概要
<xref:System.Windows.Controls.GridView>表示モードは、 <xref:System.Windows.Controls.ListView>コントロールの表示モードの1つです。 <xref:System.Windows.Controls.GridView>クラスとそのサポートクラスを使用すると、ユーザーとユーザーは、通常はボタンを対話的な列ヘッダーとして使用するテーブル内の項目コレクションを表示できます。 このトピックでは<xref:System.Windows.Controls.GridView> 、クラスの概要とその用途について説明します。  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>GridView のビューとは?  
 <xref:System.Windows.Controls.GridView>ビューモードでは、データフィールドを列にバインドし、フィールドを識別するための列ヘッダーを表示することによって、データ項目の一覧を表示します。 既定<xref:System.Windows.Controls.GridView>のスタイルでは、ボタンが列ヘッダーとして実装されます。 列ヘッダーのボタンを使用すると、重要なユーザー操作機能を実装できます。たとえば、ユーザーは列ヘッダーをクリックして、 <xref:System.Windows.Controls.GridView>特定の列の内容に従ってデータを並べ替えることができます。  
  
> [!NOTE]
> 列ヘッダーに使用<xref:System.Windows.Controls.GridView>するボタンコントロールは、から<xref:System.Windows.Controls.Primitives.ButtonBase>派生します。  
  
 次の図は、 <xref:System.Windows.Controls.GridView>コンテンツの<xref:System.Windows.Controls.ListView>ビューを示しています。  
    
 ![ListView コンテンツの GridView ビューを示すスクリーンショット。](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>列はオブジェクトに<xref:System.Windows.Controls.GridViewColumn>よって表され、その内容に合わせて自動的にサイズを変更できます。 必要に応じて、を<xref:System.Windows.Controls.GridViewColumn>特定の幅に明示的に設定することもできます。 列のサイズは、列ヘッダー間のグリッパーをドラッグすることで変更できます。 この機能はに<xref:System.Windows.Controls.GridView>組み込まれているため、列の追加、削除、置換、および並べ替えを動的に行うこともできます。 ただし、 <xref:System.Windows.Controls.GridView>では、表示されるデータを直接更新することはできません。  
  
 次の例では、従業員データ<xref:System.Windows.Controls.GridView>を表示するを定義する方法を示します。 この例<xref:System.Windows.Controls.ListView>では、は`EmployeeInfoDataSource`をと<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>して定義します。 コンテンツをデータカテゴリ<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>に<xref:System.Windows.Controls.GridViewColumn>バインドする`EmployeeInfoDataSource`のプロパティ定義。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 次の図は、前の例により作成されるテーブルを示しています。 GridView コントロールには、ItemsSource オブジェクトのデータが表示されます。
    
 ![GridView の出力を含む ListView を示すスクリーンショット。](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>GridView のレイアウトとスタイル  
 の<xref:System.Windows.Controls.GridViewColumn>列セルと列ヘッダーの幅は同じです。 既定では、各列の幅がコンテンツに合わせて調整されます。 列を固定幅に設定することもできます。  
  
 関連するデータのコンテンツは水平方向の行に表示されます。 たとえば前の図では、各従業員の姓と名と ID 番号が横一列に並ぶため 1 つのセットとして表示されています。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>GridView の列の定義およびスタイル設定  
 に<xref:System.Windows.Controls.GridViewColumn>表示するデータフィールドを定義する場合は、、 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>、または<xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A>の各プロパティを使用します。 プロパティ<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>は、どちらのテンプレートプロパティよりも優先されます。  
  
 の<xref:System.Windows.Controls.GridView>列のコンテンツの配置を指定するには<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>、を定義します。 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>を使用<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> して<xref:System.Windows.Controls.ListView>表示されるコンテンツには、プロパティとプロパティを使用しないでください。<xref:System.Windows.Controls.GridView>  
  
 列ヘッダーのテンプレートおよびスタイルプロパティを指定するには<xref:System.Windows.Controls.GridView>、 <xref:System.Windows.Controls.GridViewColumn>、、 <xref:System.Windows.Controls.GridViewColumnHeader>およびの各クラスを使用します。 詳細については、[GridView の列ヘッダーのスタイルとテンプレートの概要](gridview-column-header-styles-and-templates-overview.md)を参照してください。  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>GridView への視覚的要素の追加  
 コントロールやコントロールなどのビジュアル要素<xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.GridView>を表示モードに追加するには、テンプレートまたはスタイルを使用します。 <xref:System.Windows.Controls.Button>  
  
 ビジュアル要素をデータ項目として明示的に定義した場合は、で<xref:System.Windows.Controls.GridView>1 回だけ表示できます。 この制限が存在する理由は 1 つの要素は 1 つの親しか持てないためです。したがって視覚的要素をビジュアル ツリーに 1 回だけ表示できます。  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>GridView での行のスタイル設定  
 <xref:System.Windows.Controls.GridViewRowPresenter>クラスと<xref:System.Windows.Controls.GridViewHeaderRowPresenter>クラスを使用して、 <xref:System.Windows.Controls.GridView>の行の書式設定と表示を行います。 <xref:System.Windows.Controls.GridView>ビューモードで行のスタイルを適用する方法の例については、「 [GridView を実装する ListView で行のスタイル](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)を適用する」を参照してください。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>ItemContainerStyle 使用時の配置問題  
 列ヘッダーとセル間の配置の問題を回避するには、プロパティを設定<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>したり、内の項目の幅に影響を与えるテンプレートを指定したりしないでください。 たとえば<xref:System.Windows.FrameworkElement.Margin%2A> 、プロパティを設定したり、 <xref:System.Windows.Controls.ListView>コントロールで定義<xref:System.Windows.Controls.ControlTemplate>されて<xref:System.Windows.Controls.CheckBox>いるに<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>を追加するを指定したりしないでください。 代わりに、ビューモードを<xref:System.Windows.Controls.GridView>定義するクラスの列幅に直接影響を与えるプロパティとテンプレートを指定します。  
  
 たとえば<xref:System.Windows.Controls.CheckBox> 、 <xref:System.Windows.Controls.GridView> <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate>ビューモード<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>でを行に追加するには、をに追加し、プロパティをそれに設定します。<xref:System.Windows.Controls.CheckBox>  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>ユーザーによる GridView の操作  
 アプリケーションでを<xref:System.Windows.Controls.GridView>使用すると、ユーザーはと対話し、 <xref:System.Windows.Controls.GridView>の書式を変更できます。 たとえばユーザーは、列の順序の変更、列のサイズの変更、テーブルのアイテムの選択、コンテンツのスクロールを実行できます。 ユーザーが列ヘッダーのボタンをクリックしたときに応答するイベント ハンドラーを定義することもできます。 イベントハンドラーは、列の内容に従って、 <xref:System.Windows.Controls.GridView>に表示されるデータの並べ替えなどの操作を実行できます。  
  
 次の一覧では、ユーザーの操作にを<xref:System.Windows.Controls.GridView>使用するの機能の詳細について説明します。  
  
- **ドラッグ アンド ドロップで列の順序を変更する**  
  
     ユーザーは、列ヘッダーの<xref:System.Windows.Controls.GridView>上にマウスの左ボタンを置き、その列を新しい位置にドラッグすることによって、内の列の順序を変更できます。 ユーザーが列ヘッダーをドラッグしている間、そのヘッダーの浮動バージョンと、列を挿入する場所を示す黒い実線が表示されます。  
  
     ヘッダーのフローティングバージョンの既定のスタイルを変更する場合<xref:System.Windows.Controls.ControlTemplate>は、 <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>プロパティがに<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>設定され<xref:System.Windows.Controls.GridViewColumnHeader>ているときにトリガーされる型に対してを指定します。 詳細については、[ドラッグした GridView 列ヘッダーのスタイルを作成する](how-to-create-a-style-for-a-dragged-gridview-column-header.md)を参照してください。  
  
- **内容に合わせて列のサイズを変更する**  
  
     ユーザーは列ヘッダーの右側にあるグリッパーをダブルクリックすると、内容に合わせて列のサイズを変更できます。  
  
    > [!NOTE]
    > <xref:System.Windows.Controls.GridViewColumn.Width%2A>プロパティをに`Double.NaN`設定すると、同じ効果を得ることができます。  
  
- **行の項目を選択する**  
  
     ユーザーは、 <xref:System.Windows.Controls.GridView>内の1つ以上の項目を選択できます。  
  
     選択した項目<xref:System.Windows.Style>のを変更する場合は、「トリガーを使用して[ListView で選択した項目のスタイルを](how-to-use-triggers-to-style-selected-items-in-a-listview.md)設定する」を参照してください。  
  
- **スクロールして画面に表示されていない内容を表示する**  
  
     のサイズ<xref:System.Windows.Controls.GridView>が、すべての項目を表示するのに十分な大きさではない場合、ユーザーは<xref:System.Windows.Controls.ScrollViewer>コントロールによって提供されるスクロールバーを使用して、水平方向または垂直方向にスクロールできます。 すべて<xref:System.Windows.Controls.Primitives.ScrollBar>のコンテンツが特定の方向に表示される場合、は表示されません。 列ヘッダーは、垂直スクロール バーでのスクロール操作ではなく水平方向のスクロール操作を行います。  
  
- **列ヘッダーのボタンをクリックして列を操作する**  
  
     ユーザーは並べ替えアルゴリズムを指定しておけば、列ヘッダーのボタンをクリックして列に表示されているデータを並べ替えることができます。  
  
     並べ替えアルゴリズムのよう<xref:System.Windows.Controls.Primitives.ButtonBase.Click>な機能を提供するために、列ヘッダーのボタンのイベントを処理することができます。 1つの<xref:System.Windows.Controls.Primitives.ButtonBase.Click>列ヘッダーのイベントを処理するには<xref:System.Windows.Controls.GridViewColumnHeader>、でイベントハンドラーを設定します。 すべての列ヘッダーの<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを処理するイベントハンドラーを設定するには、 <xref:System.Windows.Controls.ListView>コントロールにハンドラーを設定します。  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>その他のカスタム ビューの取得  
 抽象クラスから派生した<xref:System.Windows.Controls.ListView> クラスは、クラスで使用できる表示モードの1つにすぎません。<xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ViewBase> クラスから派生することによっ<xref:System.Windows.Controls.ListView>て、 <xref:System.Windows.Controls.ViewBase>の他のカスタムビューを作成できます。 カスタム ビュー モードの例については、[ListView のカスタム ビュー モードを作成する](how-to-create-a-custom-view-mode-for-a-listview.md)を参照してください。  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>GridViewサポート クラス  
 次のクラスは、 <xref:System.Windows.Controls.GridView>表示モードをサポートしています。  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [ListView の概要](listview-overview.md)
- [ヘッダーがクリックされたときに GridView 列を並べ替える](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [方法トピック](listview-how-to-topics.md)
