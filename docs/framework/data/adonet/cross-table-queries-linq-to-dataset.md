---
title: 複数テーブルにまたがるクエリ (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 4ab8eb9988995b4a142b1c02e82476f45285c3b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785616"
---
# <a name="cross-table-queries-linq-to-dataset"></a>複数テーブルにまたがるクエリ (LINQ to DataSet)
1つのテーブルに対してクエリを実行するだけでなく、LINQ to DataSet でクロステーブルクエリを実行することもできます。 これを行うには、*結合*を使用します。 結合とは、あるデータ ソース内のオブジェクトを、他方のデータ ソース内で共通の属性 (たとえば製品や連絡先 ID) を持つオブジェクトと関連付けることです。 オブジェクト指向プログラミングでは、それぞれのオブジェクトは別のオブジェクトを参照するメンバーを持つため、オブジェクト間のリレーションシップのナビゲーションは比較的簡単です。 ただし、外部データベース テーブル内でのリレーションシップのナビゲーションは単純ではありません。 データベース テーブルは、組み込みのリレーションシップを持ちません。 このようなケースでは、結合操作を使用して、互いのソースの要素を対応付けることができます。 たとえば、製品情報と売上情報が 2 つのテーブルに格納されている場合、結合操作を使用して、同じ販売注文の売上情報と製品を対応付けることができます。  
  
 フレームワーク[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]には、とと<xref:System.Linq.Enumerable.GroupJoin%2A>いう<xref:System.Linq.Enumerable.Join%2A> 2 つの結合演算子が用意されています。 これらの演算子は、*等結合*を実行します。つまり、2つのデータソースに一致する結合は、キーが等しい場合に限ります。 これに対して、transact-sql では、 `equals` `less than`演算子など、以外の結合演算子もサポートされています。  
  
 リレーショナル データベース用語では、<xref:System.Linq.Enumerable.Join%2A> は内部結合を実行します。 内部結合とは、対応するデータセット内で一致するオブジェクトがあるオブジェクトのみが返される結合です。  
  
 これら<xref:System.Linq.Enumerable.GroupJoin%2A>の演算子は、リレーショナルデータベースの用語に直接相当するものではなく、内部結合と左外部結合のスーパーセットを実装します。 左外部結合は、2番目のコレクションに相関要素がない場合でも、最初 (左側) のコレクションの各要素を返す結合です。  
  
 結合の詳細については、「 [Join 操作](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、AdventureWorks サンプル データベースの `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルを従来の方法で結合し、8 月以降のオンラインでの注文を取得します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>関連項目

- [DataSet のクエリ](querying-datasets-linq-to-dataset.md)
- [単一テーブルのクエリ](single-table-queries-linq-to-dataset.md)
- [型指定された DataSet のクエリ](querying-typed-datasets.md)
- [結合演算](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [LINQ to DataSet の例](linq-to-dataset-examples.md)
