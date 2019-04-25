---
title: データベース スキーマ情報の取得
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 885d3c9ad61c9099c960ddb0c0f77fa8a98dbefa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133706"
---
# <a name="retrieving-database-schema-information"></a>データベース スキーマ情報の取得
データベースからのスキーマ情報の取得は、スキーマの検出プロセスによって行われます。 スキーマの検出により、マネージ プロバイダーを見つけるとも呼ばれる、データベース スキーマに関する情報を返すことを要求するアプリケーション*メタデータ*、特定のデータベース。 テーブル、列、ストアド プロシージャなどの各種のデータベース スキーマ要素は、スキーマ コレクションを通じて公開されます。 各スキーマ コレクションには、使用されているプロバイダーに固有の各種のスキーマ情報が含まれています。  
  
 .NET Framework マネージ プロバイダーの実装はそれぞれ、 **GetSchema**メソッドで、**接続**クラス、およびから返されるスキーマ情報、 **GetSchema**メソッドは、の形式では、<xref:System.Data.DataTable>します。 **GetSchema**メソッドが戻るには、スキーマ コレクションを指定し、返される情報量を制限するための省略可能なパラメーターを提供するオーバー ロードされたメソッド。  
  
 OLE DB、ODBC、Oracle、および SqlClient の .NET Framework データ プロバイダーの提供、 **GetSchemaTable**の列のメタデータを表す DataTable を返すメソッド、 **DataReader**します。  
  
 .NET Framework Data Provider for OLE DB では、<xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> オブジェクトの <xref:System.Data.OleDb.OleDbConnection> メソッドを使ってスキーマ情報を公開します。 引数として**GetOleDbSchemaTable**は、<xref:System.Data.OleDb.OleDbSchemaGuid>戻るには、スキーマ情報を識別し、これらの制限の配列に列が返されます。 **GetOleDbSchemaTable**を返します、<xref:System.Data.DataTable>要求されたスキーマ情報が設定されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [GetSchema およびスキーマ コレクション](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 について説明します、 **GetSchema**メソッドとそのを使用して取得し、データベースからスキーマ情報を制限する方法。  
  
 スキーマの制限  
 使用できるスキーマの制限について説明します**GetSchema**します。  
  
 [共通のスキーマ コレクション](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 すべての .NET Framework マネージド プロバイダーでサポートされる共通のスキーマ コレクションについて説明します。  
  
 [SQL Server スキーマ コレクション](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 .NET Framework Provider for SQL Server でサポートされるスキーマ コレクションについて説明します。  
  
 [Oracle スキーマ コレクション](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 .NET Framework Provider for Oracle でサポートされるスキーマ コレクションについて説明します。  
  
 [ODBC スキーマ コレクション](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 ODBC ドライバーのスキーマ コレクションについて説明します。  
  
 [OLE DB スキーマ コレクション](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 OLE DB プロバイダーのスキーマ コレクションについて説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.Common.DbConnection>クラス。  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.Odbc.OdbcConnection>クラス。  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.OleDb.OleDbConnection>クラス。  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.OracleClient.OracleConnection>クラス。  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.SqlClient.SqlConnection>クラス。  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.Common.DbDataReader>クラス。  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.Odbc.OdbcDataReader>クラス。  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.OleDb.OleDbDataReader>クラス。  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.OracleClient.OracleDataReader>クラス。  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.SqlClient.SqlDataReader>クラス。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
