---
title: DataSet の内容のコピー
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: 29afeb84498f2b1d000940ddc28545602a44d408
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626150"
---
# <a name="copying-dataset-contents"></a>DataSet の内容のコピー
コピーを作成することができます、<xref:System.Data.DataSet>元のデータに影響を与えずにデータを操作したり、作業するためのデータのサブセットを**データセット**。 コピーするときに、**データセット**を実行できます。  
  
- 正確なコピーを作成、**データセット**(スキーマ、データ、行状態情報、行のバージョンなど)。  
  
- 作成、**データセット**、既存のスキーマを格納している**データセット**、変更された行だけです。 変更されているすべての行を返すか、特定の指定**DataRowState**します。 行の状態の詳細については、次を参照してください。[行の状態と行バージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。  
  
- スキーマ、またはリレーショナル構造のコピー、**データセット**のみ、すべての行をコピーすることがなく。 行は、<xref:System.Data.DataTable> を使用して、既存の <xref:System.Data.DataTable.ImportRow%2A> にインポートできます。  
  
 正確なコピーを作成する、**データセット**スキーマとデータの両方を含む、使用、<xref:System.Data.DataSet.Copy%2A>のメソッド、**データセット**します。 次のコード例の完全なコピーを作成する方法を示しています、**データセット**します。  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 コピーを作成する、**データセット**を含むスキーマとのみ、データを表す**Added**、 **Modified**、または**Deleted**行を使用して、<xref:System.Data.DataSet.GetChanges%2A>のメソッド、**データセット**します。 使用することも**GetChanges**を渡すことによって、指定した行の状態を持つ行だけを返す、 **DataRowState**値の呼び出し時に**GetChanges**します。 次のコード例に渡す方法を示しています、 **DataRowState**を呼び出すときに**GetChanges**します。  
  
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
  
 コピーを作成する、**データセット**だけスキーマを含む、使用、<xref:System.Data.DataSet.Clone%2A>のメソッド、**データセット**します。 複製されたに既存の行を追加することもできます。**データセット**を使用して、 **ImportRow**のメソッド、 **DataTable**します。 **ImportRow**データ、行の状態、および行のバージョン情報を指定したテーブルに追加します。 列名が一致し、データ型が互換性のある型の場合には、列の値だけが追加されます。  
  
 次のコード例のクローンを作成する、**データセット**し、元の行を追加**データセット**を**顧客**テーブルに、**データセット**複製をお客様の場所、 **CountryRegion**列は、"Germany"の値を持ちます。  
  
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
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
