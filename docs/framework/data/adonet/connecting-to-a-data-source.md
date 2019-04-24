---
title: ADO.NET でのデータ ソースへの接続
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: c04624be758e4bc7c8b1981ad6a9dc44430d62b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083713"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET でのデータ ソースへの接続
ADO.NET で使用して、**接続**接続文字列に必要な認証情報を指定して特定のデータ ソースに接続するオブジェクト。 **接続**オブジェクトを使用するデータ ソースの種類に依存します。  
  
  .NET Framework に含まれている各 .NET Framework データ プロバイダーは、<xref:System.Data.Common.DbConnection> オブジェクトを持っています。 .NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbConnection> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlConnection> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcConnection> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleConnection> があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [接続の確立](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 使用する方法について説明します、**接続**オブジェクトをデータ ソースへの接続を確立します。  
  
 [接続イベント](../../../../docs/framework/data/adonet/connection-events.md)  
 使用する方法について説明します、 **InfoMessage**イベント データ ソースから情報メッセージを取得します。  
  
## <a name="see-also"></a>関連項目

- [接続文字列](../../../../docs/framework/data/adonet/connection-strings.md)
- [接続プール](../../../../docs/framework/data/adonet/connection-pooling.md)
- [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
