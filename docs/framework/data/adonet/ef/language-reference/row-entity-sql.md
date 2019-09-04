---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: dfd0031f49cbdf41797cecf21c149fafde4d7a8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249246"
---
# <a name="row-entity-sql"></a>ROW (Entity SQL)
1 つまたは複数の値から構造的に型付けされた匿名レコードを構築します。  
  
## <a name="syntax"></a>構文  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 行型で構築する値を返す任意の有効なクエリ式。  
  
 `alias`  
 行型で指定された値の別名を指定します。 別名を指定しないと、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 別名生成規則に基づいて別名の生成を試みます。  
  
## <a name="return-value"></a>戻り値  
 行型。  
  
## <a name="remarks"></a>Remarks  
 1 つまたは複数の値から構造的に型付けされた匿名レコードを構築するには、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の行コンストラクターを使用します。 行コンストラクターの結果の型は、行の構築に使用された値の型に対応するフィールド型を持つ行型です。 たとえば、次の式は `Record(a int, b string, c int)`型の値を構築します。  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 行コンストラクターで式の別名が指定されていなければ、Entity Framework は別名の生成を試みます。 詳細については、「 [識別子](identifiers-entity-sql.md) 」トピックの「別名規則」セクションを参照してください。  
  
 次の規則は、行コンストラクターで別名を定義する式に適用されます。  
  
- 行コンストラクターの式で同じコンストラクターの他の別名を参照することはできません。  
  
- 同じ行コンストラクター内の 2 つの式に同じ別名を指定することはできません。  
  
 クエリコンストラクターの詳細については、「[型の構築](constructing-types-entity-sql.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリは ROW 演算子を使用して、構造的に型付けされた匿名レコードを構築します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. [「方法:StructuralType の結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)を返すクエリを実行します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>関連項目

- [コンストラクター](constructing-types-entity-sql.md)
- [Entity SQL リファレンス](entity-sql-reference.md)
- [型定義](type-definitions-entity-sql.md)
