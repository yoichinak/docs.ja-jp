---
title: シーケンスの要素の取得またはスキップ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 885e6bc011041320a3dc7b17d84b2541bf030adf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168312"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>シーケンスの要素の取得またはスキップ
<xref:System.Linq.Queryable.Take%2A> 演算子を使用すると、シーケンス内の指定された数の要素を返し、残りをスキップできます。  
  
 <xref:System.Linq.Queryable.Skip%2A> 演算子を使用すると、シーケンス内の指定された数の要素をスキップし、残りを返すことができます。  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> を SQL Server 2000 に対するクエリで使用する場合は、いくつかの制限があります。 詳細については、「Skip 例外と Take 例外を SQL Server 2000」エントリを参照してください。[トラブルシューティング](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)します。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 変換<xref:System.Linq.Queryable.Skip%2A>サブクエリを使用して、SQL を使用した、`NOT EXISTS`句。 この変換には、次のような制限があります。  
  
-   引数は、セットである必要があります。 順序が指定されていてもマルチセットはサポートされません。  
  
-   生成されるクエリは、<xref:System.Linq.Queryable.Skip%2A> が適用される基本クエリに対して生成されるクエリより複雑な場合があります。 複雑なために、パフォーマンスが低下したり、タイムアウトが発生することもあります。  
  
## <a name="example"></a>例  
 次の例では、`Take` を使用して、雇用された最初の 5 人の `Employees` を選択します。 コレクションは最初、`HireDate` 順に並べられます。  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Linq.Queryable.Skip%2A> を使用して、最も値段が高い 10 個の `Products` 以外のすべてを選択します。  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Linq.Queryable.Skip%2A> メソッドと <xref:System.Linq.Queryable.Take%2A> メソッドを組み合わせて、最初の 50 レコードをスキップし、次の 10 レコードを返します。  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> 操作と <xref:System.Linq.Queryable.Skip%2A> 操作は、順序付けされたセットに対してのみ正しく定義されます。 順序付けされていないセットまたはマルチセットのセマンティクスは未定義です。  
  
 SQL での順序付けの制限により、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、<xref:System.Linq.Queryable.Take%2A> 演算子または <xref:System.Linq.Queryable.Skip%2A> 演算子の引数の順序を、演算子の結果に移動することを試みます。  
  
> [!NOTE]
>  [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] と [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)] で変換は異なります。 複雑さに関係なくクエリを指定して <xref:System.Linq.Queryable.Skip%2A> を使用する予定の場合は、[!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)] を使用してください。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に対して次の [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] クエリを検討します。  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次に示すように、順序付けを SQL コードの最後に移動します。  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <xref:System.Linq.Queryable.Take%2A> と <xref:System.Linq.Queryable.Skip%2A> を連結する場合は、指定されているすべての順序が一致する必要があります。 それ以外の場合、結果は未定義です。  
  
 SQL の仕様に基づく負でない定数の整数引数に対して、<xref:System.Linq.Queryable.Take%2A> と <xref:System.Linq.Queryable.Skip%2A> の両方とも正しく定義されます。  
  
## <a name="see-also"></a>関連項目

- [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [標準クエリ演算子の変換](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
