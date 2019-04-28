---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774726"
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (Entity SQL)
引数値のコレクションを返します。この値は、集計が関連する現在のグループ パーティションから投影されたものです。 `GroupPartition` 集計は、グループベースの集計であり、コレクションベースの形式ではありません。  
  
## <a name="syntax"></a>構文  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意のブール型 ( [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ) の式を指定します。  
  
## <a name="remarks"></a>Remarks  
 次のクエリでは、製品の一覧と、製品ごとの注文明細の数量のコレクションが生成されます。  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 次の 2 つのクエリは、同じ意味を持っています。  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 `GROUPPARTITION` 演算子は、ユーザー定義の集計関数と組み合わせて使用できます。  
  
 `GROUPPARTITION` は、グループ化された入力セットへの参照を格納する特殊な集計演算子です。 この参照は、GROUP BY がスコープに含まれているクエリ内の任意の位置で使用できます。 例えば以下のようにします。  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 通常の GROUP BY では、グループ化の結果は非表示です。 結果は集計関数でのみ使用できます。 グループ化の結果を表示するには、サブクエリを使用してグループ化の結果と、入力セットを相関させる必要があります。 次の 2 つのクエリは等価です。  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 例からわかるように、GROUPPARTITION 集計演算子を使用すると、グループ化後の入力セットへの参照を容易に取得できます。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] パラメーターを使用すると、GROUPPARTITION 演算子では、演算子入力内の任意の `expression` 式を指定できます。  
  
 たとえば、グループ パーティションへの次の入力式はすべて有効です。  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>例  
 次の例では、GROUPPARTITION 句を GROUP BY 句と共に使用する方法を示します。 GROUP BY 句は `SalesOrderHeader` によって `Contact`エンティティをグループ化します。 続いて GROUPPARTITION 句は、各グループの `TotalDue` プロパティを投影し、その結果、10 進数のコレクションが生成されます。  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
