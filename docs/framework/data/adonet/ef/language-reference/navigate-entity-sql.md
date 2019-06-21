---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 6ce88cecf210d8b3cf541fe7e870e19a59e344ec
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307336"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

エンティティ間で確立されたリレーションシップをナビゲートします。

## <a name="syntax"></a>構文

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>引数

`instance-expression` エンティティのインスタンス。

`relationship-type` 概念スキーマ定義言語 (CSDL) ファイルから、リレーションシップの型名。 `relationship-type`として修飾されます\<名前空間 >.\<リレーションシップ型の名前 >。

`to` リレーションシップの end。

`from` リレーションシップの開始。

## <a name="return-value"></a>戻り値

終端のカーディナリティが 1 の場合、戻り値は `Ref<T>` になります。 終端のカーディナリティが n の場合、戻り値は `Collection<Ref<T>>` になります。

## <a name="remarks"></a>Remarks

関係は、Entity Data Model (EDM) 内の最上位の構造です。 リレーションシップは、複数のエンティティ型の間で確立され、ユーザーはエンティティ間のリレーションシップをナビゲートできます。 `from` と `to` は、リレーションシップ内の名前解決があいまいでない場合の条件付きのオプションです。

NAVIGATE は、O および C 空間で有効です。

ナビゲーション構造の一般的な形式は次のようになります。

navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )

例:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

ここで、OrderCustomer は `relationship`であり、Customer と Order はリレーションシップの `to-end` (顧客) と `from-end` (注文) です。 OrderCustomer が n:1 リレーションシップとしている場合、ナビゲーション式の結果型は Ref\<顧客 >。

この式をより簡略化すると、次のようになります。

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

同様に、クエリでは、次の形式のナビゲーション式はコレクションを生成 < Ref\<順序 >> します。

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

インスタンス式は、エンティティ/参照型になる必要があります。

## <a name="example"></a>例

次の Entity SQL クエリでは、NAVIGATE 演算子を使用して、Address エンティティ型と SalesOrderHeader エンティティ型間で確立されたリレーションシップをナビゲートします。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。

1. 」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。

2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [方法: 移動 Navigate 演算子でリレーションシップ](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
