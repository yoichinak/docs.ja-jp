---
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 8cd440571726796ee3d2c91e0d2f6b50571e8e27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785328"
---
# <a name="collection-entity-sql"></a>COLLECTION (Entity SQL)
COLLECTION キーワードは、インライン関数を定義する場合にのみ使用します。 コレクション関数は、値のコレクションを操作してスカラー出力を生成する関数です。  
  
## <a name="syntax"></a>構文  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>引数  
 `type_definition`  
 サポートされる型、行、または参照のコレクションを返す式。  
  
## <a name="remarks"></a>Remarks  
 COLLECTION キーワードについて詳しくは、「 [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例は、COLLECTION キーワードを使用して 10 進数のコレクションをインライン クエリ関数の引数として宣言する方法を示します。  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
