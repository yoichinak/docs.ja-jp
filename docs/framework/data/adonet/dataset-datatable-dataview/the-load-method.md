---
title: Load メソッド
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: da0695aff9447355b1fc44a033c1b4a1cc224435
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785886"
---
# <a name="the-load-method"></a>Load メソッド
<xref:System.Data.DataTable.Load%2A> メソッドを使用して、データ ソースの行を <xref:System.Data.DataTable> に読み込むことができます。 これはオーバーロードされたメソッドであり、最も単純な形式で、1つのパラメーターである**DataReader**を受け取ります。 この形式では、単に行を含む**DataTable**が読み込まれます。 必要に応じて、 **LoadOption**パラメーターを指定して、データを**DataTable**に追加する方法を制御できます。  
  
 **LoadOption**パラメーターは、 **DataTable**に既にデータ行が含まれている場合に特に便利です。これは、データソースからの受信データをテーブル内の既存のデータと結合する方法を記述するためです。 たとえば、 **PreserveCurrentValues** (既定値) は、行が**DataTable**に**追加さ**れたとしてマークされている場合に、**元**の値または各列がデータソースの一致する行の内容に設定されることを指定します。 **現在**の値は、行が追加されたときに割り当てられた値を保持し、その行の**RowState**は**Changed**に設定されます。  
  
 <xref:System.Data.LoadOption> 列挙値の簡単な説明を次の表に示します。  
  
|LoadOption の値|説明|  
|----------------------|-----------------|  
|**OverwriteRow**|受信した行の**PrimaryKey**値が**DataTable**に既に存在する行と同じ場合、各列の**元**の値と**現在**の値は、受信した行の値に置き換えられ、 **RowState**プロパティはに設定されます。**変更なし**。<br /><br /> **DataTable**にまだ存在しないデータソースからの行は、 **RowState**値が**Unchanged のまま**追加されます。<br /><br /> このオプションを有効にすると、データソースの内容と一致するように**DataTable**の内容が更新されます。|  
|**PreserveCurrentValues (既定値)**|入力方向の行の**PrimaryKey**値が**DataTable**に既に存在する行と同じ場合、**元**の値は受信した行の内容に設定され、**現在**の値は変更されません。<br /><br /> **RowState**が**追加**または**変更**されると、 **[変更済み]** に設定されます。<br /><br /> **RowState**が**削除**された場合、**削除**されたままになります。<br /><br /> **DataTable**にまだ存在しないデータソースからの行が追加され、 **RowState**は**Unchanged**に設定されます。|  
|**UpdateCurrentValues**|受信した行の**PrimaryKey**値が**DataTable**内の既存の行と同じ場合、**現在**の値が**元**の値にコピーされ、**現在**の値が受信した行の内容に設定されます。<br /><br /> **DataTable**の**RowState**が**追加**された場合、 **RowState**は**追加さ**れたままになります。 **変更**または**削除済み**としてマークされた行については、 **RowState**が**変更**されます。<br /><br /> **DataTable**に存在しないデータソースの行が追加され、 **RowState**が**追加**されるように設定されます。|  
  
 次のサンプルでは、 **Load**メソッドを使用して、 **Northwind**データベース内の従業員の誕生日の一覧を表示します。  
  
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
