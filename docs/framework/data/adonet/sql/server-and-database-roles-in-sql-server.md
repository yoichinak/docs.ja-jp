---
title: SQL Server のサーバー ロールとデータベース ロール
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: 97ad04b1d081e5635104bdadb2d1a54402ffcca2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961102"
---
# <a name="server-and-database-roles-in-sql-server"></a>SQL Server のサーバー ロールとデータベース ロール
SQL Server では、すべてのバージョンで、個々のユーザーではなくロール (つまり、ユーザーのグループ) に対して権限を割り当てることのできるロール ベースのセキュリティが使用されています。 固定サーバー ロールおよび固定データベース ロールには、固定された一連の権限が割り当てられています。  
  
## <a name="fixed-server-roles"></a>固定サーバー ロール  
 固定サーバー ロールは、固定された一連の権限とサーバー規模のスコープを持ちます。 SQL Server の管理を目的としており、このロールに割り当てられた権限を変更することはできません。 固定サーバー ロールには、データベースにユーザー アカウントがなくても、ログインを割り当てることができます。  
  
> [!IMPORTANT]
> `sysadmin` 固定サーバー ロールは他のすべてのロールを内包し、無制限のスコープを持ちます。 本当に信頼できる場合以外は、このロールにプリンシパルを追加することは避けてください。 `sysadmin` ロールのメンバーには、サーバーのすべてのデータベースおよびリソースに対する取り消し不可能な管理特権が与えられます。  
  
 固定サーバー ロールに追加するユーザーは慎重に選ぶ必要があります。 たとえば、`bulkadmin` ロールでは、ユーザーがローカル ファイルの内容をテーブルに挿入できるため、データの整合性が損なわれる可能性があります。 固定サーバーロールと権限の完全な一覧については、「SQL Server オンラインブック」を参照してください。  
  
## <a name="fixed-database-roles"></a>固定データベース ロール  
 固定データベース ロールには、権限のグループを簡単に管理できるように、あらかじめ定義された一連の権限が割り当てられています。 `db_owner` ロールのメンバーは、データベースに対するすべての構成作業とメンテナンス作業を実行できます。  
  
 SQL Server の定義済みロールの詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[サーバーレベルのロール](/sql/relational-databases/security/authentication-access/server-level-roles)|固定サーバーロールと、それらに関連付けられた SQL Server の権限について説明します。|  
|[データベースレベルのロール](/sql/relational-databases/security/authentication-access/database-level-roles)|固定データベース ロールおよびそれに関連付けられている権限について説明します。|  
  
## <a name="database-roles-and-users"></a>データベース ロールおよびユーザー  
 データベース ユーザー アカウントはデータベース オブジェクトを扱う関係上、ログインにマップされている必要があります。 データベース ユーザーをデータベース ロールに追加すると、そのロールに関連付けられたすべての権限セットが継承されます。 すべての権限を付与できます。  
  
 アプリケーションのセキュリティを計画する際は、`public` ロール、`dbo` ユーザー アカウント、および `guest` アカウントも考慮する必要があります。  
  
### <a name="the-public-role"></a>public ロール  
 `public` ロールは、システム データベースを含め、すべてのデータベースに存在します。 このロールは削除できません。また、ユーザーを追加したり削除したりすることもできません。 他のすべてのユーザーおよびロールは既定で `public` ロールに所属するため、`public` ロールに付与された権限を継承します。 `public` には、すべてのユーザーに割り当てる必要のある権限だけを付与してください。  
  
### <a name="the-dbo-user-account"></a>dbo ユーザー アカウント  
 `dbo` (データベース所有者) は、データベースのすべてのアクティビティを実行する暗黙権限を持ったユーザー アカウントです。 `sysadmin` 固定サーバー ロールのメンバーは、自動的に `dbo` にマップされます。  
  
> [!NOTE]
> `dbo`は、「 [SQL Server での所有権とユーザースキーマの分離](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)」で説明されているように、スキーマの名前でもあります。  
  
 `dbo` ユーザー アカウントは、よく `db_owner` 固定データベース ロールと混同されます。 `db_owner` のスコープがサーバー全体であるのに対し、`sysadmin` のスコープはデータベースです。 `db_owner` ロールのメンバーであるからといって、`dbo` のユーザー権限があるとは限りません。  
  
### <a name="the-guest-user-account"></a>guest ユーザー アカウント  
 認証されて SQL Server のインスタンスへのログインが許可されたユーザーが、その後、データベースにアクセスするためには各データベースに別個のユーザー アカウントが存在している必要があります。 データベースごとにユーザー アカウントが要求されるため、SQL Server のインスタンスに接続したとしても、ユーザーは、サーバー上のすべてのデータベースにアクセスできるわけではありません。 この要件を回避するには、データベースに `guest` ユーザー アカウントを設定します。guest ユーザーは、データベースにユーザー アカウントがなくてもデータベースにログインしてアクセスできます。  
  
 `guest` アカウントは、SQL Server のすべてのバージョンが備えている組み込みのアカウントです。 新しいデータベースでは、既定で無効化されています。 このアカウントを有効にした場合でも、Transact-SQL の REVOKE CONNECT FROM GUEST ステートメントを実行して、CONNECT 権限を取り消すことによって無効にできます。  
  
> [!IMPORTANT]
> `guest` アカウントはできるだけ使用しないようにしてください。ユーザーごとに割り当てられたデータベース権限がなくても、すべてのログイン ユーザーが、このアカウントに付与されているデータベース権限を取得できるようになります。 `guest` アカウントを使用する必要がある場合は、最小限の権限を付与するようにしてください。  
  
 SQL Server のログイン、ユーザー、およびロールの詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[データベースエンジンのアクセス許可を持つはじめに](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|プリンシパル、ロール、資格情報、セキュリティ保護可能なリソース、および権限について説明したトピックへのリンクが含まれています。|  
|[プリンシパル](/sql/relational-databases/security/authentication-access/principals-database-engine)|プリンシパルの説明のほか、サーバー ロールとデータベース ロールについて説明したトピックへのリンクが含まれています。|  
  
## <a name="see-also"></a>関連項目

- [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server におけるアプリケーション セキュリティのシナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server での認証](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [SQL Server における所有権とユーザーとスキーマの分離](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [SQL Server の承認とアクセス許可](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
