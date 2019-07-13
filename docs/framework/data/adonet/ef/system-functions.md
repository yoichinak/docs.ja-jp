---
title: システム関数
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 135154d2f5e26cdf7f2e41e8ed2b561bb75f377e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879451"
---
# <a name="system-functions"></a>システム関数
.NET Framework Data Provider for SQL Server (SqlClient) には、次のシステム関数が用意されています。  
  
|関数|説明|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|チェックサム値を返します。 `CHECKSUM` は、ハッシュ インデックスの作成に使用します。<br /><br /> **引数**<br /><br /> `value`:A `Boolean`、 `Byte`、 `Int16`、 `Int32`、 `Int64`、 `Single`、 `Decimal`、 `Double`、 `DateTime`、 `String`、 `Binary`、または`Guid`します。 1 つ、2 つ、または 3 つの値を指定できます。<br /><br /> **戻り値**<br /><br /> 指定された式の絶対値。<br /><br /> **例**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|有効桁数が 7 (SQL Server 2008) または 3 (SQL Server 2005) の `DateTime` 値に使用する現在の日付と時刻を SQL Server の内部形式で生成します。<br /><br /> **戻り値**<br /><br /> 現在のシステム日時を `DateTime` として表現した値。<br /><br /> **例**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|現在のユーザーの名前を返します。<br /><br /> **戻り値**<br /><br /> ASCII の `String`。<br /><br /> **例**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|式を表すために必要なバイト数を返します。<br /><br /> **引数**<br /><br /> `expression`:A `Boolean`、 `Byte`、 `Int16`、 `Int32`、 `Int64`、 `Single`、 `Decimal`、 `Double`、 `DateTime`、 `Time`、 `DateTimeOffset`、 `String`、 `Binary`、または`Guid`.<br /><br /> **戻り値**<br /><br /> プロパティのサイズ (`Int32`)。<br /><br /> **例**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|ワークステーション名を返します。<br /><br /> **戻り値**<br /><br /> Unicode の `String`。<br /><br /> **例**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|入力式が有効な日付かどうかを調べます。<br /><br /> **引数**<br /><br /> `expression`:A `Boolean`、 `Byte`、 `Int16`、 `Int32`、 `Int64`、 `Single`、 `Decimal`、 `Double`、 `DateTime`、 `Time`、 `DateTimeOffset`、 `String`、 `Binary`、または`Guid`.<br /><br /> **戻り値**<br /><br /> `Int32`。 入力式が有効な日付である場合は 1 です。 それ以外の場合は 0 です。<br /><br /> **例**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|式が数値型として有効かどうかを調べます。<br /><br /> **引数**<br /><br /> `expression`:A `Boolean`、 `Byte`、 `Int16`、 `Int32`、 `Int64`、 `Single`、 `Decimal`、 `Double`、 `DateTime`、 `Time`、 `DateTimeOffset`、 `String`、 `Binary`、または`Guid`.<br /><br /> **戻り値**<br /><br /> `Int32`。 入力式が有効な日付である場合は 1 です。 それ以外の場合は 0 です。<br /><br /> **例**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Guid 型の一意な値を作成します。<br /><br /> **戻り値**<br /><br /> `Guid`。<br /><br /> **例**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|指定した識別番号から、データベース ユーザー名を返します。<br /><br /> **引数**<br /><br /> `expression`:データベース ユーザーに関連付けられている `Int32` 型の識別番号を指定します。<br /><br /> **戻り値**<br /><br /> Unicode の `String`。<br /><br /> **例**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 SqlClient でサポートされる文字列関数の詳細については、SqlClient プロバイダー マニフェストで指定した SQL Server のバージョンのドキュメントを参照してください。  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[システム関数 Transact SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[システム関数 Transact SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[システム関数 (TRANSACT-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>関連項目

- [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Entity Framework 用 SqlClient 関数](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
