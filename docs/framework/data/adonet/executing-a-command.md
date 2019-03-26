---
title: コマンドの実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: 4081558f9ea6a1bc258ab4cbebe6c2f72ee2c60c
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903387"
---
# <a name="executing-a-command"></a>コマンドの実行
.NET Framework に含まれている各 .NET Framework データ プロバイダーは、それぞれ <xref:System.Data.Common.DbCommand> を継承する固有のコマンド オブジェクトを持ちます。 .NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbCommand> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlCommand> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcCommand> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleCommand> があります。 次の表に示したように、各オブジェクトはコマンドを実行するための各種のメソッドを公開しており、コマンドの種類と適切な戻り値に基づいて使い分けることになります。  
  
|コマンド|戻り値|  
|-------------|------------------|  
|`ExecuteReader`|`DataReader` オブジェクトを返します。|  
|`ExecuteScalar`|単一のスカラー値を返します。|  
|`ExecuteNonQuery`|行を一切返さないコマンドを実行します。|  
|`ExecuteXMLReader`|<xref:System.Xml.XmlReader> を返します。 `SqlCommand` オブジェクトでのみ使用できます。|  
  
 厳密に型指定された各コマンド オブジェクトは、次の表に示す <xref:System.Data.CommandType> 列挙値をサポートしています。これらの列挙値を使用してコマンド文字列の解釈方法を指定できます。  
  
|CommandType|説明|  
|-----------------|-----------------|  
|`Text`|データ ソース側で実行されるステートメントを定義する SQL コマンド。|  
|`StoredProcedure`|ストアド プロシージャの名前。 呼び出す `Parameters` メソッドに関係なく、コマンドの `Execute` プロパティを使用して入力パラメーターと出力パラメーターにアクセスし、戻り値を取得できます。 `ExecuteReader` を使用した場合は、`DataReader` を閉じるまで戻り値および出力パラメーターにアクセスすることはできません。|  
|`TableDirect`|テーブルの名前。|  
  
## <a name="example"></a>例  
 <xref:System.Data.SqlClient.SqlCommand> オブジェクトを作成し、そのプロパティを設定することによってストアド プロシージャを実行するコード サンプルを次に示します。 ストアド プロシージャへの入力パラメーターは、<xref:System.Data.SqlClient.SqlParameter> オブジェクトを使って指定します。 このコマンドを <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> メソッドで実行し、<xref:System.Data.SqlClient.SqlDataReader> からの出力をコンソール ウィンドウに表示します。  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>コマンドのトラブルシューティング  
 .NET Framework Data Provider for SQL Server には、失敗したコマンド実行に関連して断続的に発生する問題を検出できるパフォーマンス カウンターが追加されています。 詳細については、[パフォーマンス カウンター](../../../../docs/framework/data/adonet/performance-counters.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET の概要](ado-net-overview.md)
