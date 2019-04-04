---
title: 量指定子操作 (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 090bc53c3dcedc82972ab7d16fa2968011a7db65
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412254"
---
# <a name="quantifier-operations-c"></a>量指定子操作 (C#)
量指定子操作は、シーケンス内の要素の一部またはすべてが条件を満たしているかどうかを示す <xref:System.Boolean> 値を返します。  
  
 次の図は、2 つの異なるソース シーケンスに対する、2 つの異なる量指定子操作を示しています。 最初の操作では、1 つ以上の要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。 2 番目の操作では、すべての要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。  
  
 ![LINQ 量指定子操作](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 次のセクションでは、量指定子操作を実行する標準クエリ演算子のメソッドの一覧を示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|C# のクエリ式の構文|説明|  
|-----------------|-----------------|---------------------------------|----------------------|  
|すべて|シーケンス内のすべての要素が条件を満たしているかどうかを調べます。|該当なし。|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|どれでも可|シーケンス内のいずれかの要素が条件を満たしているかどうかを調べます。|該当なし。|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|内容|指定した要素がシーケンスに格納されているかどうかを調べます。|該当なし。|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq>
- [標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [方法: 実行時に述語フィルターを動的に指定する](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [方法: 指定された単語のセットを含む文章を照会する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
