---
title: テーブルの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 01ab11d8e3c1d2c84514770816ca9c9eab0835b6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649192"
---
# <a name="table-overview"></a>テーブルの概要
<xref:System.Windows.Documents.Table> フロー ドキュメント コンテンツのグリッド ベースのプレゼンテーションをサポートするブロック レベル要素です。 この要素は、その柔軟性により非常に便利ですが、正しく理解して使用するのが難しいとも言えます。  
  
 このトピックは、次のセクションで構成されています。  
  
- [テーブルの基本](#table_basics)  
  
- [テーブルとグリッドの相違点](#table_vs_Grid)  
  
- [テーブルの基本構造](#basic_table_structure)  
  
- [テーブルの内容](#table_containment)  
  
- [行グループ](#row_groupings)  
  
- [背景のレンダリングの優先順位](#rendering_precedence)  
  
- [複数の行または列にまたがるセル](#spanning_rows_or_columns)  
  
- [テーブルとコードのバインディング](#building_a_table_with_code)  
  
- 関連トピック 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>テーブルの基本  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>テーブルとグリッドの相違点  
 <xref:System.Windows.Documents.Table> <xref:System.Windows.Controls.Grid>いくつかの一般的な機能を共有するが、各はさまざまなシナリオに最適です。 A<xref:System.Windows.Documents.Table>はフロー コンテンツ内で使用するために設計されています (を参照してください[フロー ドキュメントの概要](flow-document-overview.md)フロー コンテンツの詳細については)。 グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。 内で、 <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Table>サポート フロー コンテンツの動作の改ページ、列のリフロー、コンテンツの選択中になど、<xref:System.Windows.Controls.Grid>はありません。 A<xref:System.Windows.Controls.Grid>一方は最も以外で使用される、<xref:System.Windows.Documents.FlowDocument>など多くの理由で<xref:System.Windows.Controls.Grid>行と列のインデックスに基づいて要素を追加します<xref:System.Windows.Documents.Table>はありません。 <xref:System.Windows.Controls.Grid>要素により、1 つの「セルです」内に要素を 1 つ以上の子コンテンツのレイヤー。 <xref:System.Windows.Documents.Table> 階層化はサポートされません。 子要素を<xref:System.Windows.Controls.Grid>「セル」境界の領域に対して絶対配置できます。 <xref:System.Windows.Documents.Table> この機能をサポートしません。 最後に、<xref:System.Windows.Controls.Grid>少ないリソースが必要です、<xref:System.Windows.Documents.Table>ので使用を検討して、<xref:System.Windows.Controls.Grid>パフォーマンスを向上させる。  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>テーブルの基本構造  
 <xref:System.Windows.Documents.Table> 列で構成されるグリッド ベースのプレゼンテーションを提供します (によって表される<xref:System.Windows.Documents.TableColumn>要素) と行 (によって表される<xref:System.Windows.Documents.TableRow>要素)。 <xref:System.Windows.Documents.TableColumn> 要素のコンテンツをホストしていません。単に列と列の特性を定義します。 <xref:System.Windows.Documents.TableRow> 要素をホストする必要があります、<xref:System.Windows.Documents.TableRowGroup>要素で、テーブルの行のグループ化を定義します。 <xref:System.Windows.Documents.TableCell> テーブルに表示する実際のコンテンツが含まれる要素をホストする必要があります、<xref:System.Windows.Documents.TableRow>要素。 <xref:System.Windows.Documents.TableCell> 派生した要素を含めることができますのみ<xref:System.Windows.Documents.Block>します。  有効な子要素を<xref:System.Windows.Documents.TableCell>が含まれます。  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> 要素は、テキスト コンテンツを直接ホストしない可能性があります。 コンテンツ要素などのフローのコンテインメイト規則の詳細については<xref:System.Windows.Documents.TableCell>を参照してください[フロー ドキュメントの概要](flow-document-overview.md)します。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> ような<xref:System.Windows.Controls.Grid>要素が、その他の機能があり、そのため、大きいリソースのオーバーヘッドが必要です。  
  
 次の例では、単純な 2 × 3 テーブル[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]します。  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 この例の表示結果を次の図に示します。  
  
 ![基本的なテーブルの表示方法を示すスクリーン ショット。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>テーブルの内容  
 <xref:System.Windows.Documents.Table> 派生した、<xref:System.Windows.Documents.Block>要素の一般的な規則に準拠している<xref:System.Windows.Documents.Block>レベルの要素。  A<xref:System.Windows.Documents.Table>次の要素のいずれかで要素を含めることがあります。  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>行グループ  
 <xref:System.Windows.Documents.TableRowGroup>要素がテーブル内の行を任意にグループ化する方法を提供します。 テーブル内のすべての行が行グループに属している必要があります。  多くの場合、行グループ内の行は共通の目的を共有しており、1 つのグループとしてスタイルを設定できます。  一般に、行のグループ化は、テーブルに格納された主要コンテンツから、特別な目的を持つ行 (タイトル行、ヘッダー行、フッター行など) を分離するために使用します。  
  
 次の例では[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]をスタイル設定されたヘッダーとフッター行を含むテーブルを定義します。  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーン ショット:テーブルの行グループ](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>背景のレンダリングの優先順位  
 テーブル要素は、次の順序でレンダリングされます (優先順位の低い項目から高い項目の z オーダー)。 この順序は変更できません。 たとえば、これらの要素には、確立された順序をオーバーライドするための "Z オーダー" プロパティは用意されていません。  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 テーブル内のこれらの各要素に対して背景色を定義する例を次に示します。  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 次の図は、この例の表示結果 (背景色のみ表示) を示したものです。  
  
 ![スクリーン ショット:テーブル z&#45;順序](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>複数の行または列にまたがるセル  
 使用して複数の行または列にまたがるテーブルのセルを構成することが、<xref:System.Windows.Documents.TableCell.RowSpan%2A>または<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>属性にそれぞれします。  
  
 3 つの列にまたがるセルの例を次に示します。  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーン ショット:次の 3 つのすべての列にまたがるセル](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>テーブルとコードのバインディング  
 次の例では、プログラムで作成する方法、<xref:System.Windows.Documents.Table>し、コンテンツを設定します。 テーブルの内容は 5 つの行に配分 (によって表される<xref:System.Windows.Documents.TableRow>に含まれるオブジェクトを<xref:System.Windows.Documents.Table.RowGroups%2A>オブジェクト) と 6 つの列 (によって表される<xref:System.Windows.Documents.TableColumn>オブジェクト)。 たとえば、タイトル行はテーブル全体のタイトルの設定に使用され、ヘッダー行はテーブル内のデータ列の説明、フッター行は要約情報の格納に使用されます。  "タイトル"、"ヘッダー"、"フッター" 行の概念はテーブルに固有のものではなく、単純に異なる特性を持つ行です。 テーブルのセルは、テキスト、画像、またはその他のほとんどすべての構成は、実際のコンテンツを含めることが[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]要素。  
  
 最初に、<xref:System.Windows.Documents.FlowDocument>が作成されるホストに、 <xref:System.Windows.Documents.Table>、され、新しい<xref:System.Windows.Documents.Table>が作成され、コンテンツの追加、<xref:System.Windows.Documents.FlowDocument>します。  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 次に、6<xref:System.Windows.Documents.TableColumn>オブジェクトが作成され、テーブルの追加<xref:System.Windows.Documents.Table.Columns%2A>コレクション、書式を適用します。  
  
> [!NOTE]
>  なお、テーブルの<xref:System.Windows.Documents.Table.Columns%2A>コレクションは、標準の 0 から始まるインデックスを使用します。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 次に、タイトル行を作成してテーブルに追加し、書式を適用します。  タイトル行には、テーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 次に、ヘッダー行を作成してテーブルに追加し、ヘッダー行のセルを作成してデータを格納します。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 次に、データ行を作成してテーブルに追加し、この行のセルを作成してデータを格納します。  この行の作成はヘッダー行の作成に似ていますが、適用する書式が少し異なります。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 最後に、フッター行を作成して追加し、書式を設定します。  タイトル行と同様に、フッター行にはテーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>関連項目

- [フロー ドキュメントの概要](flow-document-overview.md)
- [XAML を使用してテーブルを定義する](how-to-define-a-table-with-xaml.md)
- [WPF のドキュメント](documents-in-wpf.md)
- [フロー コンテンツ要素を使用する](how-to-use-flow-content-elements.md)
