---
title: '- (除算)(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: c3b477a63adf3c3d51f28449e94c2b716422296c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330858"
---
# <a name="-divide-entity-sql"></a>/ (除算) (Entity SQL)
1 つの値を別の値で除算します。  
  
## <a name="syntax"></a>構文  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>引数  
 `dividend`  
 除算する数値式。 `dividend` は、任意の数値データ型の有効な式です。  
  
 `divisor`  
 被除数を除算する数値式。 `divisor` は、任意の数値データ型の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  
 2 つの引数の暗黙の型の昇格の結果であるデータ型。 暗黙的な型の上位変換の詳細については、次を参照してください。[型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)します。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリを使用して、/算術演算子を別の 1 つの数値を除算します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
