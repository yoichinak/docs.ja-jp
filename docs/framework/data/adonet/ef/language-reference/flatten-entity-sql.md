---
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 4f9a6315fc9cc2f295c21cc5fb7e1007e47796b9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304578"
---
# <a name="flatten-entity-sql"></a>FLATTEN (Entity SQL)
コレクションのコレクションをフラット化して単一のコレクションに変換します。 変換後のコレクションは、入れ子構造が失われるだけで、変換前のコレクションとまったく同じ要素を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>引数  
 `collection`  
 値のコレクションのコレクションをフラット化して単一のコレクションとして返す有効な任意の式。  
  
## <a name="remarks"></a>Remarks  
 `FLATTEN` 1 つ、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]演算子を設定します。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。 参照してください[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)の優先順位は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]演算子を設定します。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、 `FLATTEN` 演算子を使用して、コレクションのコレクションをフラット化されたコレクションに変換します。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
