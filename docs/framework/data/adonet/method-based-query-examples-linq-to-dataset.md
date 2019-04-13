---
title: メソッド ベースのクエリ例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
ms.openlocfilehash: 9419bd664a0e918b1ed40e5d468d01cf724f054d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139803"
---
# <a name="method-based-query-examples-linq-to-dataset"></a>メソッド ベースのクエリ例 (LINQ to DataSet)
このセクションでは、データセットに LINQ をプログラミングの標準クエリ演算子を使用するメソッド ベースのクエリ構文例を提供します。 <xref:System.Data.DataSet>これらの例で使用されるを使用して設定されますが、`FillDataSet`メソッドで指定されている[をデータセットにデータを読み込む](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。 詳細については、次を参照してください。[標準クエリ演算子の概要 (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)または[標準クエリ演算子の概要 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [射影](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Select%2A> メソッドおよび <xref:System.Linq.Enumerable.SelectMany%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
 [パーティション分割](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Skip%2A> メソッドおよび <xref:System.Linq.Enumerable.Take%2A> メソッドを使って <xref:System.Data.DataSet> を照会し、結果をパーティション分割する例を取り上げます。  
  
 [順序](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A>、<xref:System.Linq.Enumerable.ThenByDescending%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、結果を並べ替える例を取り上げます。  
  
 [集合演算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A>、<xref:System.Linq.Enumerable.Union%2A> の各演算子を使って、データ行の集合に対する値ベースの比較操作を実行する例を取り上げます。  
  
 [変換演算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A>、<xref:System.Linq.Enumerable.ToList%2A> の各メソッドを使ってクエリ式を即時実行する例を示しています。  
  
 [要素演算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.First%2A> メソッドおよび <xref:System.Linq.Enumerable.ElementAt%2A> メソッドを使用して <xref:System.Data.DataRow> から <xref:System.Data.DataSet> 要素を取得する例を取り上げます。  
  
 [集計演算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Sum%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、データを集計する例を取り上げます。  
  
 [Join](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.GroupJoin%2A> メソッドおよび <xref:System.Linq.Enumerable.Join%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
## <a name="see-also"></a>関連項目

- [クエリ式の例](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)
- [DataSet 固有の演算子の例](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)
- [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
