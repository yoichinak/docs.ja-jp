---
title: SQL Server でのストアド プロシージャの署名
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 1caf3de06a03d4eab97e68ac1ecdc00dacdd5dc8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094620"
---
# <a name="signing-stored-procedures-in-sql-server"></a>SQL Server でのストアド プロシージャの署名
 デジタル署名は、署名者の秘密キーで暗号化されたデータ ダイジェストです。 秘密キーにより、デジタル署名がその保持者または所有者に固有であることが保証されます。 ストアド プロシージャ、関数 (インライン テーブル値関数) を除く、トリガー、およびアセンブリに署名することができます。  
  
 証明書や非対称キーを使用してストアド プロシージャに署名することができます。 この機能は、動的 SQL などのように、組み合わせ所有権によって権限を継承できない場合や、組み合わせ所有権が壊れている場合を想定して用意されています。 作成、証明書にマップされたユーザー証明書にアクセスする必要があるストアド プロシージャ オブジェクトに対するユーザー アクセス許可を付与します。  

 同じ証明書にマップされるログインを作成し、そのログインに必要なサーバー レベル権限が付与したり 1 つまたは複数の固定サーバー ロールにログインを追加できます。 これは有効にしないように設計されています、`TRUSTWORTHY`データベースより高いレベルのアクセス許可が必要なシナリオを設定します。  
  
 ストアド プロシージャを実行すると、SQL Server は、呼び出し元の証明書ユーザーやログインのアクセス許可を結合します。 異なり、`EXECUTE AS`句では、プロシージャの実行コンテキストは変更されません。 ログイン名とユーザー名を返す組み込み関数を実行すると、証明書ユーザーの名前ではなく、呼び出し元の名前が返されます。  
  
## <a name="creating-certificates"></a>証明書の作成  
 証明書または非対称キー、execute と共に、ストアド プロシージャのコードの暗号化されたハッシュで構成されるデータのダイジェストでストアド プロシージャに署名するときに、ユーザーが作成された秘密キーを使用します。 実行時に、このデータ ダイジェストが公開キーを使用して復号化され、ストアド プロシージャのハッシュ値と比較されます。 Execute を変更するのと、ユーザーは、デジタル署名が不要になったと一致するように、ハッシュ値を無効になります。 ストアド プロシージャに変更を削除します署名全体からストアド プロシージャのコードを変更する秘密キーへのアクセスを持たない誰かができなくなります。 いずれの場合も、する必要があります再署名する手順、コードまたは execute を変更するたびにユーザーとして。  
  
 モジュールへの署名では、2 つの必要な手順があります。  
  
1.  Transact-SQL ステートメント `CREATE CERTIFICATE [certificateName]` を使用して、証明書を作成します。 このステートメントには、開始日、終了日、パスワードを設定するためのオプションがあります。 既定の有効期限の日付は、1 年間です。  
  
1.  Transact-SQL ステートメント `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` を使用して、証明書によってプロシージャに署名します。  

モジュールが署名されていると、1 つまたは複数のプリンシパルは証明書に関連付ける必要のある追加のアクセス許可を保持するために作成する必要があります。  

モジュールには、その他のデータベース レベルのアクセス許可が必要がある場合。  
  
1.  Transact-SQL ステートメント `CREATE USER [userName] FROM CERTIFICATE [certificateName]` を使用して、証明書に関連付けられたデータベース ユーザーを作成します。 このユーザーは、データベースのみに存在し、その同じ証明書からログインが作成されてもいない限り、ログインに関連付けられていません。  
  
1.  証明書ユーザーに必要なデータベース レベルのアクセス許可を付与します。  
  
モジュールには、追加のサーバー レベルのアクセス許可が必要がある場合。  
  
1.  証明書のコピー、`master`データベース。  
 
1.  TRANSACT-SQL を使用してその証明書に関連付けられているログインを作成`CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]`ステートメント。  
  
1.  証明書のログインに必要なサーバー レベルのアクセス許可を付与します。  
  
> [!NOTE]  
>  証明書では、DENY ステートメントを使用して権限が取り消されているユーザーに権限を与えることはできません。 DENY は常に GRANT よりも優先されるため、証明書ユーザーに許可された権限を呼び出し元が継承することはできません。  
  
## <a name="external-resources"></a>外部リソース  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[モジュール署名](https://go.microsoft.com/fwlink/?LinkId=98590)で SQL Server オンライン ブック|モジュールの署名について説明し、サンプル シナリオと、関連する Transact-SQL のトピックへのリンクを示します。|  
|[証明書を使用したストアド プロシージャを署名](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)で SQL Server オンライン ブック|証明書を使用したストアド プロシージャの署名のチュートリアルです。|  
  
## <a name="see-also"></a>関連項目

- [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server セキュリティの概要](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server におけるアプリケーション セキュリティのシナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server でのストアド プロシージャを使用した権限の管理](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [SQL Server での安全な動的 SQL の作成](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [SQL Server での借用を使用した権限のカスタマイズ](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [ストアド プロシージャでのデータの変更](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
