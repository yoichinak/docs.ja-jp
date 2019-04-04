---
title: ページング (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 1cc7b0ff931e0772cbdfc0f278b75153558efda6
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825993"
---
# <a name="paging-entity-sql"></a>ページング (Entity SQL)
物理的なページングを使用して実行できる、[スキップ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)と[制限](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)でサブ句、 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)句。 物理的ページングを決定的に実行するには、SKIP と LIMIT を使用する必要があります。 使用する必要がある、非確定的な方法で、結果内の行の数を制限する場合は、[上部](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)します。 TOP および SKIP/LIMIT は、同時には指定できません。  
  
## <a name="top-overview"></a>TOP の概要  
 SELECT 句には、オプションの ALL/DISTINCT 修飾子に続けてオプションの TOP サブ句を指定できます。 TOP サブ句は、クエリ結果の先頭から指定した行セットだけを返すよう指定します。 詳細については、[上部](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)を参照してください。  
  
## <a name="skip-and-limit-overview"></a>SKIP/LIMIT の概要  
 SKIP と LIMIT は ORDER BY 句の一部です。 SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。 たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。 LIMIT 式のサブ句が ORDER BY 句に存在する場合、クエリは並べ替え順序に従って並べ替えられ、結果の行数は LIMIT 式によって制限されます。 たとえば、LIMIT 5 は、結果セットを 5 つのインスタンスまたは行に制限します。 SKIP と LIMIT を同時に使用することはできません。SKIP のみまたは LIMIT のみを ORDER BY 句と一緒に使用できます。 詳細については、次のトピックを参照してください。  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>関連項目
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [方法: クエリ結果 ページ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
