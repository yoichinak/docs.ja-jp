---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 76a63140668fb1f41cf9e6f901d9a43240a1d098
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936085"
---
# <a name="having-entity-sql"></a>HAVING (Entity SQL)
グループまたは集計の検索条件を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>引数  
 `search_condition`  
 グループまたは集計の検索条件を指定します。 HAVING 句を GROUP BY ALL と共に使用した場合、HAVING 句により ALL はオーバーライドされます。  
  
## <a name="remarks"></a>Remarks  
 HAVING 句は、グループ化の結果について追加的なフィルター処理条件を指定する場合に使用します。 クエリ式で GROUP BY 句が指定されていないと、暗黙的な単独セットのグループになります。  
  
> [!NOTE]
> HAVING は、 [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)ステートメントでのみ使用できます。 [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)を使用しない場合、HAVING は WHERE 句と同様に動作します。  
  
 GROUP BY 操作後に適用される場合を除いて、HAVING 句は WHERE 句と同様に動作します。 つまり、次の例のように、HAVING 句は別名および集計のグループ化のみを参照できます。  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 前述のグループは、複数の製品を含むグループのみに制限されています。  
  
## <a name="example"></a>例  
 次の Entity SQL のクエリでは、HAVING および GROUP BY 操作を使用して、グループまたは集計の検索条件を指定します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. [「方法:PrimitiveType の結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)を返すクエリを実行します。  
  
2. 次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [クエリ式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
