---
title: セット操作 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 8ec7f2785617c354a1aa506ac0df9eef7d051b59
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679295"
---
# <a name="set-operations-visual-basic"></a>セット操作 (Visual Basic)
LINQ のセット操作は、同一または別個のコレクション (またはセット) に等しい要素があるかどうかに基づいて、結果を生成するクエリ操作です。  
  
 次のセクションでは、セット操作を実行する標準クエリ演算子のメソッドの一覧を示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|コレクションから重複する値を削除します。|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|除く|差集合 (一方のコレクションにだけ存在し、もう一方のコレクションには出現しない要素) を返します。|該当なし。|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|交差|積集合 (2 つのコレクションのそれぞれに出現する要素) を返します。|該当なし。|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|和集合|和集合 (2 つのコレクションのどちらかに出現する一意の要素) を返します。|該当なし。|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>セット操作の比較  
  
### <a name="distinct"></a>Distinct  
 次の図は、文字のシーケンスに対する <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> メソッドの動作を示しています。 返されたシーケンスには、入力シーケンスからの一意の要素が格納されています。  
  
 ![Distinct&#40;&#41; の動作を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")  
  
### <a name="except"></a>除く  
 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> の動作を次の図に示します。 返されたシーケンスには、1 つ目の入力シーケンスのうち、2 つ目の入力シーケンスには存在しない要素が格納されています。  
  
 ![アクションを示すグラフィックを除く&#40;&#41;します。](./media/set-operations/except-behavior-graphic.png "の動作を除く。")  
  
### <a name="intersect"></a>交差  
 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> の動作を次の図に示します。 返されたシーケンスには、両方の入力シーケンスに共通する要素が格納されています。  
  
 ![2 つのシーケンスの交差部分を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>和集合  
 次の図は、2 つの文字シーケンスに対する和集合演算を示しています。 返されたシーケンスには、両方の入力シーケンスからの一意の要素が格納されています。  
  
 ![2 つのシーケンスの結合を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## <a name="query-expression-syntax-example"></a>クエリ式の構文例  
 次の例では、`Distinct`を整数のリストから一意の番号を返す LINQ クエリ内の句。  
  
 [!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Linq>
- [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Distinct 句](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [方法: 結合および比較文字列のコレクション (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [方法: 2 つのリスト (LINQ) (Visual Basic) の差集合を見つける](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
