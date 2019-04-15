---
title: DataView の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 05122f7c980c4b7dfdb27eec73464a4f0556ba99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096681"
---
# <a name="creating-a-dataview"></a>DataView の作成
<xref:System.Data.DataView> は 2 とおりの方法で作成できます。 使用することができます、 **DataView**への参照を作成できますコンス トラクター、または、<xref:System.Data.DataTable.DefaultView%2A>のプロパティ、<xref:System.Data.DataTable>します。 **DataView**コンス トラクターは空、またはいずれかがかかることができます、 **DataTable**引数を 1 つとして、または**DataTable**フィルター条件、並べ替え条件、および行と共に状態フィルター。 使用する追加の引数の詳細については、 **DataView**を参照してください[並べ替えとフィルター データ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)します。  
  
 のインデックス、 **DataView**ときにも、構築、 **DataView**が作成されるときのいずれかと、**並べ替え**、 **RowFilter**、または**RowStateFilter**プロパティが変更されると、任意の最初の並べ替え順序を指定するか、作成するときに、コンス トラクター引数としてフィルタ リング条件によって最適なパフォーマンスを実現し、 **DataView**します。 作成、 **DataView**並べ替えまたはフィルター条件を指定しを設定せず、**並べ替え**、 **RowFilter**、または**RowStateFilter**プロパティが、その後、インデックスの構築には少なくとも 2 回: したらときに、 **DataView**が作成し、もう一度、並べ替えまたはフィルターのプロパティのいずれかが変更された日時。  
  
 作成する場合、 **DataView**を任意の引数を受け取らないコンス トラクターを使用することができなくを使用する、 **DataView**を設定するまで、**テーブル**プロパティ.  
  
 次のコード例は、作成する方法を示します、 **DataView**を使用して、 **DataView**コンス トラクター。 A **RowFilter**、**並べ替え**列、および**DataViewRowState**に沿ってで提供されている、 **DataTable**します。  
  
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
  
 次のコード例は、既定値への参照を取得する方法を示します**DataView**の**DataTable**を使用して、 **DefaultView**テーブルのプロパティ。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [データの並べ替えとフィルター処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
