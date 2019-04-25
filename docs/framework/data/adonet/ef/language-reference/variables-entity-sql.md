---
title: 変数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bf6fa95e38d1eb5817fd67165b6993cbb0755fd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153583"
---
# <a name="variables-entity-sql"></a>変数 (Entity SQL)
## <a name="variable"></a>変数  
 変数式は、現在のスコープで定義されている名前付きの式への参照です。 変数の参照を有効にする必要があります[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別子で定義されている[識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)します。  
  
 次の例は、式における変数の使用方法を示しています。 FROM 句の `c` は変数の定義です。 SELECT 句内で使用された `c` は、変数参照を表します。  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>関連項目

- [識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [パラメーター](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
