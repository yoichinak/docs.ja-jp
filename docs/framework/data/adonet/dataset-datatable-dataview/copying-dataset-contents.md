---
title: DataSet の内容のコピー
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: d8a7762c4ec5d650295ca0626180285723549051
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786519"
---
# <a name="copying-dataset-contents"></a>DataSet の内容のコピー
の<xref:System.Data.DataSet>コピーを作成して、元のデータに影響を与えずにデータを操作したり、データ**セット**のデータのサブセットを操作したりすることができます。 **データセット**をコピーするときは、次の操作を実行できます。  
  
- スキーマ、データ、行状態情報、および行バージョンを含む、**データセット**の正確なコピーを作成します。  
  
- 既存の**データセット**のスキーマを含み、変更された行のみを含む**データセット**を作成します。 変更されたすべての行を返すことも、特定の**DataRowState**を指定することもできます。 行の状態の詳細については、「[行の状態と行のバージョン](row-states-and-row-versions.md)」を参照してください。  
  
- 行をコピーせずに、**データセット**のスキーマ (リレーショナル構造) のみをコピーします。 行は、<xref:System.Data.DataTable> を使用して、既存の <xref:System.Data.DataTable.ImportRow%2A> にインポートできます。  
  
 スキーマとデータの両方を含む**データセット**の正確なコピーを作成するに<xref:System.Data.DataSet.Copy%2A>は、**データセット**のメソッドを使用します。 次のコード例は、**データセット**の正確なコピーを作成する方法を示しています。  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 スキーマと、**追加**、**変更**、または**削除**された行を表すデータだけを含むデータ**セット**のコピーを<xref:System.Data.DataSet.GetChanges%2A>作成するには、データ**セット**のメソッドを使用します。 **GetChanges**を呼び出すときに**DataRowState**値を渡すことで、 **GetChanges**を使用して、指定した行の状態の行のみを返すこともできます。 次のコード例は、 **GetChanges**を呼び出すときに**DataRowState**を渡す方法を示しています。  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 スキーマのみを含む**データセット**のコピーを作成するには、 <xref:System.Data.DataSet.Clone%2A> **データセット**のメソッドを使用します。 また、 **DataTable**の**importrow**メソッドを使用して、複製された**データセット**に既存の行を追加することもできます。 **Importrow**は、指定されたテーブルにデータ、行の状態、および行のバージョン情報を追加します。 列名が一致し、データ型が互換性のある型の場合には、列の値だけが追加されます。  
  
 次のコード例では、**データセット**の複製を作成し、元の**データ**セットの行を、**国**の列の値が "ドイツ" になっている顧客の**データセット**の複製の**customers**テーブルに追加します。".  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET の概要](../ado-net-overview.md)
