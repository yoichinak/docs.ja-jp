---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 14c0b5d273b26c71c9c63e8bbbcef863ac95a5f3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319698"
---
# <a name="key-entity-sql"></a>KEY (Entity SQL)
参照またはエンティティ式のキーを抽出します。  
  
## <a name="syntax"></a>構文  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Remarks  
 エンティティ キーには、指定されたエンティティまたはエンティティ参照の正しい順序でキー値が格納されます。 複数のエンティティ セットが同じ型に基づくことができるので、同じキーがそれぞれのエンティティ セットで使用される場合があります。 一意の参照を取得するには、 `REF`を使用します。 KEY 演算子の戻り値の型は、同じ順序でエンティティの各キーの 1 つのフィールドを含む行型です。  
  
 次の例では、キー演算子は、BadOrder エンティティへの参照に渡され、その参照のキー部分を返します。 この場合、 `Id` プロパティに対応する 1 つだけのフィールドを持つレコード型です。  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>例  
 次の Entity SQL クエリは、KEY 演算子を使用して、型参照を持つ式のキー部分を抽出します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
