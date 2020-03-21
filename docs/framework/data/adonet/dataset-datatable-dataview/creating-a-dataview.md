---
title: DataView の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151339"
---
# <a name="creating-a-dataview"></a>DataView の作成
<xref:System.Data.DataView> は 2 とおりの方法で作成できます。 **DataView**コンストラクタを使用するか、プロパティへの参照を<xref:System.Data.DataTable.DefaultView%2A>作成することができます。 <xref:System.Data.DataTable> **DataView**コンストラクターは空にすることも **、DataTable**を単一の引数として使用することも、フィルター条件、並べ替え条件、および行状態フィルターとともに**DataTable**を使用することもできます。 **DataView**で使用できる追加の引数の詳細については、「[データの並べ替えとフィルター](sorting-and-filtering-data.md)処理」を参照してください。  
  
 **DataView**のインデックスは **、DataView**が作成されるときに、並**べ替え****、RowFilter**、または**RowStateFilter**のいずれかのプロパティが変更されたときに、最もパフォーマンスが高いため **、DataView**を作成するときに、最初の並べ替え順序またはフィルタ条件をコンストラクターの引数として指定することで、最適なパフォーマンスを実現します。 並べ替え条件またはフィルター条件を指定せずに**DataView**を作成し、後で**並べ替え****、RowFilter**、または**RowStateFilter**プロパティを設定すると **、DataView**が作成されたときと、並べ替えまたはフィルターのプロパティのいずれかが変更されたときに、少なくとも 2 回インデックスが作成されます。  
  
 引数を取らないコンストラクタを使用して**DataView**を作成する場合 **、Table**プロパティを設定するまで**DataView**を使用できないことに注意してください。  
  
 次のコード例は **、DataView**コンストラクターを使用して**DataView**を作成する方法を示しています。 **行フィルター**、**並べ替え**列、および**データビュー行状態**は、**データ テーブル**と共に提供されます。  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],
    "Country = 'USA'",
    "ContactName",
    DataViewRowState.CurrentRows);  
```  
  
 次のコード例は、テーブルの**DefaultView**プロパティを使用して **、データ テーブル**の既定の**データ ビュー**への参照を取得する方法を示しています。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [データの並べ替えとフィルター処理](sorting-and-filtering-data.md)
- [DataTables](datatables.md)
- [ADO.NET の概要](../ado-net-overview.md)
