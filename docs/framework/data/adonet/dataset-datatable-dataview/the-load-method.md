---
title: Load メソッド
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150728"
---
# <a name="the-load-method"></a>Load メソッド
<xref:System.Data.DataTable.Load%2A> メソッドを使用して、データ ソースの行を <xref:System.Data.DataTable> に読み込むことができます。 これは、最も単純な形式で、単一のパラメーター **DataReader**を受け取るオーバーロードされたメソッドです。 このフォームでは、単に行を**含む DataTable を**読み込みます。 必要に応じて、データを**DataTable**に追加する方法を制御する**LoadOption**パラメーターを指定できます。  
  
 **LoadOption**パラメーターは、データ ソースからの入力データとテーブル内の既存のデータを結合する方法を記述するため **、DataTable**に既にデータ行が含まれている場合に特に便利です。 たとえば **、PreserveCurrentValues** (既定値) では、行が**DataTable**で**追加**済みとしてマークされている場合、**元**の値または各列がデータ ソースの一致する行の内容に設定されるように指定します。 **Current**値は、行が追加されたときに割り当てられた値を保持し、行の**RowState**が**変更**に設定されます。  
  
 <xref:System.Data.LoadOption> 列挙値の簡単な説明を次の表に示します。  
  
|LoadOption の値|説明|  
|----------------------|-----------------|  
|**OverwriteRow**|受信行が**DataTable**内の行と同じ**主キー**値を持つ場合、各列の**元**の値と**現在**の値は、入力行の値に置き換えられ **、RowState**プロパティは**Unchanged**に設定されます。<br /><br /> データ ソースの行のうち、**データ テーブル**に存在しない行は **、RowState**値が **[未変更]** の値で追加されます。<br /><br /> このオプションは、データ ソースの内容と一致するように**DataTable**の内容を更新します。|  
|**PreserveCurrentValues (既定値)**|受信行が**DataTable**内の行と同じ**主キー**値を持つ場合、**元**の値は受信行の内容に設定され、**現在**の値は変更されません。<br /><br /> **RowState**が **[追加]** または **[変更済み**] の場合は、**変更済**みに設定されます。<br /><br /> **RowState**が**削除された**場合は、**削除された**ままになります。<br /><br /> データ ソースの行が追加され、**データ テーブル**に存在しない行が追加され **、RowState**が**未変更**に設定されます。|  
|**UpdateCurrentValues**|受信行が**DataTable**内の既に存在する行と同じ**主キー**値を持つ場合 **、現在**の値は**元**の値にコピーされ、**現在**の値は、受信行の内容に設定されます。<br /><br /> **データ テーブル**の**RowState**が**追加**された場合 **、RowState**は**追加された**ままになります。 **更新または****削除済**みとしてマークされた行の**場合、RowState**は**変更済み**になります。<br /><br /> データ ソースの行が追加され、**データ テーブル**に存在しない、 **RowState**が**追加に**設定されます。|  
  
 次のサンプルでは **、Load**メソッドを使用して **、Northwind**データベース内の従業員の誕生日の一覧を表示します。  
  
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

- [DataTable 内のデータの操作](manipulating-data-in-a-datatable.md)
- [ADO.NET の概要](../ado-net-overview.md)
