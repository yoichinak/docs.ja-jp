---
title: データの並べ替えとフィルター処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 68b2f75681bef6c43b7eb2072d6e9266408ca102
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607180"
---
# <a name="sorting-and-filtering-data"></a>データの並べ替えとフィルター処理
<xref:System.Data.DataView> には、<xref:System.Data.DataTable> のデータの並べ替えとフィルター処理を行うさまざまな方法が用意されています。  
  
- <xref:System.Data.DataView.Sort%2A> プロパティを使用すれば、1 列または複数列の並べ替え順序を指定し、ASC (昇順) パラメーターと DESC (降順) パラメーターを含めることができます。  
  
- <xref:System.Data.DataView.ApplyDefaultSort%2A> プロパティを使用すると、テーブルの主キー列 (1 列または複数列) に基づいて、昇順の並べ替え順序を自動的に作成できます。 <xref:System.Data.DataView.ApplyDefaultSort%2A> 場合にのみ適用されます、**並べ替え**プロパティが null 参照または空の文字列と、テーブルが定義されている主キーを持っている場合。  
  
- <xref:System.Data.DataView.RowFilter%2A> プロパティを使用すると、列の値に基づいて行のサブセットを指定できます。 詳細については、有効な式の**RowFilter**プロパティに関するリファレンス情報を参照してください、<xref:System.Data.DataColumn.Expression%2A>のプロパティ、<xref:System.Data.DataColumn>クラス。  
  
     取得、データのサブセットの動的なビューを提供することではなく、データの特定のクエリの結果を使用する場合、<xref:System.Data.DataView.Find%2A>または<xref:System.Data.DataView.FindRows%2A>のメソッド、 **DataView**最高のパフォーマンスを実現するためには設定、 **RowFilter**プロパティ。 設定、 **RowFilter**プロパティは、アプリケーションにオーバーヘッドを追加し、パフォーマンスが低下は、データのインデックスを再構築します。 **RowFilter**プロパティは、最適な使用データ バインド アプリケーションでバインドされたコントロールがフィルター処理された結果が表示されます。 **検索**と**FindRows**メソッドは、再構築するインデックスを必要とせず、現在のインデックスを活用します。 詳細については、**検索**と**FindRows**メソッドを参照してください[行の検索](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)します。  
  
- <xref:System.Data.DataView.RowStateFilter%2A> プロパティを使用して、表示する行バージョンを指定できます。 **DataView**に応じてを公開する行バージョンを暗黙的に管理、 **RowState**の基になる行のできます。 たとえば場合、 **RowStateFilter**に設定されている**DataViewRowState.Deleted**、 **DataView**公開、**元**の行のバージョンすべて**Deleted**行があるためありません**現在**行バージョン。 使用して、公開される行の行バージョンを指定できます、 **RowVersion**のプロパティ、 **DataRowView**します。  
  
     次の表は、オプションの**DataViewRowState**します。  
  
    |DataViewRowState のオプション|説明|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**現在**行バージョンのすべて**Unchanged**、 **Added**、および**Modified**行。 既定値です。|  
    |**追加**|**現在**行バージョンのすべて**Added**行。|  
    |**削除**|**元**行バージョンのすべて**Deleted**行。|  
    |**ModifiedCurrent**|**現在**行バージョンのすべて**Modified**行。|  
    |**ModifiedOriginal**|**元**行バージョンのすべて**Modified**行。|  
    |**None**|行がありません。|  
    |**OriginalRows**|**元**行バージョンのすべて**Unchanged**、 **Modified**、および**Deleted**行。|  
    |**変更なし**|**現在**行バージョンのすべて**Unchanged**行。|  
  
 行の状態と行のバージョンの詳細については、次を参照してください。[行の状態と行バージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。  
  
 在庫数が標準在庫数以下である製品を、仕入先 ID (supplier ID) で並べ替え、さらに製品名 (product name) で並べ替えたビューを作成するコード サンプルを次に示します。  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
