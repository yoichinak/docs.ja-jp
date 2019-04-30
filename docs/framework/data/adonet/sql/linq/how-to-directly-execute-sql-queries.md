---
title: '方法: SQL クエリを直接実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 6423959ed5036cc8ab2a88bb7273ef7aa95c8958
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037766"
---
# <a name="how-to-directly-execute-sql-queries"></a>方法: SQL クエリを直接実行する
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、作成したクエリをパラメーター化された SQL クエリ (テキスト形式) に変換し、それを SQL Server に送って処理します。  
  
 アプリケーションでローカルに使用できるさまざまなメソッドの中には、SQL では実行できないものもあります。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、このようなローカル メソッドを、SQL 環境内で使用できる同等の操作や関数に変換しようとします。 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 組み込み型のほとんどのメソッドと演算子には、SQL コマンドに直接対応する変換が用意されています。 使用可能な関数から生成できるものもあります。 生成できないものについては、ランタイム例外が発生します。 詳細については、次を参照してください。 [SQL-CLR 型マッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)します。  
  
 特殊なタスクに対して [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリでは不十分な場合は、<xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドを使用して SQL クエリを実行し、そのクエリの結果をオブジェクトに直接変換できます。  
  
## <a name="example"></a>例  
 次の例では、`Customer` クラスのデータが 2 つのテーブル (customer1 および customer2) にわたって格納されているものとします。 クエリは `Customer` オブジェクトのシーケンスを返します。  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 表形式の結果内の列名が、エンティティ クラスの列のプロパティと一致する限り[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL クエリからオブジェクトを作成します。  
  
## <a name="example"></a>例  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドは、パラメーターの使用にも対応しています。 パラメーター化されたクエリを実行するには、次のようなコードを使用します。  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 クエリ テキスト内では、`Console.WriteLine()` および `String.Format()` で使用するのと同じ中かっこ表記を使用して、パラメーターを表現します。 実際、`String.Format()`などパラメーター名の生成中、中かっこで囲んだパラメーターを置き換える、指定したクエリ文字列が実際に呼び出される@p0、 @p1 ..., @p(n)。  
  
## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [データベースに対するクエリの実行](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
