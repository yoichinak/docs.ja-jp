---
title: SQL Server でのバルク コピー操作
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 086b3b997cf0915be7cfa603a651eb412d52e985
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194800"
---
# <a name="bulk-copy-operations-in-sql-server"></a>SQL Server でのバルク コピー操作
Microsoft SQL Server には、という一般的なコマンド ライン ユーティリティが含まれています。 **bcp**の高速で一括 SQL Server データベースのテーブルまたはビューに大きなファイルをコピーします。 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、同様の機能を備えたマネージド コード ソリューションを作成できます。 SQL Server のテーブルにデータを読み込むには、INSERT ステートメントを使用するなどの方法もありますが、<xref:System.Data.SqlClient.SqlBulkCopy> を使用すれば他の方法よりもパフォーマンス面で大幅に有利になります。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、SQL Server のテーブルにのみデータを書き込むことができます。 ただし、データ ソースについては SQL Server に限定されているわけではありません。<xref:System.Data.DataTable> インスタンスのデータの読み込み、または、<xref:System.Data.IDataReader> インスタンスによるデータの読み取りであれば、任意のデータ ソースを使用することができます。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、次のことを実行できます。  
  
-   単一のバルク コピー操作  
  
-   複数のバルク コピー操作  
  
-   トランザクション内でのバルク コピー操作  
  
> [!NOTE]
>  .NET Framework バージョン 1.1 以前を使用する場合 (サポートされていません、<xref:System.Data.SqlClient.SqlBulkCopy>クラス)、SQL Server TRANSACT-SQL を実行できる**BULK INSERT**ステートメントを使用して、<xref:System.Data.SqlClient.SqlCommand>オブジェクト。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [バルク コピー サンプルのセットアップ](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 バルク コピーの例で使用されるテーブルについて説明します。また、AdventureWorks データベースにテーブルを作成する SQL スクリプトを提供します。  
  
 [バルク コピー操作の単一実行](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用して、SQL Server のインスタンスにデータをバルク コピーする単一の方法を説明します。また、Transact-SQL ステートメントと <xref:System.Data.SqlClient.SqlCommand> クラスを使用したバルク コピー操作の実行方法も説明します。  
  
 [バルク コピー操作の複数実行](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用して、SQL Server のインスタンスにデータのバルク コピー操作を行う複数の方法を説明します。  
  
 [トランザクションとバルク コピー操作](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 トランザクション内でのバルク コピー操作の実行方法を説明します。トランザクションのコミットやロールバックの方法も説明します。  
  
## <a name="see-also"></a>関連項目

- [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
