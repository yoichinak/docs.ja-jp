---
title: クエリ式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 5a200c8fc5adcb6334d0a0ddf290d275de4eb768
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696881"
---
# <a name="query-expressions-entity-sql"></a>クエリ式 (Entity SQL)
クエリ式とは、さまざまなクエリ演算子を組み合わせて 1 つの構文にしたものです。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 次の式のさまざまな種類用意されています:[リテラル](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)、[パラメーター](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)、[変数](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)、演算子、[関数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)、set 演算子、および具合です。 詳細については、[Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)を参照してください。  
  
## <a name="clauses"></a>句  
 クエリ式は、オブジェクトのコレクションに連続した操作を適用する一連の句で構成されます。 これらは、SQL select ステートメントの標準で見つかった場合、同じ句に基づいています。[選択](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)、 [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)、[場所](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)、[でグループ化](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)、 [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)、および[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)します。  
  
## <a name="scope"></a>スコープ  
 FROM 句で定義された名前は、出現順 (左から右の順) に FROM スコープに導入されます。 JOIN リストでは、式は既にリストで定義されている名前を参照できます。 FROM 句で指定された要素のパブリック プロパティは FROM スコープに追加されません。それらは、別名で修飾された名前を常に参照する必要があります。 通常は、SELECT 式のすべての部分が FROM スコープに含まれると見なされます。  
  
## <a name="see-also"></a>関連項目
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
