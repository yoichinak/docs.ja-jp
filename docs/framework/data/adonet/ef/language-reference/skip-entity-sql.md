---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: b6335086ce5b61cf23db2bf967d1a82f322e83b3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043617"
---
# <a name="skip-entity-sql"></a>SKIP (Entity SQL)

物理的なページングは、ORDER BY 句の SKIP サブ句を使用して実行できます。 SKIP を ORDER BY 句と切り離して使用することはできません。

## <a name="syntax"></a>構文

```
[ SKIP n ]
```

## <a name="arguments"></a>引数

`n` \
スキップするアイテムの数。

## <a name="remarks"></a>Remarks

SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。 たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。

> [!NOTE]
> TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは無効です。 TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。

> [!NOTE]
> SQL Server 2000 では、キー以外の列で ORDER BY と共に SKIP を使用すると、正しくない結果が返される可能性があります。 キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。 これは、SQL Server 2000 に対する SKIP の変換方法によるものです。 たとえば、次のコードでは、 `E.NonKeyColumn` に重複値が存在する場合、5 行を超える行はスキップされます。
>
> `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`

次[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の[ようにクエリを実行します。クエリ結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))のページでは、ORDER BY 演算子と SKIP を使用して、SELECT ステートメントで返されるオブジェクトで使用される並べ替え順序を指定します。

## <a name="see-also"></a>関連項目

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [方法: クエリ結果のページ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [ページング](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
