---
title: サポートされていない式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: af0e00f470584883b6a65b63f2650c1c359b404c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489859"
---
# <a name="unsupported-expressions"></a>サポートされていない式

このトピックで説明でサポートされていない TRANSACT-SQL 式[!INCLUDE[esql](../../../../../../includes/esql-md.md)]します。 詳細については、次を参照してください。 [Entity SQL の相違 TRANSACT-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)します。

## <a name="quantified-predicates"></a>定量化された述語

TRANSACT-SQL は、次の形式の構成要素を使用できます。

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

ただし、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、このようなコンストラクターがサポートされていません。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、これに相当する式を次のように記述できます。

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* 演算子

TRANSACT-SQL の使用をサポートする、* をすべての列を予測するかを示すために、SELECT 句での演算子。これは [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていません。

## <a name="see-also"></a>関連項目

- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Entity SQL と Transact-SQL の相違点](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
