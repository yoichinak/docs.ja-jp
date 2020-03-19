---
title: アクティブ パターン
description: アクティブ パターンを使用して、F# プログラミング言語で入力データを細分化する名前付きパーティションを定義する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187060"
---
# <a name="active-patterns"></a>アクティブ パターン

*アクティブなパターン*を使用すると、入力データを細分化する名前付きパーティションを定義できるため、これらの名前を、判別共用体の場合と同じようにパターン一致式で使用できます。 アクティブ パターンを使用すると、パーティションごとにカスタマイズした方法でデータを分解できます。

## <a name="syntax"></a>構文

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>解説

前の構文では、識別子は、引数 、つまり *、引数*のすべての値のセットのサブセットの名前で表される入力データのパーティションの名前です。 アクティブなパターン定義には、最大 7 つのパーティションを含めることができます。 *式*は、データを分解するフォームを表します。 アクティブなパターン定義を使用して、引数として指定された値が属する名前付きパーティションを決定するための規則を定義できます。 (|) 記号は*バナナ クリップ*と呼ばれ、このタイプの let バインドによって作成される関数は*アクティブ な認識エンジン*と呼ばれます。

例として、引数を持つ次のアクティブなパターンを考えてみましょう。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

次の例のように、パターンマッチング式でアクティブなパターンを使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

このプログラムの出力は次のとおりです。

```console
7 is odd
11 is odd
32 is even
```

アクティブパターンのもう 1 つの用途は、基になるデータにさまざまな表現がある場合など、複数の方法でデータ型を分解することです。 たとえば、オブジェクトを`Color`RGB 表現または HSB 表現に分解できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

上記のプログラムの出力は次のとおりです。

```console
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

この 2 つのアクティブ パターンを組み合わせて使用すると、データを適切な形式に分割して分解し、計算に最も便利な形式で適切なデータに対して適切な計算を実行できます。

結果として得られるパターン・マッチング式により、データを非常に読みやすく、複雑な分岐やデータ分析コードを大幅に簡素化する便利な方法でデータを書き込むことが可能になります。

## <a name="partial-active-patterns"></a>部分的なアクティブ パターン

場合によっては、入力スペースの一部だけをパーティション分割する必要があります。 その場合は、一連の部分パターンを記述し、各パターンは一部の入力に一致しますが、他の入力と一致しません。 常に値を生成しないアクティブなパターンは *、部分アクティブパターン*と呼ばれます。これらの値には、オプション型の戻り値があります。 部分的にアクティブなパターンを定義するには、バナナクリップ内の\_パターンリストの最後にワイルドカード文字 () を使用します。 次のコードは、部分的なアクティブ パターンの使用を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

前の例の出力は次のとおりです。

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

部分的なアクティブパターンを使用する場合、個々の選択肢が分離または相互に排他的である場合がありますが、必要はありません。 次の例では、一部の数値は 64 などの正方形と立方体の両方であるため、パターンの正方形とパターン Cube は不整合ではありません。 次のプログラムでは、AND パターンを使用して、四角形と立方体のパターンを組み合わせます。 これは、正方形とキューブの両方である1000までの整数と、唯一のキューブである整数を出力します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

出力は次のようになります。

```console
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

## <a name="parameterized-active-patterns"></a>パラメータ化されたアクティブ パターン

アクティブパターンは、常に、一致する項目に対して少なくとも 1 つの引数を取りますが、追加の引数を取ることがあり、その場合は *、名前パラメーター化されたアクティブパターン*が適用されます。 追加の引数を使用すると、一般的なパターンを特殊化できます。 たとえば、正規表現を使用して文字列を解析するアクティブ パターンには、次のコード`Integer`のように正規表現が追加のパラメーターとして含まれることがよくあります。 この例では、さまざまな日付形式に正規表現を使用する文字列を指定して、一般的な ParseRegex アクティブ パターンをカスタマイズします。 整数アクティブ パターンは、一致した文字列を DateTime コンストラクタに渡すことができる整数に変換するために使用されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

上記のコードの出力は次のとおりです。

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

アクティブパターンはパターンマッチング式だけに限定されず、let-binding で使用することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

上記のコードの出力は次のとおりです。

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [match 式](match-expressions.md)
