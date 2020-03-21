---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149441"
---
# <a name="oracle-bfiles"></a>Oracle BFILE
.NET Framework Data Provider for Oracle には、<xref:System.Data.OracleClient.OracleBFile> クラスが含まれています。このクラスは、Oracle <xref:System.Data.OracleClient.OracleType.BFile> データ型で使用されます。  
  
 Oracle **BFILE**データ型は、最大サイズが 4 ギガバイトのバイナリ データへの参照を含む Oracle **LOB**データ型です。 Oracle **BFILE**は、そのデータがサーバーではなくオペレーティング システムの物理ファイルに格納されるという点で、他の Oracle **LOB**データ型とは異なります。 **BFILE**データ型は、データへの読み取り専用アクセスを提供することに注意してください。  
  
 **Lob**データ・タイプと区別する**BFILE**データ・タイプの他の特性は、次のとおりです。  
  
- 非構造化データの保持。  
  
- サーバー側チャンキングのサポート。  
  
- 参照コピーのセマンティクスの使用。 たとえば **、BFILE**でコピー操作を実行すると **、BFILE**ロケーター (ファイルへの参照) のみがコピーされます。 ファイル内のデータはコピーされません。  
  
 **BFILE**データ型は、サイズが大きい LOB を参照するために使用する必要があります。 **BFILE**データ・タイプを使用する場合 **、LOB**データ・タイプと比較して、より多くのクライアント、サーバー、および通信オーバーヘッドが必要になります。 少量のデータを取得するだけでよい場合は **、BFILE**にアクセスする方が効率的です。 オブジェクト全体を取得したい場合は、データベースに常駐する LOB へのアクセスがいっそう効果的です。  
  
 各非 NULL **OracleBFile**オブジェクトは、基になる物理ファイルの場所を定義する 2 つのエンティティに関連付けられます。  
  
1. Oracle DIRECTORY オブジェクト。ファイル システムのディレクトリに対するデータベースのエイリアスです。  
  
2. 基になる物理ファイルのファイル名。このファイルは、DIRECTORY オブジェクトに関連付けられたディレクトリに配置されています。  
  
## <a name="example"></a>例  
 次の C# の例では、Oracle テーブルに**BFILE**を作成し **、OracleBFile**オブジェクトの形式で取得する方法を示します。 この例<xref:System.Data.OracleClient.OracleDataReader>では、オブジェクトと**OracleBFile** **のシーク**および**読み取り**メソッドの使用方法を示します。 このサンプルを使用するには、まず、Oracle サーバー上に "c:\\\bfiles" という名前のディレクトリと "MyFile.jpg" という名前のファイルを作成する必要があります。  
  
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
