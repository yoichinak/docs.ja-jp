---
title: ADO.NET でのデータ ソースへの接続
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786765"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET でのデータ ソースへの接続
ADO.NET**では、接続オブジェクトを**使用して、接続文字列に必要な認証情報を指定することによって、特定のデータソースに接続します。 使用する**接続**オブジェクトは、データソースの種類によって異なります。  
  
 .NET Framework に含まれている各 .NET Framework データ プロバイダーは、<xref:System.Data.Common.DbConnection> オブジェクトを持っています。 .NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbConnection> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlConnection> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcConnection> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleConnection> があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [接続の確立](establishing-the-connection.md)  
 **接続**オブジェクトを使用してデータソースへの接続を確立する方法について説明します。  
  
 [接続イベント](connection-events.md)  
 **インフォメッセージ**イベントを使用して、データソースから情報メッセージを取得する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [接続文字列](connection-strings.md)
- [接続プール](connection-pooling.md)
- [コマンドおよびパラメーター](commands-and-parameters.md)
- [DataAdapter と DataReader](dataadapters-and-datareaders.md)
- [トランザクションと同時実行](transactions-and-concurrency.md)
- [ADO.NET の概要](ado-net-overview.md)
