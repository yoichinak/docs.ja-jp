---
title: -- (コメント) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 1ea1929b0e6f965f71fbb015ee6795affb3bce7c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251214"
---
# <a name="---comment-entity-sql"></a>-- (コメント) (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリには、コメントを含めることができます。 コメント行の先頭には、2 個のダッシュ (`--`) を付けます。  
  
## <a name="syntax"></a>構文  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a>引数  
 `text_of_comment`  
 コメントのテキストを表す文字列です。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリは、コメントの使い方を示しています。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. [「方法:StructuralType の結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)を返すクエリを実行します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL の概要](entity-sql-overview.md)
- [Entity SQL リファレンス](entity-sql-reference.md)
