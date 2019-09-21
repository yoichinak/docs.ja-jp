---
title: DataView の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 3e1c31dac458594eee70ddd99469aca7cf63b848
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785478"
---
# <a name="creating-a-dataview"></a>DataView の作成
<xref:System.Data.DataView> は 2 とおりの方法で作成できます。 **DataView**コンストラクターを使用することも、 <xref:System.Data.DataTable.DefaultView%2A> <xref:System.Data.DataTable>のプロパティへの参照を作成することもできます。 **DataView**コンストラクターは空にすることも、 **datatable**を単一の引数として使用することも **、datatable を**フィルター条件、並べ替え条件、および行の状態フィルターと共に取得することもできます。 **DataView**で使用できるその他の引数の詳細については、「[データの並べ替えとフィルター処理](sorting-and-filtering-data.md)」を参照してください。  
  
 **Dataview の**インデックスは、 **dataview**が作成されたときと、 **Sort**、 **RowFilter**、または**rowstatefilter**の各プロパティが変更されたときに、最適なパフォーマンスを実現するために、最初の**DataView**を作成するときに、コンストラクター引数として並べ替え順序またはフィルター条件を指定します。 並べ替えまたはフィルター条件を指定せずに**dataview**を作成した後、 **sort**、 **RowFilter**、または**rowstatefilter**の各プロパティを後で設定すると、インデックスが少なくとも2回作成されます。 **dataview**が並べ替えまたはフィルターのプロパティが変更されたときに作成されます。  
  
 引数を受け取らないコンストラクターを使用して**dataview**を作成した場合、**テーブル**プロパティを設定するまで**dataview**を使用することはできません。  
  
 **Dataview**コンストラクターを使用して**dataview**を作成する方法を次のコード例に示します。 **DataTable**と共に**RowFilter**、 **Sort**列、および**DataViewRowState**が指定されています。  
  
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
  
 次のコード例は、テーブルの**DefaultView**プロパティを使用して、 **DataTable**の既定の**DataView**への参照を取得する方法を示しています。  
  
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
