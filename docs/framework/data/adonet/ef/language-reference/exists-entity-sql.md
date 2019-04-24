---
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 72d96c5f24fcedf870370de3792680831145a454
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311137"
---
# <a name="exists-entity-sql"></a>EXISTS (Entity SQL)
コレクションが空かどうかを調べます。  
  
## <a name="syntax"></a>構文  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 コレクションを返す任意の有効な式。  
  
 NOT  
 EXISTS の結果を否定することを指定します。  
  
## <a name="return-value"></a>戻り値  
 コレクションが空でない場合は `true`、それ以外の場合は `false` です。  
  
## <a name="remarks"></a>Remarks  
 EXISTS は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。 優先順位は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]集合演算子を参照してください[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)します。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、EXISTS 演算子を使用して、コレクションが空かどうかを調べます。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
