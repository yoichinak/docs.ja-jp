---
title: 結合操作 (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: 95661e2d0d7f4f0e75c1fa1b10e1f322923189b1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592083"
---
# <a name="join-operations-c"></a>結合操作 (C#)
2 つのデータ ソースの "*結合*" とは、あるデータ ソースのオブジェクトを、共通の属性を共有する別のデータ ソースのオブジェクトと関連付けることです。  
  
 相互に直接の関連がない 2 つのデータ ソースを対象とするクエリにおいて、結合は重要な操作になります。 オブジェクト指向プログラミングでは、これは一方向の関係における逆の方向など、モデル化されていないオブジェクト間の相関関係を意味する場合があります。 一方向の関係の例として、City 型のプロパティを持つ Customer クラスがあるとします。ただし、City クラスには、Customer オブジェクトのコレクションを表すプロパティはありません。 City オブジェクトのリストから各都市のすべての顧客を取得する場合は、結合演算を使用して顧客を検索できます。  
  
 LINQ framework で用意された結合メソッドは <xref:System.Linq.Enumerable.Join%2A> と <xref:System.Linq.Enumerable.GroupJoin%2A> です。 この 2 つのメソッドは、等結合 (キーが等しいかどうかに基づいて 2 つのデータ ソースを対応させる結合) を実行します。 (比較に関して、Transact-SQL では、"小なり" 演算子などの "等値" 以外の結合演算子もサポートされます)。リレーショナル データベース用語で説明すると、<xref:System.Linq.Enumerable.Join%2A> は内部結合 (両方のデータ セットで一致するオブジェクトだけが返される結合) を実装します。 リレーショナル データベース用語で <xref:System.Linq.Enumerable.GroupJoin%2A> メソッドに直接相当するものはありませんが、このメソッドは内部結合と左外部結合のスーパーセットを実装します。 左外部結合とは、最初 (左側) のデータ ソースの各要素を返す結合です。これらの要素は、もう一方のデータ ソースの要素と相関関係がなくても返されます。  
  
 次の図は、2 つのセットと、内部結合または左外部結合としてこれらのセットに含まれている要素の概念図を示しています。  
  
 ![内側&#47;外側を示す 2 つの重なり合う円。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|C# のクエリ式の構文|詳細情報|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|キー セレクター関数に基づいて 2 つのシーケンスを結合し、値のペアを抽出します。|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|キー セレクター関数に基づいて 2 つのシーケンスを結合し、各要素について結果として得られる一致をグループ化します。|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq>
- [標準クエリ演算子の概要 (C#)](./standard-query-operators-overview.md)
- [匿名型](../../classes-and-structs/anonymous-types.md)
- [結合およびクロス積クエリの作成](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join 句](../../../language-reference/keywords/join-clause.md)
- [方法: 複合キーを使用した結合](../../linq-query-expressions/how-to-join-by-using-composite-keys.md)
- [方法: 異種ファイルのコンテンツを結合する (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [方法: Join 句の結果の順序指定](../../linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [方法: カスタム結合操作の実行](../../linq-query-expressions/how-to-perform-custom-join-operations.md)
- [方法: グループ結合の実行](../../linq-query-expressions/how-to-perform-grouped-joins.md)
- [方法: 内部結合の実行](../../linq-query-expressions/how-to-perform-inner-joins.md)
- [方法: 左外部結合の実行](../../linq-query-expressions/how-to-perform-left-outer-joins.md)
- [方法: 複数のソースからオブジェクト コレクションにデータを設定する (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
