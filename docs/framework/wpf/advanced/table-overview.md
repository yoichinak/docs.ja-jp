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
ms.openlocfilehash: fa7106207c69f19b647ba80ab7e724e9aad174c1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005079"
---
# <a name="table-overview"></a>テーブルの概要
<xref:System.Windows.Documents.Table> は、フロードキュメントのコンテンツのグリッドベースの表示をサポートするブロックレベルの要素です。 この要素は、その柔軟性により非常に便利ですが、正しく理解して使用するのが難しいとも言えます。  
  
 このトピックは次のセクションで構成されます。  
  
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
 <xref:System.Windows.Documents.Table> および <xref:System.Windows.Controls.Grid> はいくつかの一般的な機能を共有しますが、それぞれが異なるシナリオに適しています。 @No__t 0 はフローコンテンツ内で使用するように設計されています (フローコンテンツの詳細については、「[フロードキュメントの概要](flow-document-overview.md)」を参照してください)。 グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。 @No__t-0 の場合、@no__t は、改ページ位置の調整、列の折り返し、コンテンツの選択などのフローコンテンツの動作をサポートしますが、<xref:System.Windows.Controls.Grid> ではサポートされません。 一方、<xref:System.Windows.Controls.Grid> は、<xref:System.Windows.Documents.FlowDocument> の外部で最もよく使用されます。たとえば、<xref:System.Windows.Controls.Grid> などの多くの理由で @no__t、行と列のインデックスに基づいて要素が追加されます。 @No__t-0 要素は、子コンテンツのレイヤーを許可し、1つの "セル" 内に複数の要素を配置できるようにします。 <xref:System.Windows.Documents.Table> は、レイヤーをサポートしていません。 @No__t 0 の子要素は、"セル" の境界の領域を基準として絶対に配置できます。 <xref:System.Windows.Documents.Table> はこの機能をサポートしていません。 最後に、<xref:System.Windows.Controls.Grid> の方が必要なリソースが少なくて済み、@no__t 1 であるため、パフォーマンスを向上させるために <xref:System.Windows.Controls.Grid> を使用することを検討してください。  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>テーブルの基本構造  
 <xref:System.Windows.Documents.Table> は、列 (<xref:System.Windows.Documents.TableColumn> の要素で表される) と行 (<xref:System.Windows.Documents.TableRow> の要素で表される) で構成されるグリッドベースのプレゼンテーションを提供します。 <xref:System.Windows.Documents.TableColumn> の要素はコンテンツをホストしません。列および列の特性を定義するだけです。 @no__t 0 の要素は、テーブルの行のグループ化を定義する <xref:System.Windows.Documents.TableRowGroup> 要素でホストされている必要があります。 テーブルによって表示される実際の内容を含む @no__t 0 の要素は、<xref:System.Windows.Documents.TableRow> の要素でホストされている必要があります。 <xref:System.Windows.Documents.TableCell> には <xref:System.Windows.Documents.Block> から派生した要素のみを含めることができます。  @No__t 0 の有効な子要素には、が含まれます。  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell> の要素は、テキストコンテンツを直接ホストすることはできません。 @No__t-0 などのフローコンテンツ要素の含有規則の詳細については、「[フロードキュメントの概要](flow-document-overview.md)」を参照してください。  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table> は <xref:System.Windows.Controls.Grid> 要素に似ていますが、より多くの機能を備えているため、リソースオーバーヘッドが大きくなります。  
  
 次の例では、XAML を使用して単純な 2 x 3 テーブルを定義します。  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 この例の表示結果を次の図に示します。  
  
 ![基本的なテーブルのレンダリング方法を示すスクリーンショット。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>テーブルの内容  
 <xref:System.Windows.Documents.Table> は、<xref:System.Windows.Documents.Block> 要素から派生し、@no__t 2 レベルの要素の一般的な規則に従います。  @No__t 0 の要素は、次のいずれかの要素に含めることができます。  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>行グループ  
 @No__t-0 要素は、テーブル内の任意の行を任意にグループ化する方法を提供します。テーブル内のすべての行は、行グループに属している必要があります。  多くの場合、行グループ内の行は共通の目的を共有しており、1 つのグループとしてスタイルを設定できます。  一般に、行のグループ化は、テーブルに格納された主要コンテンツから、特別な目的を持つ行 (タイトル行、ヘッダー行、フッター行など) を分離するために使用します。  
  
 次の例では、XAML を使用して、スタイルが設定されたヘッダー行とフッター行を含むテーブルを定義します。  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 この例の表示結果を次の図に示します。  
  
 @no__t 0Screenshot ショット:テーブル行グループ @ no__t-0(./media/table-rowgroups.png "Table_RowGroups")  
  
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
  
 @no__t 0Screenshot ショット:テーブル z&#45;オーダー @ no__t-1(./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>複数の行または列にまたがるセル  
 テーブルセルは、<xref:System.Windows.Documents.TableCell.RowSpan%2A> または <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> の属性をそれぞれ使用して、複数の行または列にまたがるように構成できます。  
  
 3 つの列にまたがるセルの例を次に示します。  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 この例の表示結果を次の図に示します。  
  
 @no__t 0Screenshot ショット:3列すべてにまたがるセル @ no__t-0(./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>テーブルとコードのバインディング  
 次の例では、プログラムを使用して @no__t 0 を作成し、コンテンツを設定する方法を示します。 テーブルの内容は、5つの行 (@no__t 1 のオブジェクトに含まれる @no__t 0 のオブジェクトによって表されます) と6つの列 (<xref:System.Windows.Documents.TableColumn> のオブジェクトによって表される) に分配されます。 たとえば、タイトル行はテーブル全体のタイトルの設定に使用され、ヘッダー行はテーブル内のデータ列の説明、フッター行は要約情報の格納に使用されます。  "タイトル"、"ヘッダー"、"フッター" 行の概念はテーブルに固有のものではなく、単純に異なる特性を持つ行です。 テーブルセルには実際のコンテンツが格納されます。これは、テキスト、イメージ、またはほぼすべての @no__t 0 要素で構成できます。  
  
 まず、<xref:System.Windows.Documents.Table> をホストする @no__t 0 が作成され、新しい <xref:System.Windows.Documents.Table> が作成され、<xref:System.Windows.Documents.FlowDocument> の内容に追加されます。  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 次に、6個の @no__t オブジェクトが作成され、テーブルの @no__t コレクションに追加されます。いくつかの書式設定が適用されます。  
  
> [!NOTE]
> テーブルの @no__t 0 から始まるコレクションでは、標準の0から始まるインデックスが使用されることに注意してください。  
  
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
