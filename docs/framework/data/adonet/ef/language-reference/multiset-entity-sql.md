---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 44e411b8ae2f43bf3a729ac091ffd1eb4c462c63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303038"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)
値のリストからマルチセットのインスタンスを作成します。 MULTISET コンストラクターの値はすべて、互換性のある型 `T`である必要があります。 空のマルチセット コンストラクターは使用できません。  
  
## <a name="syntax"></a>構文  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意の有効な値のリスト。  
  
## <a name="return-value"></a>戻り値  
 型 MULTISET のコレクション\<T >。  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、行コンストラクター、オブジェクト コンストラクター、およびマルチセット (またはコレクション) コンストラクターの 3 種類のコンストラクターが用意されています。 詳細については、次を参照してください。[構築型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)します。  
  
 マルチセット コンストラクターは、値のリストからマルチセットのインスタンスを作成します。 このコンストラクターの値はすべて、互換性のある型である必要があります。  
  
 たとえば、次の式は整数のマルチセットを作成します。  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  入れ子になったマルチセット リテラルは、ラッピング multiset がある 1 つの multiset の要素です。 ときにのみサポートします。たとえば、`{{1, 2, 3}}`します。 複数のマルチセット要素が外側のマルチセットに含まれている場合 ( `{{1, 2}, {3, 4}}`など)、入れ子になったマルチセット リテラルはサポートされません。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、MULTISET 演算子を使用して、値のリストからマルチセットのインスタンスを作成します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>関連項目

- [コンストラクター](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
