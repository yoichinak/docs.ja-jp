---
title: データ ソースのデータの更新
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 0926e3c6513a698ae47b9983d0e6ad195394a4df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780615"
---
# <a name="updating-data-in-a-data-source"></a>データ ソースのデータの更新
データを変更する SQL ステートメント (INSERT、UPDATE、DELETE など) は行を返しません。 同様に、多くのストアド プロシージャは、アクションを実行しても行を返しません。 行を返さないコマンドを実行するには、適切な SQL コマンドと**接続**(必要な**パラメーター**を含む) を指定して**command**オブジェクトを作成します。 **Command オブジェクトの** **ExecuteNonQuery**メソッドを使用してコマンドを実行します。  
  
 **ExecuteNonQuery**メソッドは、実行されたステートメントまたはストアドプロシージャの影響を受ける行の数を表す整数を返します。 複数のステートメントが実行された場合は、実行された各ステートメントの影響を受けたレコードの合計を示す値が返されます。  
  
## <a name="example"></a>例  
 次のコード例では、INSERT ステートメントを実行して、 **ExecuteNonQuery**を使用してデータベースにレコードを挿入します。  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 次のコード例では、[カタログ操作の実行](performing-catalog-operations.md)時にサンプルコードによって作成されたストアドプロシージャを実行します。 ストアドプロシージャによって返される行は存在しないため、 **ExecuteNonQuery**メソッドが使用されますが、ストアドプロシージャは入力パラメーターを受け取り、出力パラメーターと戻り値を返します。  
  
 オブジェクトの場合は、最初に**パラメーター**コレクションに戻りパラメーターを追加する必要があります。 <xref:System.Data.OleDb.OleDbCommand>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a>関連項目

- [コマンドを使用したデータ変更](using-commands-to-modify-data.md)
- [DataAdapter によるデータ ソースの更新](updating-data-sources-with-dataadapters.md)
- [コマンドおよびパラメーター](commands-and-parameters.md)
- [ADO.NET の概要](ado-net-overview.md)
