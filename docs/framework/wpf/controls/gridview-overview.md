---
title: GridView の概要
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 98bc7985172cabeab19469af4b4c21e13a6bce73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181901"
---
# <a name="gridview-overview"></a>GridView の概要
<xref:System.Windows.Controls.GridView>ビュー モードは、コントロールのビュー モード<xref:System.Windows.Controls.ListView>の 1 つです。 クラス<xref:System.Windows.Controls.GridView>とそのサポート クラスを使用すると、ユーザーは、通常、ボタンを対話型の列ヘッダーとして使用するテーブルの項目コレクションを表示できます。 このトピックでは、<xref:System.Windows.Controls.GridView>クラスを紹介し、その使用方法の概要を説明します。  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>GridView のビューとは?  
 ビュー<xref:System.Windows.Controls.GridView>モードでは、データ フィールドを列に連結し、列ヘッダーを表示してフィールドを識別することで、データ項目の一覧を表示します。 既定<xref:System.Windows.Controls.GridView>のスタイルでは、ボタンが列ヘッダーとして実装されます。 列ヘッダーのボタンを使用すると、重要なユーザー操作機能を実装できます。たとえば、ユーザーは列ヘッダーをクリックして、特定<xref:System.Windows.Controls.GridView>の列の内容に従ってデータを並べ替えることができます。  
  
