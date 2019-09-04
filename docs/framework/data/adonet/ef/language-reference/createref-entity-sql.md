---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251101"
---
# <a name="createref-entity-sql"></a>CREATEREF (Entity SQL)
エンティティ セット内のエンティティへの参照を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>引数  
 `entityset_identifier`  
 エンティティ セット識別子。文字列リテラルは使用できません。  
  
 `row_typed_expression`  
 エンティティ型のキー プロパティに対応する行型の式。  
  
## <a name="remarks"></a>Remarks  
 `row_typed_expression` は、エンティティのキーの種類に構造的に同等である必要があります。 つまり、エンティティ キーのフィールドの数、型、および順序と一致している必要があります。  
  
 次の例では、Orders と BadOrders は両方とも Order 型のエンティティ セットで、ID は Order の 1 つのキー プロパティであると見なされます。 この例は、BadOrders 内のエンティティへの参照を生成する方法を示しています。 参照は未解決の場合がある点に注意してください。  つまり、参照は実際には指定のエンティティを識別しない場合があります。 そのような場合、その参照に対して `DEREF` 操作を行うと、null が返されます。  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>例  
 次の Entity SQL クエリは、CREATEREF 演算子を使用してエンティティ セット内のエンティティへの参照を作成します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. [「方法:StructuralType の結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)を返すクエリを実行します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [DEREF](deref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [REF](ref-entity-sql.md)
