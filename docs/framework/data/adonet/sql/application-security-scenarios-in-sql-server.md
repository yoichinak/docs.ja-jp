---
title: SQL Server におけるアプリケーション セキュリティのシナリオ
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 96c9f48cbf2e2ade2ff1688573a83fd86d613f2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130163"
---
# <a name="application-security-scenarios-in-sql-server"></a>SQL Server におけるアプリケーション セキュリティのシナリオ
安全な SQL Server クライアント アプリケーションを作成するにあたって、絶対に正しいという唯一の方法はありません。 アプリケーションの要件、配置環境、およびユーザー数は、アプリケーションごとに異なります。 配置した当初は十分なセキュリティが確保されたアプリケーションも、時間の経過と共に安全性が低下してゆくことが考えられます。 将来発生する脅威を正確に予測することは不可能です。  
  
 SQL Server は、製品として何度もバージョン アップを重ねながら、開発者が安全なデータベース アプリケーションを作成できるように、最新のセキュリティ機能を取り入れつつ進化してきました。 しかし、普遍的なセキュリティがない以上、継続的に監視し更新してゆくことがどうしても必要になります。  
  
## <a name="common-threats"></a>一般的な脅威  
 開発者は、セキュリティ上の脅威とそれに対抗するツール、および、セキュリティ ホールを作らないようにするにはどうすればよいかを理解しておく必要があります。 セキュリティは鎖のようなものと考えることができます。つまり、1 か所でも弱い部分があると、全体の強度が損なわれるということです。 以下は、このセクションの各トピックで詳しく取り上げているセキュリティ上の一般的な脅威を一覧にしたものです。  
  
### <a name="sql-injection"></a>SQL インジェクション  
 SQL インジェクションとは、悪意のあるユーザーによって、有効な入力データの代わりに Transact-SQL ステートメントが入力されることをいいます。 この入力データが検証を経ることなくサーバーに直接渡され、なおかつ、挿入されたコードをアプリケーションが気付かずに実行した場合、その攻撃によってデータが破損または破壊される可能性があります。 SQL Server インジェクション攻撃を阻止する方法としては、ストアド プロシージャやパラメーター化コマンドを使用する方法のほか、動的 SQL を実行できないようにしたり、すべてのユーザーの権限を制限したりすることが考えられます。  
  
### <a name="elevation-of-privilege"></a>権限の昇格  
 権限の昇格攻撃は、ユーザーが、所有者や管理者など、信頼されたアカウントの権限で振る舞うことのできる状況で発生します。 大切なことは、常に最小限の特権しか持たないユーザー アカウントで実行するようにし、必要な権限以外は割り当てないようにすることです。 コードの実行に、管理者アカウントや所有者アカウントを使用することは避けてください。 このようにすることで、仮に攻撃を阻止できなかった場合でも、損害の範囲を最小限に抑えることができます。 より高い権限が要求されるタスクを行う場合は、そのタスクの期間だけプロシージャの署名や権限の借用を使用するようにします。 証明書を使ってストアド プロシージャに署名したり、権限の借用を使用して一時的に権限を割り当てたりできます。  
  
### <a name="probing-and-intelligent-observation"></a>プローブと情報取得  
 プローブ攻撃には、アプリケーションから生成されるエラー メッセージを調べてセキュリティ上の脆弱性を探す手法がよく用いられます。 すべてのプロシージャ コードにはエラー処理を実装し、SQL Server のエラー情報がエンド ユーザーに返されないようにしてください。  
  
### <a name="authentication"></a>認証  
 SQL Server ログインを使用したアプリケーションでは、ユーザーによって入力されたデータから実行時に接続文字列を構築している場合、接続文字列のインジェクション攻撃を受ける可能性があります。 接続文字列をチェックして、有効なキーワードの組み合わせが使用されているかどうかを調べないと、攻撃者によって余分な文字が挿入され、機密データなど、サーバー上のリソースへのアクセスを許してしまうことも考えられます。 できるだけ Windows 認証を使用してください。 SQL Server ログインを使用する必要がある場合は、<xref:System.Data.SqlClient.SqlConnectionStringBuilder> を使用して接続文字列を実行時に作成および検証するようにします。  
  
### <a name="passwords"></a>パスワード  
 権限を持ったユーザーのパスワードを侵入者が入手するか、パスワードを推測できた場合、多くの場合、攻撃を許す結果になります。 パスワードは侵入者に対する防御の最前線であるため、システムのセキュリティにとって強力なパスワードを設定することは不可欠です。 混合モード認証のパスワード ポリシーを作成して適用するようにしてください。  
  
 Windows 認証を使用する場合でも、`sa` アカウントに必ず強力なパスワードを割り当てます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL Server でのストアド プロシージャを使用したアクセス許可の管理](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 ストアド プロシージャを使用して権限を管理したり、データ アクセスを制御したりする方法について説明します。 ストアド プロシージャは、セキュリティ上のさまざまな脅威に対抗する手段として効果的です。  
  
 [SQL Server での安全な動的 SQL の作成](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 ストアド プロシージャを使用して、安全な動的 SQL を作成する手法について説明します。  
  
 [SQL Server でのストアド プロシージャの署名](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 証明書を使ってストアド プロシージャに署名することで、ユーザーが直接アクセスしなくてもデータを利用できるようにする方法について説明します。 これにより、操作を直接実行するための権限が呼び出し元になくても、ストアド プロシージャで操作を実行できます。  
  
 [SQL Server での借用を使用したアクセス許可のカスタマイズ](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 EXECUTE AS 句を使って他のユーザーの権限を借用する方法について説明します。 権限の借用では、呼び出し元の実行コンテキストが、特定のユーザーの実行コンテキストに切り替えられます。  
  
 [SQL Server における行レベルのアクセス許可の付与](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 データ アクセスを制限する行レベルの権限を実装する方法について説明します。  
  
 [SQL Server でのアプリケーション ロールの作成](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 アプリケーション ロールの機能について説明します。  
  
 [SQL Server での複数データベースにまたがるアクセスの有効化](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 セキュリティを損なうことなく複数データベースにまたがるアクセスを有効にする方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [SQL Server のセキュリティ](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [SQL Server セキュリティの概要](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
