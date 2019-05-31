---
title: インデックスと範囲を使用してデータの範囲を調べる
description: この高度なチュートリアルでは、インデックスと範囲を使用してデータを調べ、シーケンシャル データ セットのスライスを調べる方法について説明します。
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 64fae4581e265d4f70b8356d5c651b4fdaca3fe9
ms.sourcegitcommit: dd3b897feb5c4ac39732bb165848e37a344b0765
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2019
ms.locfileid: "64431500"
---
# <a name="indices-and-ranges"></a>インデックスと範囲

範囲とインデックスには、<xref:System.Array>、<xref:System.Span%601>、または <xref:System.ReadOnlySpan%601> 内の 1 つの要素または範囲にアクセスできる簡潔な構文が用意されています。 これらの機能を使用すると、簡潔でわかりやすい構文でシーケンス内の各要素または要素の範囲にアクセスできるようになります。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
> * シーケンス内の範囲に構文を使用します。
> * 各シーケンスの開始と終了に関する設計上の決定について説明します。
> * <xref:System.Index> 型と <xref:System.Range> 型のシナリオについて説明します。

## <a name="language-support-for-indices-and-ranges"></a>インデックスと範囲の言語サポート

インデックスの前に `^` 文字を使用すると、**末尾から**インデックスを指定できます。 末尾からのインデックス付けは、`0..^0` で範囲全体を指定するという規則から始まります。 配列全体を列挙するには、"*最初の要素*" から開始し、"*最後の要素を過ぎる*" まで続けます。 列挙子に対する `MoveNext` メソッドの動作を考えてみてください。列挙子から末尾の要素が渡されると、メソッドから false が返されます。 インデックス `^0` は、"末尾"、`array[array.Length]`、つまり末尾の要素の後のインデックスを意味します。 `array[2]` が "先頭から 2 番目" の要素を意味することには慣れているでしょう。 今後、`array[^2]` は "末尾から 2 番目" の要素を意味するようになります。 

**範囲**は、**範囲演算子** `..` を使用して指定できます。 たとえば、`0..^0` は配列の範囲全体を指定します。0 は先頭からですが、末尾の 0 は含まれません。 どちらのオペランドでも、"先頭から" または "末尾から" を使用できます。 さらに、どちらのオペランドも省略できます。 先頭インデックスの既定値は `0`、末尾インデックスの既定値は `^0` です。

```csharp-interactive
string[] words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

各要素のインデックスによって "先頭から" と "末尾から" の概念が強調されており、その範囲では範囲の末尾が除外されています。 配列全体の "先頭" は最初の要素です。 配列全体の "末尾" は、最後の要素の "*後*" です。

末尾の単語は `^1` インデックスで取得できます。 初期化の下に次のコードを追加します。

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

次のコードでは、単語 "quick"、"brown"、"fox" から成る部分範囲が作成されます。 それには、`words[1]` から `words[3]` までが含まれます。 要素 `words[4]` が範囲内にありません。 同じメソッドに次のコードを追加します。 それをコピーして、対話型ウィンドウの下部に貼り付けます。

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

次のコードでは、"lazy" と "dog" の部分範囲が作成されます。 それには、`words[^2]` と `words[^1]` が含まれます。 末尾インデックス `words[^0]` は含まれません。 次のコードも追加します。

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

次の例では、先頭と末尾の一方または両方が開いている範囲が作成されます。

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

範囲やインデックスを変数として宣言することもできます。 この変数は、文字 `[` と `]` の内側で使用できます。

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

前の例は、さらに説明が必要な 2 つの設計上の決定を示しています。

- 範囲は*排他*です。つまり、末尾のインデックスの要素が範囲内にありません。
- インデックス `^0` は、コレクションの "*末尾の要素*" ではなく、コレクションの "*末尾*" です。

次のサンプルは、こうした選択肢の理由の多くを示しています。 `x`、`y`、`z` を変更してさまざまな組み合わせを試してください。 実験するときには、有効な組み合わせになるように `x` が `y` 未満の値、`y` が `z` 未満の値を使用します。 新しいメソッドに次のコードを追加します。 さまざまな組み合わせを試してください。

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>インデックスと範囲のシナリオ

シーケンス全体の一部の範囲について何らかの分析を行う場合は、範囲とインデックスを使用することがよくあります。 どの部分の範囲が関係しているかを正確に読み取る場合に、この新しい構文の方が明確です。 ローカル関数 `MovingAverage` は、引数として <xref:System.Range> を受け取ります。 このメソッドでは、最小値、最大値、および平均値を計算するときに、その範囲のみが列挙されます。 プロジェクトで次のコードを試してみてください。

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

完成したコードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) リポジトリからダウンロードできます。
