---
title: ADO.NET および LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 10e60ebd71c4615354c25d3a61a04e9d12d7c800
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167194"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET および LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 一部である、[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]テクノロジのファミリです。 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] プロバイダー モデルから提供されるサービスに基づいて動作します。 したがって組み合わせることができます[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]コードを既存[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]アプリケーションさせ、現在[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]の解決策を[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]します。 次の図は、この関係を高いレベルから見たものです。  
  
 ![LINQ to SQL および ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>接続  
 既存を指定する[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]接続を作成するとき、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>します。 に対するすべての操作、 <xref:System.Data.Linq.DataContext> (クエリ) を含むこの接続を使用します。 場合は、接続がまだ開いて[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]はこれで終了するときに、そのままです。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 次のコードに示すとおり、<xref:System.Data.Linq.DataContext.Connection%2A> プロパティを使用して、いつでも接続にアクセスしたり、任意に閉じたりすることができます。  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>トランザクション  
 既に独自のデータベース トランザクションを初期化していて、<xref:System.Data.Linq.DataContext> をトランザクションに使用する必要がある場合は、<xref:System.Data.Linq.DataContext> をトランザクションに渡すことができます。  
  
 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] でトランザクションを実行する場合は、<xref:System.Transactions.TransactionScope> オブジェクトの使用をお勧めします。 この方法を使うと、データベースと他のメモリ常駐リソース マネージャー間で動作する分散トランザクションを作成できます。 トランザクション スコープは、わずかなリソースで開始されます。 トランザクションのスコープ内に複数の接続がある場合のみ、このトランザクションは分散トランザクションに昇格します。  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 この方法は、すべてのデータベースに使用できるわけではありません。 たとえば、SqlClient 接続を [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] サーバーに使用する場合、この接続はシステム トランザクションに昇格できません。 代わりに、トランザクション スコープが使用されているときは、完全な分散トランザクションに自動的に参加します。  
  
## <a name="direct-sql-commands"></a>直接 SQL コマンド  
 ときには、クエリを実行したり変更内容を送信したりする <xref:System.Data.Linq.DataContext> 機能に不足があり、実行する必要がある特別なタスクを完了できないこともあります。 このような場合は、<xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドを使用して、SQL コマンドをデータベースに発行し、クエリ結果をオブジェクトに変換することができます。  
  
 たとえば、`Customer` クラスのデータが 2 つのテーブル (customer1 および customer2) に含まれているとします。 次のクエリは `Customer` オブジェクトのシーケンスを返します。  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 表形式の結果内の列名が、エンティティ クラスの列のプロパティと一致する限り[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL クエリからオブジェクトを作成します。  
  
### <a name="parameters"></a>パラメーター  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドは、パラメーターを受け取ります。 次のコードでは、パラメーター化されたクエリが実行されます。  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  パラメーターは、`Console.WriteLine()` および `String.Format()` で使用されるものと同じ中かっこ表記でクエリ テキストに表現されます。 `String.Format()` クエリ文字列を指定し、生成されたパラメーター名の中かっこで囲まれたパラメーターを置き換えるよう受け取り`@p0`、 `@p1` ...,`@p(n)`します。  
  
## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [方法: ADO.NET コマンドおよび DataContext 間の接続を再利用する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
