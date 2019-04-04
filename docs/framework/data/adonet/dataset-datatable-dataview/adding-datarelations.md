---
title: DataRelation の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 9843d5231f6ed95290af6e6d2adaa384f8b47dd7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509507"
---
# <a name="adding-datarelations"></a>DataRelation の追加
複数の <xref:System.Data.DataSet> オブジェクトを含む <xref:System.Data.DataTable> では、<xref:System.Data.DataRelation> オブジェクトを使用して 1 つのテーブルを別のテーブルに関連付けたり、テーブル間を移動したり、関連付けたテーブルから子または親の行を戻したりできます。  
  
 作成に必要な引数を**DataRelation**の名前は、 **DataRelation**作成されると、1 つまたは複数の配列<xref:System.Data.DataColumn>親と子として機能する列への参照リレーションシップ内の列。 作成した後、 **DataRelation**テーブル間を移動して、値を取得するに使用することができます。  
  
 追加する、 **DataRelation**を<xref:System.Data.DataSet>追加すると、既定では、<xref:System.Data.UniqueConstraint>親テーブルに、<xref:System.Data.ForeignKeyConstraint>子テーブルにします。 これらの既定の制約の詳細については、[DataTable の制約](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)を参照してください。  
  
 次のコード例を作成、 **DataRelation**を使用して 2 つ<xref:System.Data.DataTable>内のオブジェクト、<xref:System.Data.DataSet>します。 各<xref:System.Data.DataTable>という名前の列を含む**CustID**、2 つの間のリンクとして機能する<xref:System.Data.DataTable>オブジェクト。 例では、1 つを追加します。 **DataRelation**を、**リレーション**のコレクション、<xref:System.Data.DataSet>します。 例では、最初の引数の名前を指定する、 **DataRelation**作成中です。 2 番目の引数は、親を設定します。 **DataColumn** 3 番目の引数、子の設定と**DataColumn**します。  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 A **DataRelation**もが、**入れ子になった**プロパティに設定すると**true**、親テーブルから、関連する行の入れ子にする子テーブルから行が、使用して XML 要素として書き込まれるときに<xref:System.Data.DataSet.WriteXml%2A>します。 詳しくは、「[DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
