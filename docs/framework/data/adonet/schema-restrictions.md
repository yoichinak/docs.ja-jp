---
title: スキーマの制限
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: b5044d39d1dc5d2fa7d2ce691cdda7075fa0e32a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878411"
---
# <a name="schema-restrictions"></a>スキーマの制限
2 番目の省略可能なパラメーター、 **GetSchema**メソッドが返されるスキーマ情報の量を制限するために使用される制限事項、およびに渡される、 **GetSchema**文字列の配列としてメソッド. 配列での位置により、渡すことができる値が決定します。これは、制限の番号に相当します。  
  
 たとえば、次の表は、.NET Framework Data Provider for SQL Server を使用して、"Tables" スキーマ コレクションによりサポートされる制限を示しています。 SQL Server スキーマ コレクションの追加の制限をこのトピックの終わりに示します。  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|テーブル|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>制限値の指定  
 "Tables" スキーマ コレクションの制限の 1 つを使用するには、4 つの要素を使って文字列の配列を作成してから、制限の番号と一致する要素内に値を配置します。 たとえば、テーブルを制限によって返される、 **GetSchema** 、"Sales"スキーマ内のテーブルのみをメソッドに渡す前に"Sales"配列の 2 番目の要素の設定、 **GetSchema**メソッド。  
  
> [!NOTE]
>  `SqlClient` と `OracleClient` の制限のコレクションには、追加の `ParameterName` 列があります。 制限の既定の列は、下位互換性のために存在してはいますが、現在は無視されています。 制限の値を指定する場合、文字列置換ではなく、パラメーター付きのクエリを使って、SQL への注入攻撃のリスクを最小限にする必要があります。  
  
> [!NOTE]
>  配列内の要素数は、指定したスキーマ コレクションでサポートされる制限数以下にする必要があります。そうでない場合、<xref:System.ArgumentException> がスローされます。 制限は最大数よりも小さい場合があります。 指定されていない制限は、null (無制限) と見なされます。  
  
 呼び出すことによってサポートされている制限の一覧を決定する .NET Framework マネージ プロバイダーを照会することができます、 **GetSchema** 「制限」は、制限のスキーマのコレクションの名前を持つメソッド。 これにより、コレクション名の一覧、制限の名前、既定の制限値、および制限の番号と共に、<xref:System.Data.DataTable> が返されます。  
  
### <a name="example"></a>例  
 次の例では、使用する方法、 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 、.NET Framework Data Provider for SQL Server 方法<xref:System.Data.SqlClient.SqlConnection>に関するすべてのテーブルに含まれるスキーマ情報を取得するクラス、 **AdventureWorks**サンプル データベース、および"Sales"スキーマ内のテーブルのみに返される情報を制限します。  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
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
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
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
  
## <a name="sql-server-schema-restrictions"></a>SQL Server スキーマの制限  
 次の表に、SQL Server スキーマ コレクションの制限を示します。  
  
### <a name="users"></a>Users  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|User_Name|@Name|name|1|  
  
### <a name="databases"></a>データベース  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|名前|@Name|名前|1|  
  
### <a name="tables"></a>[テーブル]  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|テーブル|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>列  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|テーブル|@Table|TABLE_NAME|3|  
|Column|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|テーブル|@Table|TABLE_NAME|3|  
|Column|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Views  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|テーブル|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|VIEW_CATALOG|1|  
|Owner|@Owner|VIEW_SCHEMA|2|  
|テーブル|@Table|VIEW_NAME|3|  
|Column|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|SPECIFIC_CATALOG|1|  
|Owner|@Owner|SPECIFIC_SCHEMA|2|  
|名前|@Name|SPECIFIC_NAME|3|  
|パラメーター|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>手順  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|SPECIFIC_CATALOG|1|  
|Owner|@Owner|SPECIFIC_SCHEMA|2|  
|名前|@Name|SPECIFIC_NAME|3|  
|型|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|db_name()|1|  
|Owner|@Owner|user_name()|2|  
|テーブル|@Table|o.name|3|  
|ConstraintName|@ConstraintName|x.name|4|  
|Column|@Column|c.name|5|  
  
### <a name="indexes"></a>Indexes  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|db_name()|1|  
|Owner|@Owner|user_name()|2|  
|テーブル|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|CONSTRAINT_CATALOG|1|  
|Owner|@Owner|CONSTRAINT_SCHEMA|2|  
|テーブル|@Table|TABLE_NAME|3|  
|名前|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 スキーマの制限  
 次の表に、SQL Server 2008 スキーマ コレクションの制限を示します。 これらの制限は、.NET Framework 3.5 SP1 および SQL Server 2008 以降で有効です。 これらの制限は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|テーブル|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|テーブル|@Table|TABLE_NAME|3|  
|Column|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>関連項目

- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
