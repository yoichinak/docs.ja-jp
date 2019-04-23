---
title: '方法: プログラムによってテーブルをビルドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 315154b37218c0a6845f0a46149fc056780ee650
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172628"
---
# <a name="how-to-build-a-table-programmatically"></a>方法: プログラムによってテーブルをビルドする
次の例では、プログラムで作成する方法、<xref:System.Windows.Documents.Table>し、コンテンツを設定します。 テーブルの内容は 5 つの行に配分 (によって表される<xref:System.Windows.Documents.TableRow>に含まれるオブジェクトを<xref:System.Windows.Documents.Table.RowGroups%2A>オブジェクト) と 6 つの列 (によって表される<xref:System.Windows.Documents.TableColumn>オブジェクト)。 たとえば、タイトル行はテーブル全体のタイトルの設定に使用され、ヘッダー行はテーブル内のデータ列の説明、フッター行は要約情報の格納に使用されます。  "タイトル"、"ヘッダー"、"フッター" 行の概念はテーブルに固有のものではなく、単純に異なる特性を持つ行です。 テーブルのセルは、テキスト、画像、またはその他のほとんどすべての構成は、実際のコンテンツを含めることが[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]要素。  
  
## <a name="example"></a>例  
 最初に、<xref:System.Windows.Documents.FlowDocument>が作成されるホストに、 <xref:System.Windows.Documents.Table>、され、新しい<xref:System.Windows.Documents.Table>が作成され、コンテンツの追加、<xref:System.Windows.Documents.FlowDocument>します。  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>例  
 次に、6<xref:System.Windows.Documents.TableColumn>オブジェクトが作成され、テーブルの追加<xref:System.Windows.Documents.Table.Columns%2A>コレクション、書式を適用します。  
  
> [!NOTE]
>  なお、テーブルの<xref:System.Windows.Documents.Table.Columns%2A>コレクションは、標準の 0 から始まるインデックスを使用します。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>例  
 次に、タイトル行が作成され、テーブルに追加されます。いくつかの書式設定が適用されます。  タイトル行には、テーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>例  
 次に、ヘッダー行を作成してテーブルに追加し、ヘッダー行のセルを作成してデータを格納します。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>例  
 次に、データの行が作成され、テーブルに追加されます。この行のセルが作成され、内容が入力されます。  この行の作成はヘッダー行の作成に似ていますが、適用する書式が少し異なります。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>例  
 最後に、フッター行が作成され、追加され、書式設定されます。  タイトル行と同様に、フッター行にはテーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>関連項目

- [テーブルの概要](table-overview.md)
