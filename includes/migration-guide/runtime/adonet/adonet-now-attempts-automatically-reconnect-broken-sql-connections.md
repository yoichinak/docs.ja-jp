---
ms.openlocfilehash: 4c65cd62b2d84ef2b852d10a04e5f6ce0cc82d3a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235763"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET では、切断された SQL 接続の再接続が自動的に試行されるようになりました

|   |   |
|---|---|
|説明|.NET Framework 4.5.1 以降、.NET Framework では、切断された SQL 接続の再接続が自動的に試行されます。 通常、これはアプリの安定性を高めますが、再接続時に行動できるよう、接続が失われたことをアプリに認識させる必要があるという極端な状況があります。|
|提案される解決策|互換性の問題からこの機能が望ましくない場合、接続文字列 (または <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) の <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> プロパティを 0 に設定することで無効にできます。|
|スコープ|エッジ|
|Version|4.5.1|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|
