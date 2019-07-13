---
title: CASE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 3fc916d201ec79c753e06ccfcd6514761f826eb7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489500"
---
# <a name="case-entity-sql"></a>CASE (Entity SQL)
一連の `Boolean` 式を評価して結果を決定します。  
  
## <a name="syntax"></a>構文  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a>引数  
 `n`  
 複数の WHEN `Boolean_expression` THEN `result_expression` 句が使用できることを示すプレースホルダーです。  
  
 THEN `result_expression`  
 `Boolean_expression` が `true`に評価されると返される式です。 `result expression` は、任意の有効な式です。  
  
 ELSE `else_result_expression`  
 比較操作の評価がいずれも `true`でなかった場合に返される式です。 この引数を省略し、比較演算のいずれも `true`に評価されなかった場合、CASE は NULL を返します。 `else_result_expression` は、任意の有効な式です。 `else_result_expression` と任意の `result_expression` のデータ型は同一であるか、暗黙的な変換によって同一の型になる必要があります。  
  
 WHEN `Boolean_expression`  
 検索 CASE 形式を使用した場合に評価される `Boolean` 式です。 `Boolean_expression` は、任意の有効な `Boolean` 式です。  
  
## <a name="return-value"></a>戻り値  
 `result_expression` およびオプションの `else_result_expression`の一連の型の中から、最も優先順位の高い型を返します。  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Case 式が TRANSACT-SQL の case 式に似ています。 case 式を使用すると、適切な結果が得られる式を、一連の条件判定によって決めることができます。 この形式の case 式では、1 つまたは複数の `Boolean` 式によって、最終的に使用される式が決定されます。  
  
 CASE 関数は、各 WHEN 句の `Boolean_expression` を指定された順序で評価し、 `result_expression` として評価された最初の `Boolean_expression` の `true`を返します。 残りの式は評価されません。 `Boolean_expression` の評価がいずれも `true`でなかった場合、データベース エンジンは、ELSE 句が指定されていれば `else_result_expression` を、ELSE 句が指定されていない場合は NULL 値を返します。  
  
 CASE ステートメントでマルチセットを取得することはできません。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、CASE 式を使用して、一連の `Boolean` 式を評価し、結果を取得しています。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。PrimitiveType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)します。  
  
2. 次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>関連項目

- [THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)
- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
