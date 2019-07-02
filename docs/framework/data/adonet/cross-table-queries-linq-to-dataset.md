---
title: 複数テーブルにまたがるクエリ (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: ed860b60add288899ac6f97429b2f01577ee392a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504070"
---
# <a name="cross-table-queries-linq-to-dataset"></a>複数テーブルにまたがるクエリ (LINQ to DataSet)
に加えて、1 つのテーブルのクエリを実行するには、LINQ to DataSet でテーブルにまたがるクエリを実行することもできます。 これを使用する*結合*します。 結合とは、あるデータ ソース内のオブジェクトを、他方のデータ ソース内で共通の属性 (たとえば製品や連絡先 ID) を持つオブジェクトと関連付けることです。 オブジェクト指向プログラミングでは、それぞれのオブジェクトは別のオブジェクトを参照するメンバーを持つため、オブジェクト間のリレーションシップのナビゲーションは比較的簡単です。 ただし、外部データベース テーブル内でのリレーションシップのナビゲーションは単純ではありません。 データベース テーブルは、組み込みのリレーションシップを持ちません。 このようなケースでは、結合操作を使用して、互いのソースの要素を対応付けることができます。 たとえば、製品情報と売上情報が 2 つのテーブルに格納されている場合、結合操作を使用して、同じ販売注文の売上情報と製品を対応付けることができます。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework には 2 つの結合演算子は、<xref:System.Linq.Enumerable.Join%2A>と<xref:System.Linq.Enumerable.GroupJoin%2A>します。 これらの演算子実行*等結合*: 結合の 2 つのデータに一致するは、ソースが、キーが等しい場合のみです。 (これに対し、演算子の結合 TRANSACT-SQL サポート以外の`equals`など、`less than`演算子です)。  
  
 リレーショナル データベース用語では、<xref:System.Linq.Enumerable.Join%2A> は内部結合を実行します。 内部結合とは、対応するデータセット内で一致するオブジェクトがあるオブジェクトのみが返される結合です。  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A>内部結合と左外部結合のスーパー セットの実装は演算子リレーショナル データベース用語で直接相当するものがありません。 左外部結合は 2 番目のコレクションの要素と相関関係があるない場合でも、最初 (左側) のコレクションの各要素を返す結合です。  
  
 結合の詳細については、次を参照してください。[の結合操作](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))します。  
  
## <a name="example"></a>例  
 次の例では、AdventureWorks サンプル データベースの `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルを従来の方法で結合し、8 月以降のオンラインでの注文を取得します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>関連項目

- [DataSet のクエリ](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [単一テーブルのクエリ](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
- [型指定された DataSet のクエリ](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [結合演算](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
