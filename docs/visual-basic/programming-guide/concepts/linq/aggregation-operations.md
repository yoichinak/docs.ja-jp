---
title: 集計操作 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: fe39c2efb5d9f24a7d9d5240b20a9ca687ed1aa9
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202185"
---
# <a name="aggregation-operations-visual-basic"></a>集計操作 (Visual Basic)
集計の操作では、値の集合体から単一の値が計算されます。 たとえば、1 か月分の毎日の気温値から 1 日あたりの平均の気温値を計算することが集計操作です。  
  
 次の図は、数値のシーケンスに対する 2 つの集計処理の結果を示しています。 最初の処理で数値が合計されます。 2 つ目の処理でシーケンスの最大値が返されます。  
  
 ![LINQ の集計処理](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 次のセクションでは、集計処理を実行する標準クエリ演算子メソッドの一覧を示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Aggregate|コレクションの値に対してカスタム集計処理を実行します。|該当なし。|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|平均|値のコレクションの平均値を計算します。|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|カウント|コレクションの要素数をカウントします。述語関数を満たす要素のみをカウントすることもできます。|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|大規模なコレクションの要素数をカウントします。述語関数を満たす要素のみをカウントすることもできます。|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|最大|コレクション内の最大値を決定します。|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|最小|コレクション内の最小値を決定します。|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Sum|コレクション内にある値の合計を計算します。|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>クエリ式の構文例  
  
### <a name="average"></a>平均  
 次のコード例では、`Aggregate Into Average`温度を表す数値の配列の平均温度を計算する Visual Basic での句。  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>カウント  
 次のコード例では、 `Aggregate Into Count` 80 以上である、配列の値の数をカウントする Visual Basic での句。  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 次のコード例では、`Aggregate Into LongCount`句は、配列の値の数をカウントします。  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>最大  
 次のコード例では、`Aggregate Into Max`温度を表す数値の配列の最大の温度を計算する句。  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>最小  
 次のコード例では、`Aggregate Into Min`温度を表す数値の配列の最小の温度を計算する句。  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>Sum  
 次のコード例では、`Aggregate Into Sum`経費を表す値の配列から経費合計金額を計算する句。  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Linq>
- [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [方法: CSV テキスト ファイル (LINQ) (Visual Basic) で列の値を計算します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [方法: 数、合計、または平均データ](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [方法: クエリ結果内の最小値と最大値を検索します。](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [方法: 最大ファイルまたはディレクトリ ツリー (LINQ) (Visual Basic) 内のファイルのクエリ](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数をクエリ](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
