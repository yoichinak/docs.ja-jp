---
title: 集計処理 (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: 04415c430059057cef26b3750faa03b925cfa994
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594985"
---
# <a name="aggregation-operations-c"></a>集計処理 (C#)
集計の操作では、値の集合体から単一の値が計算されます。 たとえば、1 か月分の毎日の気温値から 1 日あたりの平均の気温値を計算することが集計操作です。  
  
 次の図は、数値のシーケンスに対する 2 つの集計処理の結果を示しています。 最初の処理で数値が合計されます。 2 つ目の処理でシーケンスの最大値が返されます。  
  
 ![LINQ 集計操作を示す図。](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 次のセクションでは、集計処理を実行する標準クエリ演算子メソッドの一覧を示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|C# のクエリ式の構文|詳細情報|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Aggregate|コレクションの値に対してカスタム集計処理を実行します。|適用不可。|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|平均|値のコレクションの平均値を計算します。|適用不可。|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Count|コレクションの要素数をカウントします。述語関数を満たす要素のみをカウントすることもできます。|適用不可。|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|大規模なコレクションの要素数をカウントします。述語関数を満たす要素のみをカウントすることもできます。|適用不可。|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|最大|コレクション内の最大値を決定します。|適用不可。|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min|コレクション内の最小値を決定します。|適用不可。|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|合計|コレクション内にある値の合計を計算します。|適用不可。|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq>
- [標準クエリ演算子の概要 (C#)](./standard-query-operators-overview.md)
- [方法: CSV テキスト ファイルの列値を計算する (LINQ) (C#)](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [方法: 一連のフォルダーの合計バイト数を照会する (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
