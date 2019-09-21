---
title: SQL Server でのバルク コピー操作
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: ae97bcdd6776d573cf9e523133c2c00a42c273bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782530"
---
# <a name="bulk-copy-operations-in-sql-server"></a>SQL Server でのバルク コピー操作
Microsoft SQL Server には、大量のファイルを SQL Server データベース内のテーブルまたはビューに一括コピーするための**bcp**という一般的なコマンドラインユーティリティが含まれています。 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、同様の機能を備えたマネージド コード ソリューションを作成できます。 SQL Server のテーブルにデータを読み込むには、INSERT ステートメントを使用するなどの方法もありますが、<xref:System.Data.SqlClient.SqlBulkCopy> を使用すれば他の方法よりもパフォーマンス面で大幅に有利になります。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、SQL Server のテーブルにのみデータを書き込むことができます。 ただし、データ ソースについては SQL Server に限定されているわけではありません。<xref:System.Data.DataTable> インスタンスのデータの読み込み、または、<xref:System.Data.IDataReader> インスタンスによるデータの読み取りであれば、任意のデータ ソースを使用することができます。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、次のことを実行できます。  
  
- 単一のバルク コピー操作  
  
- 複数のバルク コピー操作  
  
- トランザクション内でのバルク コピー操作  
  
> [!NOTE]
> .NET Framework バージョン1.1 またはそれ以前 ( <xref:System.Data.SqlClient.SqlBulkCopy>クラスをサポートしていません) を使用している場合は、 <xref:System.Data.SqlClient.SqlCommand>オブジェクトを使用して SQL Server transact-sql **BULK INSERT**ステートメントを実行できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [バルク コピー サンプルのセットアップ](bulk-copy-example-setup.md)  
 バルク コピーの例で使用されるテーブルについて説明します。また、AdventureWorks データベースにテーブルを作成する SQL スクリプトを提供します。  
  
 [バルク コピー操作の単一実行](single-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用して、SQL Server のインスタンスにデータをバルク コピーする単一の方法を説明します。また、Transact-SQL ステートメントと <xref:System.Data.SqlClient.SqlCommand> クラスを使用したバルク コピー操作の実行方法も説明します。  
  
 [バルク コピー操作の複数実行](multiple-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用して、SQL Server のインスタンスにデータのバルク コピー操作を行う複数の方法を説明します。  
  
 [トランザクションとバルク コピー操作](transaction-and-bulk-copy-operations.md)  
 トランザクション内でのバルク コピー操作の実行方法を説明します。トランザクションのコミットやロールバックの方法も説明します。  
  
## <a name="see-also"></a>関連項目

- [SQL Server と ADO.NET](index.md)
- [ADO.NET の概要](../ado-net-overview.md)
