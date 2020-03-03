---
title: データベース スキーマ情報の取得
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782729"
---
# <a name="retrieving-database-schema-information"></a>データベース スキーマ情報の取得
データベースからのスキーマ情報の取得は、スキーマの検出プロセスによって行われます。 スキーマ検出を使用すると、アプリケーションは、特定のデータベースのデータベーススキーマ (*メタデータ*とも呼ばれます) に関する情報を検索して返すように要求できます。 テーブル、列、ストアド プロシージャなどの各種のデータベース スキーマ要素は、スキーマ コレクションを通じて公開されます。 各スキーマ コレクションには、使用されているプロバイダーに固有の各種のスキーマ情報が含まれています。  
  
 各 .NET Framework マネージプロバイダーは、 **Connection**クラスに**getschema**メソッドを実装します。また、 **getschema**メソッドから返されるスキーマ情報は、 <xref:System.Data.DataTable>の形式になります。 **GetSchema**メソッドは、返されるスキーマコレクションを指定し、返される情報量を制限するためのオプションのパラメーターを提供する、オーバーロードされたメソッドです。  
  
 OLE DB、ODBC、Oracle、および SqlClient の .NET Framework データプロバイダーには、 **DataReader**の列メタデータを記述する DataTable を返す**getschematable**メソッドが用意されています。  
  
 .NET Framework Data Provider for OLE DB では、<xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> オブジェクトの <xref:System.Data.OleDb.OleDbConnection> メソッドを使ってスキーマ情報を公開します。 引数として、 **getoledbschematable**は、 <xref:System.Data.OleDb.OleDbSchemaGuid>返されるスキーマ情報を識別するを受け取り、返された列に対する制限の配列を取得します。 **Getoledbschematable**は、 <xref:System.Data.DataTable>要求されたスキーマ情報を格納したを返します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [GetSchema およびスキーマ コレクション](getschema-and-schema-collections.md)  
 **GetSchema**メソッドと、それを使用してデータベースからスキーマ情報を取得および制限する方法について説明します。  
  
 スキーマの制限  
 **GetSchema**で使用できるスキーマの制限について説明します。  
  
 [共通のスキーマ コレクション](common-schema-collections.md)  
 すべての .NET Framework マネージド プロバイダーでサポートされる共通のスキーマ コレクションについて説明します。  
  
 [SQL Server スキーマ コレクション](sql-server-schema-collections.md)  
 .NET Framework Provider for SQL Server でサポートされるスキーマ コレクションについて説明します。  
  
 [Oracle スキーマ コレクション](oracle-schema-collections.md)  
 .NET Framework Provider for Oracle でサポートされるスキーマ コレクションについて説明します。  
  
 [ODBC スキーマ コレクション](odbc-schema-collections.md)  
 ODBC ドライバーのスキーマ コレクションについて説明します。  
  
 [OLE DB スキーマ コレクション](ole-db-schema-collections.md)  
 OLE DB プロバイダーのスキーマ コレクションについて説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <xref:System.Data.Common.DbConnection>クラスの**GetSchema**メソッドについて説明します。  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <xref:System.Data.Odbc.OdbcConnection>クラスの**GetSchema**メソッドについて説明します。  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <xref:System.Data.OleDb.OleDbConnection>クラスの**GetSchema**メソッドについて説明します。  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <xref:System.Data.OracleClient.OracleConnection>クラスの**GetSchema**メソッドについて説明します。  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <xref:System.Data.SqlClient.SqlConnection>クラスの**GetSchema**メソッドについて説明します。  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <xref:System.Data.Common.DbDataReader>クラスの**getschematable**メソッドについて説明します。  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <xref:System.Data.Odbc.OdbcDataReader>クラスの**getschematable**メソッドについて説明します。  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <xref:System.Data.OleDb.OleDbDataReader>クラスの**getschematable**メソッドについて説明します。  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <xref:System.Data.OracleClient.OracleDataReader>クラスの**getschematable**メソッドについて説明します。  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <xref:System.Data.SqlClient.SqlDataReader>クラスの**getschematable**メソッドについて説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET でのデータの取得および変更](retrieving-and-modifying-data.md)
- [ADO.NET の概要](ado-net-overview.md)
