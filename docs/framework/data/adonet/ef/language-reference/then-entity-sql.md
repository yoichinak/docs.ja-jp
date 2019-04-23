---
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 8d2d7f9a3a1d6ff9f25db3f19bf8f39781469f9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305625"
---
# <a name="then-entity-sql"></a>THEN (Entity SQL)
WHEN 句が `true`として評価された場合の結果です。  
  
## <a name="syntax"></a>構文  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>引数  
 `when_expression`  
 任意の有効なブール式。  
  
 `then_expression`  
 コレクションを返す任意の有効なクエリ式。  
  
## <a name="remarks"></a>Remarks  
 `when_expression` が `true`として評価された場合、対応する `then-expression`が評価されます。 WHEN の条件が満たされなかった場合は、 `else-expression` が評価されます。 ただし、 `else-expression`が存在しない場合、結果は NULL になります。  
  
 例については、次を参照してください。[ケース](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)します。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、CASE 式を使用して、一連の `Boolean` 式を評価します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。PrimitiveType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)します。  
  
2. 次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>関連項目

- [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
