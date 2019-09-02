---
title: AutoIncrement 列の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205134"
---
# <a name="creating-autoincrement-columns"></a>AutoIncrement 列の作成
列値を一意にするために、新しい行がテーブルに追加されたときに列値が自動的にインクリメントされるように設定できます。 自動インクリメント<xref:System.Data.DataColumn>を作成するには、列<xref:System.Data.DataColumn.AutoIncrement%2A>のプロパティを**true**に設定します。 次<xref:System.Data.DataColumn>に、は、 <xref:System.Data.DataColumn.AutoIncrementSeed%2A>プロパティで定義されている値で始まり、各行が追加されると、列の<xref:System.Data.DataColumn.AutoIncrementStep%2A>プロパティで定義されている値によって AutoIncrement 列の値が増加します。  
  
 **Autoincrement**列の場合は、 **DataColumn**の<xref:System.Data.DataColumn.ReadOnly%2A>プロパティを**true**に設定することをお勧めします。  
  
 値 200 から開始して 3 ずつインクリメントする列を作成する方法を次の例に示します。  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataColumn>
- [DataTable スキーマの定義](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
