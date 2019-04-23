---
title: Load メソッド
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 82f840ab7dd26a4888ebf024d696f2c70701eb18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173291"
---
# <a name="the-load-method"></a>Load メソッド
<xref:System.Data.DataTable.Load%2A> メソッドを使用して、データ ソースの行を <xref:System.Data.DataTable> に読み込むことができます。 これは最も単純な形式では、1 つのパラメーターを受け取っているオーバー ロードされたメソッド、 **DataReader**します。 このフォームで、単に読み込む、 **DataTable**行。 必要に応じて、指定、 **LoadOption**にデータを追加する方法を制御するパラメーター、 **DataTable**します。  
  
 **LoadOption**パラメーターの場合に特に便利ですが、 **DataTable**既にデータの行を含む、データと組み合わせて、データ ソースからデータを受信する方法を記述できるため、テーブルの既存の。 たとえば、 **PreserveCurrentValues** (既定値) を指定する場合は、行がマークが**Added**で、 **DataTable**、**元**値列または列の各データ ソースから一致する行の内容に設定されています。 **現在**値は、行が追加されたときに割り当てられた値を保持し、 **RowState**の行に設定されます**Changed**します。  
  
 <xref:System.Data.LoadOption> 列挙値の簡単な説明を次の表に示します。  
  
|LoadOption の値|説明|  
|----------------------|-----------------|  
|**OverwriteRow**|受信した行が同じである場合**PrimaryKey**として既に存在する行の値、 **DataTable**、**元**と**現在**それぞれの値列は、受信した行の値に置き換え、 **RowState**プロパティに設定されて**Unchanged**します。<br /><br /> 行に既に存在しないデータ ソースから、 **DataTable**を使用して追加、 **RowState** @property **Unchanged**。<br /><br /> このオプションが有効の内容を更新、 **DataTable**データ ソースの内容と一致するようにします。|  
|**PreserveCurrentValues (既定値)**|受信した行が同じである場合**PrimaryKey**として既に存在する行の値、 **DataTable**、**元**値は、受信した行、および、の内容に設定されて**現在**値は変更されません。<br /><br /> 場合、 **RowState**は**Added**または**Modified**に設定されている**Modified**します。<br /><br /> 場合、 **RowState**が**Deleted**、まま**Deleted**します。<br /><br /> 行に既に存在しないデータ ソースから、 **DataTable**が追加されると、 **RowState**に設定されている**Unchanged**します。|  
|**UpdateCurrentValues**|受信した行が同じである場合**PrimaryKey**として既に存在する行の値、 **DataTable**、**現在**値をコピー、**元**値、および**現在**値は、受信した行の内容に設定されます。<br /><br /> 場合、 **RowState**で、 **DataTable**が**Added**、 **RowState**まま**Added**します。 としてマークされた行**Modified**または**Deleted**、 **RowState**は**Modified**します。<br /><br /> 行に既に存在しないデータ ソースから、 **DataTable**が追加されると、 **RowState**に設定されている**Added**。|  
  
 次のサンプルは、**ロード**に従業員の誕生日の一覧を表示するメソッド、 **Northwind**データベース。  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a>関連項目

- [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
