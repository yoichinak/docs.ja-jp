---
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: f4fa8cbc07513321e59b93503b59af172c0a6f05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211323"
---
# <a name="in-entity-sql"></a>IN (Entity SQL)
コレクション内に一致する値があるかどうかを調べます。  
  
## <a name="syntax"></a>構文  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>引数  
 `value`  
 照合する値を返す任意の有効な式。  
  
 [ NOT ]  
 IN の `Boolean` 型の結果を否定することを指定します。  
  
 `expression`  
 一致の判定対象のコレクションを返す任意の有効な式。 すべての式は、 `value`と同じ型であるか、共通の基本型または派生型である必要があります。  
  
## <a name="return-value"></a>戻り値  
 `true` 値がコレクションで見つかった場合値が null の場合は null またはコレクションが null です。それ以外の場合、`false`します。 NOT IN を使用すると、IN の結果が否定されます。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、IN 演算子を使用して、コレクション内に一致する値があるかどうかを調べます。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
