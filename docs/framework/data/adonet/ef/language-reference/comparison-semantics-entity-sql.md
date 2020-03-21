---
title: 比較セマンティクス (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150455"
---
# <a name="comparison-semantics-entity-sql"></a>比較セマンティクス (Entity SQL)
次のいずれかの [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子を実行すると、型インスタンスの比較が行われます。  
  
## <a name="explicit-comparison"></a>明示的な比較  
 等価演算  
  
- =  
  
- !=  
  
 順序付け操作  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 NULL 値が許容される操作  
  
- IS NULL  
  
- IS NOT NULL  
  
## <a name="explicit-distinction"></a>明示的な区別  
 等価区別  
  
- DISTINCT  
  
- GROUP BY  
  
 順序付け区別  
  
- ORDER BY  
  
## <a name="implicit-distinction"></a>暗黙的な区別  
 設定操作および述語 (等価)  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 項目述語 (等価)  
  
- IN  
  
## <a name="supported-combinations"></a>サポートされる組み合わせ  
 次の表は、各種類の型の比較演算子のサポートされているすべての組み合わせを示します。  
  
|**種類**|**=**<br /><br /> **!=**|**グループ化**<br /><br /> **異なる**|**UNION**<br /><br /> **交差**<br /><br /> **除いて**<br /><br /> **設定**<br /><br /> **重複**|**インチ**|**<<=**<br /><br /> **>>=**|**注文方法**|**NULL です**<br /><br /> **NULL ではありません**|  
|-|-|-|-|-|-|-|-|  
|エンティティの種類|参照<sup>1</sup>|すべてのプロパティ<sup>2</sup>|すべてのプロパティ<sup>2</sup>|すべてのプロパティ<sup>2</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|参照<sup>1</sup>|  
|複合型|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
|行|すべてのプロパティ<sup>4</sup>|すべてのプロパティ<sup>4</sup>|すべてのプロパティ<sup>4</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|すべてのプロパティ<sup>4</sup>|スロー<sup>3</sup>|  
|プリミティブ型|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|  
|マルチセット|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
|参照|はい<sup>5</sup>|はい<sup>5</sup>|はい<sup>5</sup>|はい<sup>5</sup>|Throw|Throw|はい<sup>5</sup>|  
|アソシエーション<br /><br /> type|スロー<sup>3</sup>|Throw|Throw|Throw|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
  
 <sup>1</sup>次の例に示すように、指定されたエンティティ型インスタンスの参照は暗黙的に比較されます。  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 エンティティ インスタンスは、明示的な参照に対して比較できません。 明示的な参照に対する比較を行った場合は、例外がスローされます。 たとえば、次のクエリを実行すると、例外がスローされます。  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>複合型のプロパティは、ストアに送信される前にフラット化されるため、(すべてのプロパティが同等である限り)、同等になります。 4 も参照してください<sup>。</sup>  
  
 <sup>3</sup>Entity Framework ランタイムは、サポートされていないケースを検出し、プロバイダー/ストアを使用せずに意味のある例外をスローします。  
  
 <sup>4</sup>すべてのプロパティを比較しようとしました。 比較不能な型のプロパティ (text、ntext、image など) がある場合、サーバー例外がスローされることがあります。  
  
 <sup>5</sup>参照のすべての要素が比較されます (これには、エンティティ セット名とエンティティ型のすべてのキー プロパティが含まれます)。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL の概要](entity-sql-overview.md)
