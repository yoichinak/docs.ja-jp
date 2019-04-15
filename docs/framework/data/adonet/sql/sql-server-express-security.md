---
title: SQL Server Express のセキュリティ
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: f4291de89b397f60aedd35b89d6aa3130d348be5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174552"
---
# <a name="sql-server-express-security"></a>SQL Server Express のセキュリティ
Microsoft SQL Server Express Edition (SQL Server Express) は Microsoft SQL Server をベースとしており、同データベース エンジンの多くの機能をサポートしています。 必須ではない機能やネットワーク接続は、既定では無効にされています。 これは悪意のあるユーザーに攻撃の隙をできるだけ与えないようにするための配慮です。  
  
 通常、SQL Server Express は名前付きインスタンスとしてインストールされます。 このインスタンスの既定の名前は `SQLExpress` です。 名前付きインスタンスは、コンピューターのネットワーク名と、インストール時に指定したインスタンス名によって識別されます。  
  
## <a name="network-access"></a>ネットワーク アクセス  
 セキュリティ上の理由により、SQL Server Express では、ネットワーク プロトコルが既定で無効になっています。 これにより、SQL Server Express のインスタンスをホストしているコンピューターを危険にさらすような、外部ユーザーからの攻撃を防ぐことができます。 SQL Server Express インスタンスに別のコンピューターから接続する場合は、ネットワーク接続を明示的に有効にし、SQL Server Browser サービスを開始する必要があります。  
  
 ネットワーク接続を有効にした場合、SQL Server Express のインスタンスにも、他のエディションの SQL Server と同じセキュリティ要件が適用されます。  
  
## <a name="user-instances"></a>ユーザー インスタンス  
 ユーザー インスタンスは、SQL Server Express の親インスタンスによって生成される SQL Server Express データベース エンジンの独立したインスタンスです。 ユーザー インスタンスの主要な目的は、Windows を最小限の権限しか持たないユーザー アカウントで実行しているユーザーが、そのローカル コンピューター上の SQL Server Express インスタンスについてはシステム管理者 (`sysadmin`) 権限を利用できるようにすることです。 ローカル コンピューターのシステム管理者を想定したものではありません。  
  
 ユーザー インスタンスは、SQL Server のプライマリ インスタンス (SQL Server Express) が、ユーザーに代わって生成するインスタンスです。 サービスとして実行されるのではなく、ユーザーの Windows セキュリティ コンテキスト下で、ユーザー プロセスとして実行されます。 サポートされているのは Windows ログインのみで、SQL Server ログインは禁止されています。 実行可能な操作はログインしたユーザーの権限に限定されるため、ユーザー インスタンスで実行されているソフトウェアによって、システム全体に及ぶ変更が行われることはありません。 ユーザー インスタンスは子インスタンスまたはクライアント インスタンス、あるいは、"Run As Normal User" の頭文字を取って RANU と呼ばれることもあります。  
  
 各ユーザー インスタンスは、その親インスタンスや同じコンピューター上で実行されている他のユーザー インスタンスとは分離されます。 ユーザー インスタンス上にインストールされたデータベースは、シングル ユーザー モードでのみ開くことができ、複数のユーザーが接続することはできません。 ユーザー インスタンスでは、レプリケーション、分散クエリ、およびリモート接続が無効にされています。 ユーザー インスタンスに接続したユーザーには、親 SQL Server Express インスタンスに対する特別な権限は一切与えられません。  
  
## <a name="external-resources"></a>外部リソース  
 SQL Server Express の詳細については、次のリソースを参照してください。  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition オンライン ブック](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|SQL Server 2005 Express Edition の完全なドキュメントです。|  
|[管理者以外のユーザー インスタンス](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100))で SQL Server オンライン ブック|ユーザー インスタンスの作成方法および配置方法について説明します。|  
|[SQL Server Express ユーザー インスタンス](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|ADO.NET アプリケーションにおけるユーザー インスタンスの機能について説明します。 ユーザー インスタンスを有効にする方法、<xref:System.Data.SqlClient.SqlConnection> を使ってユーザー インスタンスに接続する方法、ユーザー インスタンスの有効期間、ユーザー インスタンスのシナリオについて情報を提供します。|  
  
## <a name="see-also"></a>関連項目

- [SQL Server のセキュリティ](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [SQL Server Express ユーザー インスタンス](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
