---
title: DataRelation の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: fde1e2ace09e31234d199876ae7f063e01e7a7e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203969"
---
# <a name="adding-datarelations"></a>DataRelation の追加
複数の <xref:System.Data.DataSet> オブジェクトを含む <xref:System.Data.DataTable> では、<xref:System.Data.DataRelation> オブジェクトを使用して 1 つのテーブルを別のテーブルに関連付けたり、テーブル間を移動したり、関連付けたテーブルから子または親の行を戻したりできます。  
  
 **Datarelation**を作成するために必要な引数は、作成する**datarelation**の名前と、リレーションシップの親列および<xref:System.Data.DataColumn>子列として機能する列への1つ以上の参照の配列です。 **DataRelation**を作成したら、それを使用してテーブル間を移動したり、値を取得したりできます。  
  
 <xref:System.Data.UniqueConstraint> <xref:System.Data.ForeignKeyConstraint>に<xref:System.Data.DataSet> **DataRelation**を追加すると、既定では、親テーブルへの、および子テーブルへのが追加されます。 これらの既定の制約の詳細については、「 [DataTable の制約](datatable-constraints.md)」を参照してください。  
  
 次のコード例では、 <xref:System.Data.DataSet>で 2 <xref:System.Data.DataTable>つのオブジェクトを使用して**DataRelation**を作成します。 各<xref:System.Data.DataTable>には、2つ<xref:System.Data.DataTable>のオブジェクト間のリンクとして機能する CustID という名前の列が含まれています。 この例では、 <xref:System.Data.DataSet>の**リレーション**コレクションに単一の**DataRelation**を追加します。 この例の最初の引数では、作成する**DataRelation**の名前を指定します。 2番目の引数は親**datacolumn**を設定し、3番目の引数は子**datacolumn**を設定します。  
  
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
  
 **DataRelation**には、**入れ子になっ**たプロパティもあります。 **true**に設定すると、を使用<xref:System.Data.DataSet.WriteXml%2A>して XML 要素として書き込まれるときに、子テーブルの行が親テーブルの関連付けられた行に入れ子になります。 詳しくは、「[DataSet での XML の使用](using-xml-in-a-dataset.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
