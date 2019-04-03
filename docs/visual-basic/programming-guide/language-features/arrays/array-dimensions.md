---
title: Visual Basic における配列の次元
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 0b4e7c9e253f94e1e28700c8669d28799ab69d91
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836936"
---
# <a name="array-dimensions-in-visual-basic"></a>Visual Basic における配列の次元
A*ディメンション*は、方向が配列の要素の仕様を変更できます。 月の日付ごとの売上合計を保持する配列には、1 つのディメンション (月の日) があります。 1 か月の日付ごとに売上を部門別合計保持する配列には、2 つのディメンション (部門の番号と月の日) があります。 配列の次元数と呼ばれる、*ランク*します。  
  
> [!NOTE]
>  使用することができます、<xref:System.Array.Rank%2A>プロパティの配列に次元数があります。  
  
## <a name="working-with-dimensions"></a>ディメンションの使用  
 指定することによって、配列の要素を指定する、*インデックス*または*添字*の各次元。 要素は、そのディメンションの最も大きいインデックスをインデックス 0 から各次元の連続しています。  
  
 次の図は、ランクが異なる配列の概念の構造を示しています。 図内の各要素は、これにアクセスするインデックス値を示します。 たとえば、インデックスを指定することで 2 次元配列の 2 つ目の行の最初の要素をアクセス`(1, 0)`します。  
  
 ![1 次元配列を示す図。](./media/array-dimensions/one-dimensional-array.gif)  
  
 ![2 次元の配列を示す図。](./media/array-dimensions/two-dimensional-array.gif)  
  
 ![3 次元の配列を示す図。](./media/array-dimensions/three-dimensional-array.gif)  
  
### <a name="one-dimension"></a>1 つのディメンション  
 多くの配列では、各年齢の人の数などの 1 つだけディメンションを持ちます。 要素を指定する唯一の要件は、その要素数を保持する期間です。 そのため、このような配列は、1 つのみのインデックスを使用します。 次の例を保持する変数の宣言を*1 次元配列*年齢が 0 ~ 120 の有効期間の数します。  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>2 つのディメンション  
 一部の配列では、各ビルのキャンパス内の各床面のオフィスの数など、2 つのディメンションがあります。 要素の仕様は、建物番号と、床面の両方が必要ですし、各要素はビルとフロアの組み合わせの数を保持します。 したがって、このような配列には、2 つのインデックスが使用されます。 次の例を保持する変数の宣言を*2 次元配列*office 数、0 ~ 40 のビルとフロアが 0 ~ 5 の。  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 2 次元配列とも呼ばれますが、*長方形配列*します。  
  
### <a name="three-dimensions"></a>3 つのディメンション  
 いくつかの配列では、3 次元空間内の値などの 3 つのディメンションがあります。 このような配列は、この場合、x、y、および物理領域の z 座標を表す 3 つのインデックスを使用します。 次の例を保持する変数の宣言を*3 次元配列*3 次元のボリュームでのさまざまなポイントでの気温。  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>次の 3 つ以上のディメンション  
 配列には、最大 32 次元できますが、は 3 つ以上あるまれです。  
  
> [!NOTE]
>  配列にディメンションを追加するときに配列に必要な合計ストレージ増大、注意して使用して多次元配列をそのください。  
  
## <a name="using-different-dimensions"></a>別のディメンションを使用します。  
 当月の毎日の売り上げ高を追跡したいとします。 次の例として、月の日付ごとに 1 つを示しています 31 の要素を持つ 1 次元配列を宣言する可能性があります。  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 これで毎日についてだけでなく、1 か月の年の毎月のも、同じ情報を追跡したいとします。 次の例を示します (月) の 12 行と 31 列 (日) の 2 次元配列を宣言する可能性があります。  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 ようになりましたが対象とすると、配列は 1 年以上の情報を保持します。 5 年間の売り上げ高を追跡する場合は、次の例のように 5 レイヤー、12 行は、31 列と 3 次元の配列を宣言できます。  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 各インデックスが 0 から、最大容量の各次元に異なるので、注意してください。`salesAmounts`そのディメンションの 1 つ必要な長さよりも小さいとして宣言されています。 新しい次元ごとに、配列のサイズが増えることにも注意してください。 上記の例では、3 つのサイズは、それぞれ 31、372、および 1,860 要素です。  
  
> [!NOTE]
>  使用せずに配列を作成することができます、`Dim`ステートメントまたは`New`句。 たとえば、呼び出すことができます、<xref:System.Array.CreateInstance%2A>メソッド、または別のコンポーネントをこのように作成された配列、コードを渡すことができます。 このような配列には、0 以外の下限を持つことができます。 常を使用してディメンションの下限の境界をテストすることができます、<xref:System.Array.GetLowerBound%2A>メソッドまたは`LBound`関数。  
  
## <a name="see-also"></a>関連項目

- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [配列のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
