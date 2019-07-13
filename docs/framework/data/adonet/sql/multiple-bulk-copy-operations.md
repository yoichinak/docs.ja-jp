---
title: バルク コピー操作の複数実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 405a82c625853d242ca68088ffdf81b6bcd7c518
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922214"
---
# <a name="multiple-bulk-copy-operations"></a>バルク コピー操作の複数実行
<xref:System.Data.SqlClient.SqlBulkCopy> クラスのインスタンスを 1 つ使用すると、バルク コピー操作を複数回実行できます。 後続の呼び出しの前に更新する必要があります (たとえば、レプリケーション先テーブルの名前) のコピー間で操作のパラメーターを変更する場合、 **WriteToServer**メソッドは、次の例に示すよう。 明示的に変更されている場合を除き、すべてのプロパティ値は、任意のインスタンスに対する前回のバルク コピー操作の状態のまま残っています。  
  
> [!NOTE]
>  通常、バルク コピー操作を複数回実行する場合は、同じ <xref:System.Data.SqlClient.SqlBulkCopy> のインスタンスを使用する方が各操作ごとに別のインスタンスを使用するよりも効率的です。  
  
 同じ <xref:System.Data.SqlClient.SqlBulkCopy> オブジェクトを使用してバルク コピー操作を複数回実行する場合は、コピー元またはコピー先の情報が各操作ごとに一致しているかまたは異なっているかどうかは制限されません。 ただし、サーバーに書き込み処理を行うときは、列の関連情報を毎回正しく設定する必要があります。  
  
> [!IMPORTANT]
>  このサンプルでは」の説明に従って、作業テーブルを作成していない限りは実行されません[バルク コピー サンプルのセットアップ](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)します。 使用する構文を示すためにこのコードが提供される**SqlBulkCopy**のみです。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [SQL Server でのバルク コピー操作](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
