---
title: データの並べ替えとフィルター処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 0907aa2a66e1bf51fefc7bed8ea2612cc0c830fa
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203219"
---
# <a name="sorting-and-filtering-data"></a>データの並べ替えとフィルター処理
<xref:System.Data.DataView> には、<xref:System.Data.DataTable> のデータの並べ替えとフィルター処理を行うさまざまな方法が用意されています。  
  
- <xref:System.Data.DataView.Sort%2A> プロパティを使用すれば、1 列または複数列の並べ替え順序を指定し、ASC (昇順) パラメーターと DESC (降順) パラメーターを含めることができます。  
  
- <xref:System.Data.DataView.ApplyDefaultSort%2A> プロパティを使用すると、テーブルの主キー列 (1 列または複数列) に基づいて、昇順の並べ替え順序を自動的に作成できます。 <xref:System.Data.DataView.ApplyDefaultSort%2A>**Sort**プロパティが null 参照または空の文字列の場合、およびテーブルに主キーが定義されている場合にのみ適用されます。  
  
- <xref:System.Data.DataView.RowFilter%2A> プロパティを使用すると、列の値に基づいて行のサブセットを指定できます。 **RowFilter**プロパティの有効な式の詳細については、 <xref:System.Data.DataColumn.Expression%2A> <xref:System.Data.DataColumn>クラスのプロパティの参照情報を参照してください。  
  
     データのサブセットの動的ビューを提供するのではなく、データに対する特定のクエリの結果を返す場合は、 **DataView**のメソッド<xref:System.Data.DataView.Find%2A>また<xref:System.Data.DataView.FindRows%2A>はメソッドを使用して、 **RowFilter**プロパティ。 **RowFilter**プロパティを設定すると、データのインデックスが再構築され、アプリケーションにオーバーヘッドが追加され、パフォーマンスが低下します。 **RowFilter**プロパティは、バインドされたコントロールがフィルター処理された結果を表示するデータバインドアプリケーションで最適に使用されます。 **Find**メソッドと**FindRows**メソッドは、インデックスの再構築を必要とせずに、現在のインデックスを利用します。 **Find**メソッドと**FindRows**メソッドの詳細については、「[行の検索](finding-rows.md)」を参照してください。  
  
- <xref:System.Data.DataView.RowStateFilter%2A> プロパティを使用して、表示する行バージョンを指定できます。 **DataView**は、基になる行の**RowState**に応じて、公開する行バージョンを暗黙的に管理します。 たとえば、 **Rowstatefilter**が DataViewRowState に設定されている場合、 **DataView**は、**現在**の行バージョンがないため、**削除さ**れたすべての行の**元**の行バージョンを公開し**ます**。 **DataRowView**の**RowVersion**プロパティを使用して、公開されている行バージョンを特定できます。  
  
     次の表は、 **DataViewRowState**のオプションを示しています。  
  
    |DataViewRowState のオプション|説明|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**変更** **され**ていない、追加、および**変更**されたすべての行の**現在**の行バージョン。 既定値です。|  
    |**れ**|**追加された**すべての行の**現在**の行バージョン。|  
    |**削除**|**削除された**すべての行の**元**の行バージョン。|  
    |**ModifiedCurrent**|すべての**変更**された行の**現在**の行バージョン。|  
    |**ModifiedOriginal**|**変更**されたすべての行の**元**の行バージョン。|  
    |**None**|行がありません。|  
    |**OriginalRows**|**変更**されていない、**変更** **された、および削除された**すべての行の**元**の行バージョン。|  
    |**Unchanged**|**変更**されていないすべての行の**現在**の行バージョン。|  
  
 行の状態と行のバージョンの詳細については、「[行の状態と](row-states-and-row-versions.md)行のバージョン」を参照してください。  
  
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
- [DataViews](dataviews.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
