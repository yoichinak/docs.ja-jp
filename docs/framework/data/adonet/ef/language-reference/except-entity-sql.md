---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 32c8c418056231e98696eb8f4e9cb372d6c5740c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089459"
---
# <a name="except-entity-sql"></a>EXCEPT (Entity SQL)
EXCEPT オペランドの左辺のクエリ式から返される結果のうち、右辺のクエリ式でも返される結果を除いた、重複しない値のコレクションを返します。 すべての式は、 `expression`と同じ型であるか、共通の基本型または派生型である必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 コレクションを返す任意の有効なクエリ式。もう一方のクエリ式から返されたコレクションと比較されます。  
  
## <a name="return-value"></a>戻り値  
 `expression`と同じ型であるか、共通の基本データ型または派生型であるコレクション。  
  
## <a name="remarks"></a>Remarks  
 EXCEPT は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。 次の表に、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集合演算子の優先順位を示します。  
  
|優先順位|演算子|  
|----------------|---------------|  
|最高|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||EXCEPT|  
|最低|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、EXCEPT 演算子を使用して、2 つのクエリ式から重複しない値のコレクションを返します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
