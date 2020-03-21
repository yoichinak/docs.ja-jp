---
title: DataSet の内容のコピー
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151365"
---
# <a name="copying-dataset-contents"></a>DataSet の内容のコピー
の<xref:System.Data.DataSet>コピーを作成して、元のデータに影響を与えずにデータを操作したり **、DataSet**からデータのサブセットを操作したりできます。 データセットをコピーする場合 **、** 次のことができます。  
  
- スキーマ、データ、行の状態情報、および行のバージョンを含む**DataSet**の正確なコピーを作成します。  
  
- 既存の**DataSet**のスキーマを含む**DataSet**を作成しますが、変更された行のみを作成します。 変更されたすべての行を返すか、特定の**DataRowState**を指定できます。 行の状態の詳細については、「[行の状態」および「行バージョン](row-states-and-row-versions.md)」を参照してください。  
  
- 行をコピーせずに、**データセット**のスキーマまたはリレーショナル構造のみをコピーします。 行は、<xref:System.Data.DataTable> を使用して、既存の <xref:System.Data.DataTable.ImportRow%2A> にインポートできます。  
  
 スキーマとデータの両方を含む**DataSet**の正確なコピーを作成<xref:System.Data.DataSet.Copy%2A>するには、 **DataSet**のメソッドを使用します。 次のコード例は、 **DataSet**の正確なコピーを作成する方法を示しています。  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 スキーマを含む DataSet のコピーを作成し、**追加済み**、**変更済**み、または**削除された**行を表<xref:System.Data.DataSet.GetChanges%2A>すデータのみを含む**DataSet**のコピーを作成するには、 **DataSet**のメソッドを使用します。 また **、GetChanges**を使用して **、GetChanges**を呼び出すときに**DataRowState**値を渡すことで、指定した行の状態の行だけを返すこともできます。 次のコード例は **、GetChanges**を呼び出すときに**DataRowState**を渡す方法を示しています。  
  
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
  
 スキーマのみを含む**DataSet**のコピーを作成するには、 <xref:System.Data.DataSet.Clone%2A> **DataSet**のメソッドを使用します。 DataTable の**ImportRow**メソッドを使用して、複製された**データセット**に既存の**DataTable**行を追加することもできます。 **ImportRow は**、指定されたテーブルにデータ、行の状態、および行バージョン情報を追加します。 列名が一致し、データ型が互換性のある型の場合には、列の値だけが追加されます。  
  
 次のコード例では、**データセット**の複製を作成し、元の**データセット**の行を **、"国の地域**" 列の値が "ドイツ" の顧客の**データセット**の複製物の **[得意先**] テーブルに追加します。  
  
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
