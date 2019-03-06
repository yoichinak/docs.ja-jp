---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: e7c6cf6b67dc3af29f7ca8fb22af419235a9b833
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351646"
---
# <a name="top-entity-sql"></a>TOP (Entity SQL)

SELECT 句には、オプションの ALL/DISTINCT 修飾子に続けてオプションの TOP サブ句を指定できます。 TOP サブ句は、クエリ結果の先頭から指定した行セットだけを返すよう指定します。

## <a name="syntax"></a>構文

```
[ TOP (n) ]
```

## <a name="arguments"></a>引数

`n` 返される行の数を指定する数値式。 `n` は単一の数値リテラルかまたは単一のパラメーターです。

## <a name="remarks"></a>Remarks

TOP 式には、単一の数値リテラルまたは単一のパラメーターを使用してください。 定数リテラルを使用する場合は、リテラルの種類を Edm.Int64 (byte、int16、int32、int64、または Edm.Int64 に昇格可能な型にマップされる任意のプロバイダー型) に暗黙的に昇格でき、その値が 0 以上である必要があります。 それ以外の場合は、例外が発生します。 パラメーターを式として使用する場合は、パラメーター型も Edm.Int64 に暗黙的に昇格できる必要がありますが、パラメーター値は遅延バインドされるため、コンパイル時に実際のパラメーター値は検証されません。

定数 TOP 式の例を以下に示します。

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

パラメーター化された TOP 式の例を次に示します。

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

TOP は、クエリが並べ替えられていない限り、非決定的です。 確定的な結果が必要な場合は、 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) 句の [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) サブ句および [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) サブ句を使用します。 TOP     SKIP/LIMIT

## <a name="example"></a>例

次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは、TOP を使用して、クエリ結果から返される 1 番上の 1 行を指定します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。

1. 」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。

2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a>関連項目

- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