> [!NOTE]
> 列ヘッダーに使用<xref:System.Windows.Controls.GridView>するボタン コントロールは、 から<xref:System.Windows.Controls.Primitives.ButtonBase>派生します。  
  
 次の図は、<xref:System.Windows.Controls.GridView>コンテンツの<xref:System.Windows.Controls.ListView>ビューを示しています。  

 ![リスト ビューのコンテンツのグリッド ビューを示すスクリーン ショット。](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>列はオブジェクトによって<xref:System.Windows.Controls.GridViewColumn>表され、コンテンツに合ったサイズを自動的に設定できます。 必要に応じて、 を<xref:System.Windows.Controls.GridViewColumn>明示的に特定の幅に設定できます。 列のサイズは、列ヘッダー間のグリッパーをドラッグすることで変更できます。 また、列の追加、削除、置換、および並べ替えも行うことができます<xref:System.Windows.Controls.GridView>。 ただし、<xref:System.Windows.Controls.GridView>表示されるデータを直接更新することはできません。  
  
 従業員データを表示する を定義<xref:System.Windows.Controls.GridView>する方法を次の例に示します。 この例では、<xref:System.Windows.Controls.ListView>を`EmployeeInfoDataSource`として<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>定義します。 データ カテゴリへの<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>`EmployeeInfoDataSource`バインド<xref:System.Windows.Controls.GridViewColumn>コンテンツのプロパティ定義。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 次の図は、前の例により作成されるテーブルを示しています。 コントロールは、次のオブジェクトからデータを表示します。

 ![グリッドビュー出力を含むリストビューを示すスクリーンショット。](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>GridView のレイアウトとスタイル  
 列セルと 列ヘッダーの幅<xref:System.Windows.Controls.GridViewColumn>は同じです。 既定では、各列の幅がコンテンツに合わせて調整されます。 列を固定幅に設定することもできます。  
  
 関連するデータのコンテンツは水平方向の行に表示されます。 たとえば前の図では、各従業員の姓と名と ID 番号が横一列に並ぶため 1 つのセットとして表示されています。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>GridView の列の定義およびスタイル設定  
 に表示<xref:System.Windows.Controls.GridViewColumn>するデータ フィールドを定義する場合は、 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>または<xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A>プロパティを使用します。 この<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティは、いずれかのテンプレート プロパティよりも優先されます。  
  
 <xref:System.Windows.Controls.GridView>の列の内容の配置を指定するには、 を定義します<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。 を使用して表示<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>される<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>コンテンツには<xref:System.Windows.Controls.ListView>、 プロパティと プロパティを<xref:System.Windows.Controls.GridView>使用しないでください。  
  
 列ヘッダーのテンプレートプロパティとスタイル プロパティを指定するには、 <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridViewColumn>、および<xref:System.Windows.Controls.GridViewColumnHeader>クラスを使用します。 詳細については、[GridView の列ヘッダーのスタイルとテンプレートの概要](gridview-column-header-styles-and-templates-overview.md)を参照してください。  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>GridView への視覚的要素の追加  
 コントロールなどの<xref:System.Windows.Controls.CheckBox><xref:System.Windows.Controls.Button>ビジュアル要素をビュー モードに追加するには、<xref:System.Windows.Controls.GridView>テンプレートまたはスタイルを使用します。  
  
 ビジュアル要素をデータ項目として明示的に定義した場合、その要素は 1 回だけ表示<xref:System.Windows.Controls.GridView>できます。 この制限が存在する理由は 1 つの要素は 1 つの親しか持てないためです。したがって視覚的要素をビジュアル ツリーに 1 回だけ表示できます。  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>GridView での行のスタイル設定  
 クラスと<xref:System.Windows.Controls.GridViewRowPresenter><xref:System.Windows.Controls.GridViewHeaderRowPresenter>クラスを使用して、 の行の<xref:System.Windows.Controls.GridView>書式設定と表示を行います。 ビュー モードで行のスタイルを設定する方法の例については、「 [GridView を実装する ListView の行のスタイル設定](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)」を参照してください。 <xref:System.Windows.Controls.GridView>  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>ItemContainerStyle 使用時の配置問題  
 列ヘッダーとセルの間の位置合わせの問題を回避するには、プロパティを設定したり、のアイテムの幅に影響するテンプレート<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>を指定したりしないでください。 たとえば、プロパティを設定したり、<xref:System.Windows.FrameworkElement.Margin%2A><xref:System.Windows.Controls.ListView>コントロールで定義されている<xref:System.Windows.Controls.ControlTemplate>に<xref:System.Windows.Controls.CheckBox>を追加<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>する を指定したりしないでください。 代わりに、ビュー モードを定義するクラスで列幅に直接影響する<xref:System.Windows.Controls.GridView>プロパティとテンプレートを指定します。  
  
 たとえば、ビュー モードで<xref:System.Windows.Controls.CheckBox><xref:System.Windows.Controls.GridView>行に を追加<xref:System.Windows.Controls.CheckBox>するには、<xref:System.Windows.DataTemplate>に を追加し、プロパティを<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>その<xref:System.Windows.DataTemplate>行に設定します。  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>ユーザーによる GridView の操作  
 アプリケーションで を<xref:System.Windows.Controls.GridView>使用すると、ユーザーは を操作したり、 の書式を<xref:System.Windows.Controls.GridView>変更したりできます。 たとえばユーザーは、列の順序の変更、列のサイズの変更、テーブルのアイテムの選択、コンテンツのスクロールを実行できます。 ユーザーが列ヘッダーのボタンをクリックしたときに応答するイベント ハンドラーを定義することもできます。 イベント ハンドラーは、列の内容に<xref:System.Windows.Controls.GridView>従って表示されるデータの並べ替えなどの操作を実行できます。  
  
 次の一覧では、ユーザー操作に使用<xref:System.Windows.Controls.GridView>する機能について詳しく説明します。  
  
- **ドラッグ アンド ドロップで列の順序を変更する**  
  
     ユーザーは、列ヘッダーの上<xref:System.Windows.Controls.GridView>にあるときにマウスの左ボタンを押し、その列を新しい位置にドラッグすることで、列の順序を変更できます。 ユーザーが列ヘッダーをドラッグしている間、そのヘッダーの浮動バージョンと、列を挿入する場所を示す黒い実線が表示されます。  
  
     ヘッダーのフローティング バージョンの既定のスタイルを変更する場合は、プロパティが<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>に<xref:System.Windows.Controls.GridViewColumnHeader>設定されたときにトリガーされる型の<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>を指定します。 詳細については、[ドラッグした GridView 列ヘッダーのスタイルを作成する](how-to-create-a-style-for-a-dragged-gridview-column-header.md)を参照してください。  
  
- **内容に合わせて列のサイズを変更する**  
  
     ユーザーは列ヘッダーの右側にあるグリッパーをダブルクリックすると、内容に合わせて列のサイズを変更できます。  
  
    > [!NOTE]
    > プロパティを<xref:System.Windows.Controls.GridViewColumn.Width%2A>に`Double.NaN`設定して、同じ効果を得ることができます。  
  
- **行の項目を選択する**  
  
     ユーザーは、 で 1 つまたは<xref:System.Windows.Controls.GridView>複数の項目を選択できます。  
  
     選択した項目の を<xref:System.Windows.Style>変更する場合は、「 [ListView で選択した項目のスタイルを設定するためにトリガーを使用する」を](how-to-use-triggers-to-style-selected-items-in-a-listview.md)参照してください。  
  
- **スクロールして画面に表示されていない内容を表示する**  
  
     のサイズ<xref:System.Windows.Controls.GridView>がすべての項目を表示するのに十分な大きさでない場合、ユーザーは<xref:System.Windows.Controls.ScrollViewer>コントロールによって提供されるスクロール バーを使用して、水平方向または垂直方向にスクロールできます。 A<xref:System.Windows.Controls.Primitives.ScrollBar>は、すべてのコンテンツが特定の方向に表示されている場合は非表示になります。 列ヘッダーは、垂直スクロール バーでのスクロール操作ではなく水平方向のスクロール操作を行います。  
  
- **列ヘッダーのボタンをクリックして列を操作する**  
  
     ユーザーは並べ替えアルゴリズムを指定しておけば、列ヘッダーのボタンをクリックして列に表示されているデータを並べ替えることができます。  
  
     ソートアルゴリズムのような機能<xref:System.Windows.Controls.Primitives.ButtonBase.Click>を提供するために、列ヘッダーボタンのイベントを処理できます。 1 つの<xref:System.Windows.Controls.Primitives.ButtonBase.Click>列ヘッダーのイベントを処理するには、 にイベント ハンドラー<xref:System.Windows.Controls.GridViewColumnHeader>を設定します。 すべての列ヘッダーのイベントを<xref:System.Windows.Controls.Primitives.ButtonBase.Click>処理するイベント ハンドラーを設定するには、コントロールにハンドラーを<xref:System.Windows.Controls.ListView>設定します。  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>その他のカスタム ビューの取得  
 抽象<xref:System.Windows.Controls.GridView>クラスから派生した<xref:System.Windows.Controls.ViewBase>クラスは、<xref:System.Windows.Controls.ListView>クラスの表示モードの 1 つにすぎません。 クラスから派生して、その他<xref:System.Windows.Controls.ListView>のカスタム ビューを<xref:System.Windows.Controls.ViewBase>作成できます。 カスタム ビュー モードの例については、[ListView のカスタム ビュー モードを作成する](how-to-create-a-custom-view-mode-for-a-listview.md)を参照してください。  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>GridViewサポート クラス  
 次のクラスは、<xref:System.Windows.Controls.GridView>ビュー モードをサポートします。  
  
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
- [ハウツートピック](listview-how-to-topics.md)
