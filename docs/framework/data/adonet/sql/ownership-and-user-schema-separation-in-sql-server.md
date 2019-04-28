---
title: SQL Server における所有権とユーザーとスキーマの分離
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: b56a2c6f1211a11d2aa55de0cc101f6b90f7f83d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646060"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>SQL Server における所有権とユーザーとスキーマの分離
オブジェクトの所有者は、それを管理するための取り消し不可能な権限を持ちます。これは SQL Server のセキュリティの核となる概念です。 オブジェクトの所有者から権限を削除することはできません。また、特定のユーザーがデータベース内のオブジェクトを所有しているときに、そのユーザーをデータベースから削除することもできません。  
  
## <a name="user-schema-separation"></a>ユーザーとスキーマの分離  
 ユーザーとスキーマの分離により、データベース オブジェクトの権限をより柔軟に管理できるようになりました。 A*スキーマ*は個別の名前空間をグループ オブジェクトにできるデータベース オブジェクトの名前付きコンテナーです。 たとえば、AdventureWorks サンプル データベースには、Production、Sales、および HumanResources というスキーマが格納されています。  
  
 オブジェクトを参照する 4 つの部分から成る命名構文では、スキーマ名が指定されます。  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>スキーマの所有者と権限  
 スキーマは任意のデータベース プリンシパルが所有できるほか、1 つのプリンシパルが複数のスキーマを所有することもできます。 スキーマにはセキュリティ ルールを適用できます。適用されたセキュリティ ルールは、そのスキーマのすべてのオブジェクトによって継承されます。 スキーマに対してアクセス権限を設定すると、そのスキーマに追加された新しいオブジェクトにこれらの権限が自動的に適用されます。 ユーザーに既定のスキーマを割り当て、複数のデータベース ユーザーでその同じスキーマを共有できます。  
  
 既定では、開発者がスキーマにオブジェクトを作成した場合、そのオブジェクトは、開発者ではなく、そのスキーマを所有するセキュリティ プリンシパルによって所有されることになります。 オブジェクトの所有権は、Transact-SQL ステートメント ALTER AUTHORIZATION で転送できます。 1 つのスキーマに対し、それぞれ異なるユーザーによって所有されたオブジェクトを追加することもできます。そうすることで、スキーマそのものに割り当てるよりも権限を細かく管理できますが、権限の管理が煩雑になるため、この方法はお勧めできません。 オブジェクトはスキーマ間で移動できるほか、プリンシパル間でスキーマの所有権を転送することもできます。 データベース ユーザーを削除してもスキーマには影響しません。  
  
### <a name="built-in-schemas"></a>組み込みスキーマ  
 SQL Server には、組み込みのデータベース ユーザーおよびロールと同じ名前を持った 10 個の定義済みスキーマが付属しています。 これらは主に下位互換性を確保するために存在します。 固定データベース ロールと同じ名前のスキーマは、不要であれば削除してもかまいません。 次のスキーマを削除することはできません。  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 これらを model データベースから削除した場合、新しいデータベースにはこれらのスキーマが存在しなくなります。  
  
> [!NOTE]
>  `sys` スキーマおよび `INFORMATION_SCHEMA` スキーマは、システム オブジェクト用に予約されています。 これらのスキーマにオブジェクトを作成することはできません。また、これらのスキーマを削除することもできません。  
  
#### <a name="the-dbo-schema"></a>dbo スキーマ  
 `dbo` スキーマは、新しく作成されたデータベースに使用される既定のスキーマです。 `dbo` スキーマは、`dbo` ユーザー アカウントによって所有されます。 既定では、Transact-SQL コマンド CREATE USER で作成されたユーザーには、`dbo` が既定のスキーマとして割り当てられます。  
  
 `dbo` スキーマが割り当てられたユーザーは、`dbo` ユーザー アカウントの権限を継承しません。 スキーマの権限はユーザーによって継承されるのではなく、そのスキーマに含まれたデータベース オブジェクトによって継承されます。  
  
> [!NOTE]
>  1 部構成の名前を使用してデータベース オブジェクトを参照すると、まずユーザーの既定のスキーマが検索されます。 そこで目的のオブジェクトが見つからなかった場合は、`dbo` スキーマ内が検索されます。 `dbo` スキーマ内にオブジェクトが見つからなかった場合は、エラーが返されます。  
  
## <a name="external-resources"></a>外部リソース  
 オブジェクトの所有権とスキーマの詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[ユーザーとスキーマの分離](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))|ユーザーとスキーマの分離によって導入された変更について説明します。 新しい動作とそれが所有権、カタログ ビュー、および権限に与える影響を取り上げています。|  
  
## <a name="see-also"></a>関連項目

- [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server におけるアプリケーション セキュリティのシナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server での認証](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [SQL Server のサーバー ロールとデータベース ロール](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [SQL Server の承認とアクセス許可](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
