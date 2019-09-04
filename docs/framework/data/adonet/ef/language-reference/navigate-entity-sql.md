---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249939"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

エンティティ間で確立されたリレーションシップをナビゲートします。

## <a name="syntax"></a>構文

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>引数

`instance-expression`エンティティのインスタンス。

`relationship-type`概念スキーマ定義言語 (CSDL) ファイルからのリレーションシップの型名。 は > 名前空間\<として\<修飾されます。`relationship-type`リレーションシップの種類の名前 >。

`to`リレーションシップの末尾。

`from`リレーションシップの先頭。

## <a name="return-value"></a>戻り値

終端のカーディナリティが 1 の場合、戻り値は `Ref<T>` になります。 終端のカーディナリティが n の場合、戻り値は `Collection<Ref<T>>` になります。

## <a name="remarks"></a>Remarks

リレーションシップは、Entity Data Model (EDM) のファーストクラスの構造体です。 リレーションシップは、複数のエンティティ型の間で確立され、ユーザーはエンティティ間のリレーションシップをナビゲートできます。 `from` と `to` は、リレーションシップ内の名前解決があいまいでない場合の条件付きのオプションです。

NAVIGATE は、O および C 空間で有効です。

ナビゲーション構造の一般的な形式は次のようになります。

navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )

例えば:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

ここで、OrderCustomer は `relationship`であり、Customer と Order はリレーションシップの `to-end` (顧客) と `from-end` (注文) です。 Ordercustomer が n:1 のリレーションシップである場合、navigate 式の結果の型は Ref\<customer > になります。

この式をより簡略化すると、次のようになります。

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

同様に、次の形式のクエリでは、navigate 式によって、> >\<参照順序 < コレクションが生成されます。

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

インスタンス式は、エンティティ/参照型になる必要があります。

## <a name="example"></a>例

次の Entity SQL クエリでは、NAVIGATE 演算子を使用して、Address エンティティ型と SalesOrderHeader エンティティ型間で確立されたリレーションシップをナビゲートします。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。

1. [「方法:StructuralType の結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)を返すクエリを実行します。

2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [方法: Navigate 演算子を使用したリレーションシップのナビゲート](navigate-entity-sql.md)
