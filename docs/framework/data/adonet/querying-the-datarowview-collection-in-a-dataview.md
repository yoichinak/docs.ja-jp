---
title: DataView の DataRowView コレクションの照会
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 8b6b6c5b9d7157b1279f23770b1d223635252685
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651832"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>DataView の DataRowView コレクションの照会
<xref:System.Data.DataView> は、<xref:System.Data.DataRowView> オブジェクトの列挙可能なコレクションを公開します。 <xref:System.Data.DataRowView> は、<xref:System.Data.DataRow> のカスタマイズされたビューを表し、<xref:System.Data.DataRow> の特定のバージョンをコントロールに表示します。 <xref:System.Data.DataRow> などのコントロールを通じて、<xref:System.Windows.Forms.DataGridView> のバージョンを 1 つだけ表示できます。 <xref:System.Data.DataRow> が <xref:System.Data.DataRowView> の <xref:System.Data.DataRowView.Row%2A> プロパティを使用して公開している <xref:System.Data.DataRowView> にアクセスできます。 <xref:System.Data.DataRowView> を使用して値を表示している場合は、<xref:System.Data.DataView.RowStateFilter%2A> プロパティによって、基になる <xref:System.Data.DataRow> から公開される行バージョンが決まります。 使用して別の行のバージョンにアクセスする方法については、<xref:System.Data.DataRow>を参照してください[行の状態と行バージョン](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。 のコレクション<xref:System.Data.DataRowView>オブジェクトによって公開されている、<xref:System.Data.DataView>は、列挙可能なことができますを使用する[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]それに対してクエリを実行します。  
  
 次の例では、`Product` テーブルに対して赤色の製品を照会し、そのクエリに基づくテーブルを作成します。 このテーブルから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView.RowStateFilter%2A> プロパティに、削除行と変更行を条件とするフィルターを設定します。 次に <xref:System.Data.DataView> を LINQ クエリのソースとして使用し、変更済みおよび削除済みの <xref:System.Data.DataRowView> オブジェクトを <xref:System.Windows.Forms.DataGridView> コントロールにバインドします。  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 次の例では、<xref:System.Windows.Forms.DataGridView> コントロールにバインドされたビューから製品のテーブルを作成します。 <xref:System.Data.DataView> に対して赤色の製品を照会し、並べ替えた結果を <xref:System.Windows.Forms.DataGridView> コントロールにバインドしています。  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>関連項目

- [データ バインディングと LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
