---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 2d7db741cea5421b2391588c0479f44e2b478ca3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626421"
---
# <a name="oracle-bfiles"></a>Oracle BFILE
.NET Framework Data Provider for Oracle には、<xref:System.Data.OracleClient.OracleBFile> クラスが含まれています。このクラスは、Oracle <xref:System.Data.OracleClient.OracleType.BFile> データ型で使用されます。  
  
 Oracle **BFILE**データ型は、Oracle **LOB** 4 ギガバイトの最大サイズのバイナリ データへの参照を含むデータ型。 Oracle **BFILE**他の Oracle とは異なります**LOB**データ型の代わりに、オペレーティング システムで、サーバー上の物理ファイル内のデータが格納されていることにします。 なお、 **BFILE**データ型がデータに読み取り専用アクセスを提供します。  
  
 その他の特性、 **BFILE**から区別するためのデータ型、 **LOB**データ型はできることです。  
  
- 非構造化データの保持。  
  
- サーバー側チャンキングのサポート。  
  
- 参照コピーのセマンティクスの使用。 コピー操作を実行する場合など、 **BFILE**、のみ、 **BFILE** (つまり、ファイルへの参照) ロケーターをコピーします。 ファイル内のデータはコピーされません。  
  
 **BFILE**サイズが大きい Lob を参照するデータ型を使用する必要があり、そのため、データベースに格納する実用的ではありません。 複数のクライアント、サーバー、および通信のオーバーヘッドを必要とを使用して、 **BFILE**と比較して、データ型、 **LOB**データ型。 アクセスする方が効率的です、 **BFILE**のみ少量のデータを取得する必要がある場合。 オブジェクト全体を取得したい場合は、データベースに常駐する LOB へのアクセスがいっそう効果的です。  
  
 各 NULL でない**OracleBFile**オブジェクトが基になる物理ファイルの場所を定義する 2 つのエンティティに関連付けられています。  
  
1. Oracle DIRECTORY オブジェクト。ファイル システムのディレクトリに対するデータベースのエイリアスです。  
  
2. 基になる物理ファイルのファイル名。このファイルは、DIRECTORY オブジェクトに関連付けられたディレクトリに配置されています。  
  
## <a name="example"></a>例  
 C# の例を次に示しますを作成する方法、 **BFILE** 、Oracle のテーブルし、の形式で取得し、 **OracleBFile**オブジェクト。 この例で、<xref:System.Data.OracleClient.OracleDataReader>オブジェクトと**OracleBFile** **シーク**と**読み取り**メソッド。 このサンプルを使用するために作成することする必要がありますまずという名前のディレクトリ"c:\\\bfiles"と"MyFile.jpg"をという名前を Oracle サーバー上のファイル。  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a>関連項目

- [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
