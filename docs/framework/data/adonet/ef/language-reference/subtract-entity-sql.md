---
title: '- (減算)(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: aa179f65dbbf1f411fd137a759bb37efbdd1fb48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494068"
---
# <a name="--subtract-entity-sql"></a>- (減算) (Entity SQL)
2 つの値の間で減算をします。  
  
## <a name="syntax"></a>構文  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意の数値データ型の有効な式。  
  
## <a name="result-types"></a>戻り値の型  
 2 つの引数の暗黙の型の昇格の結果であるデータ型。 暗黙的な型の上位変換の詳細については、[型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)を参照してください。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、- 算術演算子を使用して 2 つの数値の間で減算をします。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a>関連項目
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
