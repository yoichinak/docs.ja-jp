---
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 6437b17fe1c1277701f06988ef6c02f4caf70e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319468"
---
# <a name="-or-entity-sql"></a>|| (OR) (Entity SQL)
2 つの `Boolean` 式を結合します。  
  
## <a name="syntax"></a>構文  
  
```sql  
boolean_expression OR boolean_expression  
-- or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>引数  
 `boolean_expression`  
 `Boolean`値を返す任意の有効な式。  
  
## <a name="return-value"></a>戻り値  
 いずれかの条件が`true` の場合は `true`、それ以外の場合は `false`。  
  
## <a name="remarks"></a>Remarks  
 OR は [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の論理演算子です。 2 つの条件を結合する場合に使用します。 1 つのステートメント内に複数の論理演算子が使われている場合、OR 演算子は AND 演算子の次に評価されます。 ただし、かっこを使うと、演算の順序を変更することができます。  
  
 2つの縦棒&#124;&#124;() には、or 演算子と同じ機能があります。  
  
 使用可能な入力値と戻り値の型を次の表に示します。  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|true|true|true|  
|`FALSE`|true|false|NULL|  
|`NULL`|true|NULL|NULL|  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、OR 演算子を使用して 2 つの `Boolean` 式を結合します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
