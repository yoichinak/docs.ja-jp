---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 9066f9fb68ce2c50e9523881cfa0dd930cd0b52e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319730"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
クエリ式が NULL かどうかを調べます。  
  
## <a name="syntax"></a>構文  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意の有効なクエリ式。 コレクションにすることはできません。また、コレクション メンバーや、コレクション型のプロパティを持つレコード型を含めることはできません。  
  
 NOT  
 IS NULL の EDM.Boolean の結果を否定します。  
  
## <a name="return-value"></a>戻り値  
 `true` によって NULL が返される場合は `expression`、それ以外の場合は `false` です。  
  
## <a name="remarks"></a>Remarks  
 外部結合の要素が NULL かどうかを確認するには、`IS NULL` を使用します。  
  
```sql  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 メンバーに実際の値が含まれているかどうかを確認するには、`IS NULL` を使用します。  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 次の表は、いくつかのパターンにおける `IS NULL` の動作を示しています。 すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。  
  
|パターン|動作|  
|-------------|--------------|  
|null IS NULL|`true`を返します。|  
|TREAT (null AS EntityType) IS NULL|`true`を返します。|  
|TREAT (null AS ComplexType) IS NULL|エラーをスローします。|  
|TREAT (null AS RowType) IS NULL|エラーをスローします。|  
|EntityType IS NULL|`true` または `false`を返します。|  
|ComplexType IS NULL|エラーをスローします。|  
|RowType IS NULL|エラーをスローします。|  
  
## <a name="example"></a>例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリでは、IS NOT NULL 演算子を使用して、クエリ式が null でないかどうかを判断します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
