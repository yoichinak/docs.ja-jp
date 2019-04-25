---
title: 型定義 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 2e068db0ce202c26cad36c8ed7adf0acdfb8e363
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096024"
---
# <a name="type-definitions-entity-sql"></a>型定義 (Entity SQL)
型定義は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline 関数の宣言ステートメントで使用されます。  
  
## <a name="remarks"></a>Remarks  
 インライン関数の宣言ステートメントから成る、[関数](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)キーワードの後に (かっこで囲まれたパラメーター定義リストが続く関数名 (例:"MyAvg") を表す識別子例:"dues します。  
  
 パラメーター定義リストは、0 個以上のパラメーター定義で構成されます。 各パラメーター定義は、識別子 (関数のパラメーターの名前。例 : "dues") とそれに続く型定義 (例 : "Collection(Decimal)") で構成されます。  
  
 型定義は、次のいずれかになります。  
  
-   識別子の型 ("Int32" や "AdventureWorks.Order" など)。  
  
-   キーワード `COLLECTION` とそれに続くかっこに囲まれた別の型定義 (例 : "Collection(AdventureWorks.Order)")。  
  
-   キーワード ROW とそれに続くかっこに囲まれたプロパティ定義リスト (例 : "Row(x AdventureWorks.Order)")。 プロパティの定義などの形式である"`identifier type_definition`、 `identifier type_definition`,..."です。  
  
-   キーワード REF とそれに続くかっこに囲まれた識別子の型 (例 : "Ref(AdventureWorks.Order)")。 REF 型定義演算子は、引数としてエンティティ型を必要とします。 引数としてプリミティブ型を指定することはできません。  
  
 型定義を入れ子にできます (例 : "Collection(Row(x Ref(AdventureWorks.Order)))")。  
  
 型定義のオプションは、次のとおりです。  
  
-   `IdentifierName supported_type`、または  
  
-   `IdentifierName` COLLECTION(`type_definition`)、または  
  
-   `IdentifierName` ROW(`property_definition`)、または  
  
-   `IdentifierName` REF(`supported_entity_type`)  
  
 プロパティ定義オプションは、`IdentifierName type_definition` です。  
  
 現在の名前空間で使用されている型であれば、いずれもサポートされます。 これには、プリミティブ型とエンティティ型の両方が含まれます。  
  
 サポートされるエンティティ型は、現在の名前空間で使用されているエンティティ型だけを参照します。 これには、プリミティブ型は含まれません。  
  
## <a name="examples"></a>使用例  
 簡単な型定義の例を次に示します。  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 COLLECTION 型定義の例を次に示します。  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 ROW 型定義の例を次に示します。  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 REF 型定義の例を次に示します。  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>関連項目

- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
