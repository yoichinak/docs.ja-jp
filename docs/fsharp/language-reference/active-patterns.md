---
title: アクティブ パターン
description: アクティブ パターンを使用して、F# プログラミング言語で入力データを分割する名前付きのパーティションを定義する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 0f1f57de425836738201d2d8f84ab67a0df142ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772751"
---
# <a name="active-patterns"></a>アクティブ パターン

*アクティブ パターン*パターン一致式の判別共用体と同様に、これらの名前を使用できるように、入力のデータを分割する名前付きパーティションを定義できます。 アクティブ パターンを使用すると、パーティションごとにカスタマイズした方法でデータを分解できます。

## <a name="syntax"></a>構文

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Remarks

前の構文では、識別子は、名前で表される入力データのパーティションに*引数*、または、つまり、名、引数のすべての値のセットのサブセットをします。 アクティブ パターン定義で最大 7 つのパーティションがあります。 *式*をデータを分解する形式について説明します。 名前付きのパーティションのうちに引数が属しているように指定された値を決定する規則を定義するのにアクティブ パターンの定義を使用することができます。 (| と |) 記号と呼びます*バナナ クリップ*この種類の let バインドによって作成された関数が呼び出されると、*認識エンジンのアクティブな*します。

たとえば、引数を持つアクティブ パターンを検討してください。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

アクティブ パターンは、次の例のように、式に一致するパターンで使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

このプログラムの出力は次のとおりです。

```
7 is odd
11 is odd
32 is even
```

アクティブ パターンの別の使用など、同じ基になるデータがさまざまな可能な表現を持っている場合、複数の方法でデータ型を分解することです。 たとえば、`Color`オブジェクトは、RGB 表現や、HSB 表現に分解する可能性があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

上記のプログラムの出力は次のとおりです。

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

組み合わせでは、アクティブ パターンを使用してこれら 2 つの方法はパーティションに有効にする、適切なフォームだけにデータを分解し、計算のため最も便利な形式で適切なデータに対して適切な計算を実行します。

結果として得られるパターン マッチング式は、非常に判読しやすくに大幅に簡素化する可能性のある複雑な分岐構造とデータ分析のコードは、便利な方法で書き込まれるデータを有効にします。

## <a name="partial-active-patterns"></a>部分的なアクティブ パターン

場合によっては、入力領域の一部のみをパーティション分割する必要があります。 その場合は、うちのいくつかの入力に一致が他の入力と一致しない部分のパターンのセットを作成します。 常に値を生成しないアクティブ パターンが呼び出される*アクティブ パターンの部分的な*; オプションの種類である戻り値があります。 ワイルドカード文字を使用する部分的なアクティブ パターンを定義する (\_) バナナ クリップ内のパターンの一覧の最後にします。 次のコードでは、部分的なアクティブ パターンの使用を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

前の例の出力は次のとおりです。

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

部分的なアクティブ パターンを使用する場合、個々 の選択肢があります不整合のあるまたは相互に排他的ですが、必要はありません。 次の例では、パターンの四角形とキューブのパターンのない不整合のある、いくつかの数字は四角形と、64 などのキューブの両方であるためです。 次のプログラムは、四角形と立方パターンを組み合わせて、AND パターンを使用します。 これは、最大 1,000 両方平方和、キューブとキューブのみであるものであるすべての整数を出力します。 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

出力は次のとおりです。

```
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a>パラメーター化されたアクティブ パターン

アクティブ パターンは、常に一致する項目の少なくとも 1 つの引数を受け取りますが、この場合、名前でも、追加の引数がかかる*パラメーター化されたアクティブ パターン*適用されます。 追加の引数は、特殊化する一般的なパターンを使用できます。 たとえば、多くの場合、文字列を解析する正規表現を使用するアクティブ パターンに含める部分アクティブ パターンを使用する次のコードのように、追加のパラメーターとして正規`Integer`上記のコード例で定義されています。 この例では、一般的なである ParseRegex アクティブ パターンをカスタマイズする正規表現を使用して、さまざまな日付形式の文字列が与えられます。 一致した文字列を DateTime コンス トラクターに渡すことができる整数に変換するには、整数アクティブ パターンを使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

前のコードの出力は次のとおりです。

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

アクティブ パターンは、パターン マッチング式のみに制限することはありません、let バインドで使用することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

前のコードの出力は次のとおりです。

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [match 式](match-expressions.md)
