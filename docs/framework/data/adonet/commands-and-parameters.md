---
title: コマンドおよびパラメーター
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: a769e8cbd5138e78136df018abe058ac6c568951
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198128"
---
# <a name="commands-and-parameters"></a>コマンドおよびパラメーター
データ ソースへの接続を確立した後、<xref:System.Data.Common.DbCommand> オブジェクトを使用してコマンドを実行し、データ ソースから結果を返すことができます。 コマンドは、使用している .NET Framework データ プロバイダーのいずれかのコマンド コンストラクターで作成できます。 コンストラクターには、データ ソースで実行する SQL ステートメント、<xref:System.Data.Common.DbConnection> オブジェクト、<xref:System.Data.Common.DbTransaction> オブジェクトなど、オプションの引数を渡すことができます。 これらのオブジェクトをコマンドのプロパティとして構成することもできます。 また、<xref:System.Data.Common.DbConnection.CreateCommand%2A> オブジェクトの `DbConnection` メソッドを使用して、特定の接続用のコマンドを作成することもできます。 コマンドによって実行される SQL ステートメントは、<xref:System.Data.Common.DbCommand.CommandText%2A> プロパティを使って構成できます。  
  
 .NET Framework に含まれている各 .NET Framework データ プロバイダーは、`Command` オブジェクトを持ちます。 .NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbCommand> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlCommand> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcCommand> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleCommand> があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [コマンドの実行](../../../../docs/framework/data/adonet/executing-a-command.md)  
 ADO.NET の `Command` オブジェクトと、それを使用してデータ ソースに対してクエリやコマンドを実行する方法について説明します。  
  
 [パラメーターおよびパラメーター データ型の構成](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 `Command` のパラメーターの使用 (方向、データ型、パラメーター構文など) について説明します。  
  
 [CommandBuilder でのコマンドの生成](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 `DataAdapter` に単一テーブルを対象とする SELECT コマンドが割り当てられているときに、コマンド ビルダーを使用して INSERT、UPDATE、DELETE の各コマンドを自動的に生成する方法について説明します。  
  
 [データベースからの単一の値の取得](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 `ExecuteScalar` オブジェクトの `Command` メソッドを使用してデータベース クエリから単一の値を返す方法について説明します。  
  
 [コマンドを使用したデータ変更](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 データ プロバイダーを使用して、ストアド プロシージャまたはデータ定義言語 (DDL) のステートメントを実行する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DataSet、DataTable、および DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [データ ソースへの接続](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
