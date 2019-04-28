---
title: '* (乗算)(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 308df758d59a7e12a8b5a19ae72fcbee2f168490
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760468"
---
# <a name="-multiply-entity-sql"></a>* (乗算) (Entity SQL)
2 つの式を乗算します。  
  
## <a name="syntax"></a>構文  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意の数値データ型の有効な式。  
  
## <a name="result-types"></a>戻り値の型  
 2 つの引数の暗黙の型の昇格の結果であるデータ型。 暗黙的な型の上位変換の詳細については、次を参照してください。[型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)します。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、* 算術演算子を使用して 2 つの数値を乗算します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
