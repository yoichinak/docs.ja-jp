---
title: 演算子の優先順位 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 722ebe5f0ec530f8c7f86e9f9901451b060903f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159134"
---
# <a name="operator-precedence-entity-sql"></a>演算子の優先順位 (Entity SQL)
ときに、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]クエリが複数の演算子、演算子の優先順位は、操作が実行されるシーケンスを決定します。 実行される順序により、クエリ結果の値は大きく変わります。  
  
 演算子には、次の表に示す優先順位レベルが定義されています。 優先順位が高い演算子は、優先順位が低い演算子よりも前に評価されます。  
  
|レベル|演算の種類|演算子|  
|-----------|--------------------|--------------|  
|1|1 次式|`. , [] ()`|  
|2|単項|`! not`|  
|3|乗法|`* / %`|  
|4|加法|`+ -`|  
|5|順序|`< > <= >=`|  
|6|等価比較|`= != <>`|  
|7|条件 AND|`and &&`|  
|8|条件 OR|`or &#124;&#124;`|  
  
 式の中の 2 つの演算子が同じ優先順位レベルである場合は、クエリの中での位置に従って演算子は左から右へと評価されます。 たとえば、`x+y-z` は `(x+y)-z` と評価されます。  
  
 クエリの中で演算子の定義済みの優先順位をオーバーライドするには、かっこを使用します。 この場合、かっこ内のすべての演算が評価され、1 つの結果が作成されてから、かっこ外の演算子でこの結果が使用されます。 たとえば、`x+y*z`を乗算します`y`によって`z`し追加します`x`が`(x+y)*z`を追加します`x`に`y`には、結果を乗算`z`。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
