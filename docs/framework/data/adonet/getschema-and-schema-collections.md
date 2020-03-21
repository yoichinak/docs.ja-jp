---
title: GetSchema およびスキーマ コレクション
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: e18c23e9bbec97a64110aba6eb7241761ecece06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149558"
---
# <a name="getschema-and-schema-collections"></a>GetSchema およびスキーマ コレクション
各 .NET Framework マネージ プロバイダーの**接続**クラスは **、GetSchema**メソッドを実装して、現在接続されているデータベースに関するスキーマ情報を取得するために使用され **、GetSchema**メソッドから返されるスキーマ情報は<xref:System.Data.DataTable>、 の形式で取得されます。 **GetSchema**メソッドは、返されるスキーマ コレクションを指定し、返される情報の量を制限するためのオプション のパラメーターを提供するオーバーロードされたメソッドです。  
  
## <a name="specifying-the-schema-collections"></a>スキーマ コレクションの指定  
 **GetSchema**メソッドの最初の省略可能なパラメーターは、文字列として指定されるコレクション名です。 スキーマ コレクションには 2 種類あります。すべてのプロバイダーに共通している一般的なスキーマ コレクションと、各プロバイダーによって固有のスキーマ コレクションです。  
  
 .NET Framework マネージ プロバイダーに対してクエリを実行して、引数を指定しない**GetSchema**メソッドを呼び出すか、スキーマ コレクション名 "MetaDataCollections" を使用して、サポートされているスキーマ コレクションの一覧を確認できます。 これにより、サポートされるスキーマ コレクションの一覧、それぞれがサポートする制限数、および使用する識別子部分の数と共に、<xref:System.Data.DataTable> が返されます。  
  
### <a name="retrieving-schema-collections-example"></a>スキーマ コレクションの取得例  
 次の例では、SQL Server<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A><xref:System.Data.SqlClient.SqlConnection>クラスの .NET Framework データ プロバイダのメソッドを使用して **、AdventureWorks**サンプル データベースに含まれるすべてのテーブルに関するスキーマ情報を取得する方法を示します。  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
   End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
   Console.WriteLine("Press any key to continue.");  
   Console.ReadKey();  
   }  
 }  
  
  private static string GetConnectionString()  
  {  
   // To avoid storing the connection string in your code,  
   // you can retrieve it from a configuration file.  
   return "Data Source=(local);Database=AdventureWorks;" +  
      "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [データベース スキーマ情報の取得](retrieving-database-schema-information.md)
- [ADO.NET の概要](ado-net-overview.md)
