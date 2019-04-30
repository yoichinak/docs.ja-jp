---
title: DataTable へのデータの追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: ec4ad84a39afe21ef77507732e5e0e417d45f3e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034524"
---
# <a name="adding-data-to-a-datatable"></a>DataTable へのデータの追加
<xref:System.Data.DataTable> を作成し、列と制約を使用してそのテーブルの構造を定義した後で、テーブルに新しいデータ行を追加できます。 新しい行を追加するには、新しい変数を <xref:System.Data.DataRow> 型として宣言します。 新しい**DataRow**を呼び出すと、オブジェクトが返されます、<xref:System.Data.DataTable.NewRow%2A>メソッド。 **DataTable**を作成し、 **DataRow**で定義されている、オブジェクトが、テーブルの構造に基づく、<xref:System.Data.DataColumnCollection>します。  
  
 次の例では、呼び出すことによって新しい行を作成する方法、 **NewRow**メソッド。  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 その後でインデックスまたは列名を使用して、新しく追加した行を操作する例を次に示します。  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 新しい行にデータを挿入した後、**追加**メソッドを使用して、行を追加、 <xref:System.Data.DataRowCollection>、次のコードに示す。  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 呼び出すことも、**追加**として型指定された値の配列を渡すことによって新しい行を追加するメソッドを<xref:System.Object>次の例のようにします。  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 として型指定された値の配列を渡す**オブジェクト**を**追加**メソッドは、テーブル内の新しい行を作成し、その列の値をオブジェクト配列内の値に設定します。 配列内の値は、テーブル内での列の順序に基づいて、列に順次的に割り当てられます。  
  
 次の例では、10 個の行を追加、新しく作成した**顧客**テーブル。  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
