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
ms.openlocfilehash: 4bd747cea43755116c56b16f1de9a6ffb59935ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187269"
---
# <a name="table-overview"></a>テーブルの概要
<xref:System.Windows.Documents.Table>は、フロー ドキュメント コンテンツのグリッドベースのプレゼンテーションをサポートするブロック レベル要素です。 この要素は、その柔軟性により非常に便利ですが、正しく理解して使用するのが難しいとも言えます。  
  
 このトピックの内容は次のとおりです。  
  
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
 <xref:System.Windows.Documents.Table>共通<xref:System.Windows.Controls.Grid>の機能を共有しますが、それぞれのシナリオに最適です。 A<xref:System.Windows.Documents.Table>はフロー コンテンツ内で使用するように設計されています (フロー コンテンツの詳細については、「[フロー ドキュメントの概要](flow-document-overview.md)」を参照)。 グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。 <xref:System.Windows.Documents.FlowDocument>内では、<xref:System.Windows.Documents.Table>ページネーション、列のリフロー、コンテンツ選択などのフローコンテンツの動作をサポートしますが<xref:System.Windows.Controls.Grid>、a はサポートしません。 一<xref:System.Windows.Controls.Grid>方、行と列のインデックスに基づく<xref:System.Windows.Documents.FlowDocument>要素の追加など<xref:System.Windows.Controls.Grid>、<xref:System.Windows.Documents.Table>多くの理由から、A は使用するのが最適です。 この<xref:System.Windows.Controls.Grid>要素を使用すると、子コンテンツの階層化が可能になり、1 つの "セル" 内に複数の要素が存在できます。 <xref:System.Windows.Documents.Table>は、レイヤ化をサポートしていません。 子要素は<xref:System.Windows.Controls.Grid>、"セル" 境界の領域に対して絶対に位置指定できます。 <xref:System.Windows.Documents.Table>この機能はサポートされていません。 最後に、<xref:System.Windows.Controls.Grid>は必要なリソース<xref:System.Windows.Documents.Table>が少ないので、<xref:System.Windows.Controls.Grid>を使用してパフォーマンスを向上することを検討してください。  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a>テーブルの基本構造  
 <xref:System.Windows.Documents.Table>は、(要素によって表される) 列と行<xref:System.Windows.Documents.TableColumn>(要素で表される)<xref:System.Windows.Documents.TableRow>から構成されるグリッドベースのプレゼンテーションを提供します。 <xref:System.Windows.Documents.TableColumn>要素はコンテンツをホストしません。列と列の特性を定義するだけです。 <xref:System.Windows.Documents.TableRow>要素は、テーブルの行の<xref:System.Windows.Documents.TableRowGroup>グループ化を定義する要素でホストされる必要があります。 <xref:System.Windows.Documents.TableCell>要素は、テーブルによって表示される実際のコンテンツを含み、<xref:System.Windows.Documents.TableRow>要素内でホストされる必要があります。 <xref:System.Windows.Documents.TableCell>から派生する要素のみを含めることができます<xref:System.Windows.Documents.Block>。  インクルードに有効な<xref:System.Windows.Documents.TableCell>子要素。  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>要素はテキストコンテンツを直接ホストすることはできません。 フロー<xref:System.Windows.Documents.TableCell>コンテンツ要素の包含構造ルールの詳細については、「 フロー[ドキュメントの概要](flow-document-overview.md)」を参照してください。  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>要素に<xref:System.Windows.Controls.Grid>似ていますが、より多くの機能を持っているので、リソースのオーバーヘッドが大きくなります。  
  
 次の例では、XAML を使用して簡単な 2 x 3 テーブルを定義します。  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 この例がどのように表示されるかを次の図に示します。  
  
 ![基本的なテーブルのレンダリング方法を示すスクリーンショット。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a>テーブルの内容  
 <xref:System.Windows.Documents.Table>は<xref:System.Windows.Documents.Block>要素から派生し、レベル要素の共通規則に<xref:System.Windows.Documents.Block>従います。  要素<xref:System.Windows.Documents.Table>は、次のいずれかの要素に含まれる場合があります。  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a>行グループ  
 この<xref:System.Windows.Documents.TableRowGroup>要素は、テーブル内の行を任意にグループ化する方法を提供します。テーブル内のすべての行は、行グループに属している必要があります。  多くの場合、行グループ内の行は共通の目的を共有しており、1 つのグループとしてスタイルを設定できます。  一般に、行のグループ化は、テーブルに格納された主要コンテンツから、特別な目的を持つ行 (タイトル行、ヘッダー行、フッター行など) を分離するために使用します。  
  
 次の例では、XAML を使用して、スタイル付きヘッダー行とフッター行を含むテーブルを定義します。  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 この例がどのように表示されるかを次の図に示します。  
  
 ![スクリーンショット: テーブル行グループ](./media/table-rowgroups.png "Table_RowGroups")  
  
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
  
 ![スクリーンショット: テーブル z&#45;順序](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a>複数の行または列にまたがるセル  
 テーブルセルは、 または 属性を使用して複数の<xref:System.Windows.Documents.TableCell.RowSpan%2A>行または<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>列にまたがるように構成できます。  
  
 3 つの列にまたがるセルの例を次に示します。  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 この例がどのように表示されるかを次の図に示します。  
  
 ![スクリーンショット: 3 つの列すべてにまたがるセル](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a>テーブルとコードのバインディング  
 プログラムで を作成し、コンテンツを<xref:System.Windows.Documents.Table>設定する方法を次の例に示します。 テーブルの内容は、5 つの行 (<xref:System.Windows.Documents.TableRow><xref:System.Windows.Documents.Table.RowGroups%2A>オブジェクトに含まれるオブジェクトで表される) と 6 つの列<xref:System.Windows.Documents.TableColumn>(オブジェクトで表されます) に割り当てられます。 たとえば、タイトル行はテーブル全体のタイトルの設定に使用され、ヘッダー行はテーブル内のデータ列の説明、フッター行は要約情報の格納に使用されます。  "タイトル"、"ヘッダー"、"フッター" 行の概念はテーブルに固有のものではなく、単純に異なる特性を持つ行です。 表のセルには、テキスト、画像、またはその他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]の要素で構成される実際のコンテンツが含まれます。  
  
 まず、<xref:System.Windows.Documents.FlowDocument><xref:System.Windows.Documents.Table>をホストするために が作成され、<xref:System.Windows.Documents.Table>の内容に新しいが作成され、<xref:System.Windows.Documents.FlowDocument>追加されます。  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 次に、6 つの<xref:System.Windows.Documents.TableColumn>オブジェクトが作成され、いくつかの書式<xref:System.Windows.Documents.Table.Columns%2A>が適用されたテーブルのコレクションに追加されます。  
  
> [!NOTE]
> テーブルのコレクションでは、標準<xref:System.Windows.Documents.Table.Columns%2A>の 0 から始まるインデックスを使用することに注意してください。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 次に、タイトル行が作成され、テーブルに追加されます。いくつかの書式設定が適用されます。  タイトル行には、テーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 次に、ヘッダー行が作成され、テーブルに追加されます。ヘッダー行のセルが作成され、内容が入力されます。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 次に、データの行が作成され、テーブルに追加されます。この行のセルが作成され、内容が入力されます。  この行の作成はヘッダー行の作成に似ていますが、適用する書式が少し異なります。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 最後に、フッター行が作成され、追加され、書式設定されます。  タイトル行と同様に、フッター行にはテーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>関連項目

- [フロー ドキュメントの概要](flow-document-overview.md)
- [XAML を使用してテーブルを定義する](how-to-define-a-table-with-xaml.md)
- [WPF のドキュメント](documents-in-wpf.md)
- [フロー コンテンツ要素を使用する](how-to-use-flow-content-elements.md)
