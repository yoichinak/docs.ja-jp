---
title: 式列の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 8ae8c8e020a3d8ada5bdcd5037187e6f3abd33a4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203826"
---
# <a name="creating-expression-columns"></a>式列の作成
列の式を定義すると、同じ行の他の列値またはテーブル内の複数の行の列値に基づいて計算した値を、その列に格納できます。 評価する式を定義するには、対象の列の <xref:System.Data.DataColumn.Expression%2A> プロパティを使用し、その式で <xref:System.Data.DataColumn.ColumnName%2A> プロパティを使用して他の列を参照します。 式列の <xref:System.Data.DataColumn.DataType%2A> は、その式が返す値に適した型であることが必要です。  
  
 テーブル内の式列で使用できるいくつかの式の種類を次の表に示します。  
  
|式の種類|例|  
|---------------------|-------------|  
|条件式|"Total > = 500"|  
|計算|"UnitPrice * Quantity"|  
|集約|Sum(Price)|  
  
 次の例に示すように、既存の**DataColumn**オブジェクトで<xref:System.Data.DataColumn> **Expression**プロパティを設定するか、コンストラクターに渡す3番目の引数としてプロパティを含めることができます。  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 式は他の式列を参照できます。ただし、2 つの式が相互に参照し合う循環参照の場合は、例外が生成されます。 式の記述に関する規則につい<xref:System.Data.DataColumn.Expression%2A>ては、 **DataColumn**クラスのプロパティを参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataTable スキーマの定義](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
