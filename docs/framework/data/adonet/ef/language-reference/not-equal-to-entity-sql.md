---
title: '!= (等しくない) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 3d6e391e708b81c45af82280f200aebdaef41421
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130971"
---
# <a name="-not-equal-to-entity-sql"></a>!= (等しくない) (Entity SQL)
2 つの式を比較して、左の式の値が右の式の値と等しくないかどうかを判別します。 != (等しくない) 演算子は、機能的には <> 演算子と同じです。  
  
## <a name="syntax"></a>構文  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意の有効な式。 両方の式とも、暗黙的に変換可能なデータ型でなければなりません。  
  
## <a name="result-types"></a>戻り値の型  
 `true` 左の式が右の式と等しくない場合それ以外の場合、`false`します。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリは != 演算子を使用して 2 つの式を比較し、左の式が右の式と等しくないかどうかを判別します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
