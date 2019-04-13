---
title: 比較セマンティクス (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 6b4c4177ebd6c45e00a1ac7774e40a43e0c14a74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083336"
---
# <a name="comparison-semantics-entity-sql"></a>比較セマンティクス (Entity SQL)
次のいずれかの [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子を実行すると、型インスタンスの比較が行われます。  
  
## <a name="explicit-comparison"></a>明示的な比較  
 等価演算  
  
-   =  
  
-   !=  
  
 順序付け操作  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 NULL 値が許容される操作  
  
-   IS_NULL  
  
-   IS NOT NULL  
  
## <a name="explicit-distinction"></a>明示的な区別  
 等価区別  
  
-   DISTINCT  
  
-   GROUP BY  
  
 順序付け区別  
  
-   ORDER BY  
  
## <a name="implicit-distinction"></a>暗黙的な区別  
 設定操作および述語 (等価)  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   OVERLAPS  
  
 項目述語 (等価)  
  
-   IN  
  
## <a name="supported-combinations"></a>サポートされている組み合わせ  
 次の表は、各種類の型の比較演算子のサポートされているすべての組み合わせを示します。  
  
|**型**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**IS_NULL**<br /><br /> **IS NOT NULL**|  
|-|-|-|-|-|-|-|-|  
|エンティティ型|Ref<sup>1</sup>|すべてのプロパティ<sup>2</sup>|すべてのプロパティ<sup>2</sup>|すべてのプロパティ<sup>2</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|Ref<sup>1</sup>|  
|複合型|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
|行|すべてのプロパティ<sup>4</sup>|すべてのプロパティ<sup>4</sup>|すべてのプロパティ<sup>4</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|すべてのプロパティ<sup>4</sup>|スロー<sup>3</sup>|  
|プリミティブ型|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|  
|マルチセット|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
|参照|[はい]<sup>5</sup>|[はい]<sup>5</sup>|[はい]<sup>5</sup>|[はい]<sup>5</sup>|Throw|Throw|[はい]<sup>5</sup>|  
|関連付け<br /><br /> 種類|スロー<sup>3</sup>|Throw|Throw|Throw|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
  
 <sup>1</sup>特定のエンティティ型のインスタンスの参照は、暗黙的に比較すると、次の例に示すようにします。  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 エンティティ インスタンスは、明示的な参照に対して比較できません。 明示的な参照に対する比較を行った場合は、例外がスローされます。 たとえば、次のクエリを実行すると、例外がスローされます。  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>複合型のプロパティが比較可能な (ただし、すべてのプロパティが比較可能な) になるように、ストアに送信される前にフラット化します。 参照してください<sup>4。</sup>  
  
 <sup>3</sup>Entity Framework ランタイムがサポートされていないケースを検出し、プロバイダー/ストアは呼び出されず、意味のある例外をスローします。  
  
 <sup>4</sup>すべてのプロパティを比較ましょう。 比較不能な型のプロパティ (text、ntext、image など) がある場合、サーバー例外がスローされることがあります。  
  
 <sup>5</sup>参照のすべての個々 の要素を比較 (エンティティ セットの名前と、エンティティ型のすべてのキー プロパティを含む)。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
