---
title: 変数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248689"
---
# <a name="variables-entity-sql"></a>変数 (Entity SQL)
## <a name="variable"></a>変数  
 変数式は、現在のスコープで定義されている名前付きの式への参照です。 変数参照は、[識別子](identifiers-entity-sql.md)で定義[!INCLUDE[esql](../../../../../../includes/esql-md.md)]されている有効な識別子である必要があります。  
  
 次の例は、式における変数の使用方法を示しています。 FROM 句の `c` は変数の定義です。 SELECT 句内で使用された `c` は、変数参照を表します。  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>関連項目

- [識別子](identifiers-entity-sql.md)
- [パラメーター](parameters-entity-sql.md)
- [Entity SQL の概要](entity-sql-overview.md)
