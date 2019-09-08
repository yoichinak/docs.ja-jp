---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 214140bb8fcf43154b014ea3db609d355a27af7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794634"
---
# <a name="oracle-bfiles"></a>Oracle BFILE
.NET Framework Data Provider for Oracle には、<xref:System.Data.OracleClient.OracleBFile> クラスが含まれています。このクラスは、Oracle <xref:System.Data.OracleClient.OracleType.BFile> データ型で使用されます。  
  
 Oracle **BFILE**データ型は、最大サイズが 4 gb のバイナリデータへの参照を含む oracle **LOB**データ型です。 Oracle **BFILE**は、データがサーバー上ではなくオペレーティングシステムの物理ファイルに格納されるという点で、他の oracle **LOB**データ型とは異なります。 **BFILE**データ型は、データへの読み取り専用アクセスを提供することに注意してください。  
  
 **LOB**データ型と区別する、 **BFILE**データ型のその他の特性は次のとおりです。  
  
- 非構造化データの保持。  
  
- サーバー側チャンキングのサポート。  
  
- 参照コピーのセマンティクスの使用。 たとえば、 **bfile**に対してコピー操作を実行すると、ファイルへの参照である**bfile**ロケーターだけがコピーされます。 ファイル内のデータはコピーされません。  
  
 **BFILE**データ型は、サイズが大きい lob を参照するために使用する必要があります。したがって、データベースに格納するのは現実的ではありません。 **LOB**データ型と比較して、 **BFILE**データ型を使用する場合は、クライアント、サーバー、および通信のオーバーヘッドが増加します。 少量のデータだけを取得する必要がある場合は、 **BFILE**にアクセスする方が効率的です。 オブジェクト全体を取得したい場合は、データベースに常駐する LOB へのアクセスがいっそう効果的です。  
  
 NULL 以外の各**OracleBFile**オブジェクトは、基になる物理ファイルの場所を定義する2つのエンティティに関連付けられています。  
  
1. Oracle DIRECTORY オブジェクト。ファイル システムのディレクトリに対するデータベースのエイリアスです。  
  
2. 基になる物理ファイルのファイル名。このファイルは、DIRECTORY オブジェクトに関連付けられたディレクトリに配置されています。  
  
## <a name="example"></a>例  
 次C#の例では、Oracle テーブルで**BFILE**を作成し、 **OracleBFile**オブジェクトの形式で取得する方法を示します。 この例では、 <xref:System.Data.OracleClient.OracleDataReader>オブジェクトと**OracleBFile** **Seek**メソッドと**Read**メソッドを使用する方法を示します。 このサンプルを使用するには、まず、"c:\\\bfiles" という名前のディレクトリを作成し、Oracle サーバーに "myfile.txt" という名前のファイルを作成する必要があることに注意してください。  
  
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

- [Oracle および ADO.NET](oracle-and-adonet.md)
- [ADO.NET の概要](ado-net-overview.md)
