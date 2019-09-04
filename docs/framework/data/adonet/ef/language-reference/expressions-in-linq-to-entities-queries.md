---
title: LINQ to Entities クエリ内の式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250972"
---
# <a name="expressions-in-linq-to-entities-queries"></a>LINQ to Entities クエリ内の式
式は、単一の値、オブジェクト、メソッド、または名前空間として評価されるコード フラグメントです。 式には、リテラル値、メソッド呼び出し、演算子とそのオペランド、または単純な名前を含めることができます。 単純な名前には、変数、型メンバー、メソッド パラメーター、名前空間、または型の名前を指定できます。 式では、他の式をパラメーターとして使用する演算子、またはパラメーターが他のメソッド呼び出しであるメソッド呼び出しを使用できます。 したがって、単純な式だけでなく、非常に複雑な式も作成できます。  
  
 LINQ to Entities のクエリでは、ラムダ式を含む、 <xref:System.Linq.Expressions>名前空間内の型で許可されているものを式に含めることができます。 LINQ to Entities クエリで使用できる式は、 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]にクエリを実行するために使用できる式のスーパーセットです。  に対する[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]クエリの一部である式は、および基になる`ObjectQuery<T>`データソースでサポートされている操作に制限されます。  
  
 次の例では、`Where` 句で使用される比較の式を示します。  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> などの特定の言語構成C# `unchecked`要素は、LINQ to Entities では意味がありません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [定数式](constant-expressions.md)  
  
 [比較式](comparison-expressions.md)  
  
 [NULL 比較](null-comparisons.md)  
  
 [初期化式](initialization-expressions.md)  
  
 [リレーションシップ、ナビゲーションプロパティ、外部キー](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>関連項目

- [ADO.NET Entity Framework](../index.md)
