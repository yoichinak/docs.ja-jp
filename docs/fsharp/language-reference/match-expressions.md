---
title: 一致式
description: F#一致式を使用して、式と一連のパターンとの比較に基づく分岐コントロールを提供する方法について説明します。
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627611"
---
# <a name="match-expressions"></a>一致式

式`match`は、式と一連のパターンとの比較に基づいて分岐コントロールを提供します。

## <a name="syntax"></a>構文

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>Remarks

パターン一致式を使用すると、テスト式と一連のパターンとの比較に基づいて、複雑な分岐を実行できます。 この式では、各パターンと*テスト式*が比較され、一致が見つかると、対応する*結果式*が評価され、結果の値が match 式の値として返されます。 `match`

前の構文で示されているパターン一致関数は、引数でパターンマッチングがすぐに実行されるラムダ式です。 前の構文で示されているパターン一致関数は、次の関数と同じです。

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

ラムダ式の詳細については[、次を参照してください。ラムダ式:`fun`キーワード](./functions/lambda-expressions-the-fun-keyword.md)します。

パターンのセット全体で、入力変数のすべての一致候補をカバーする必要があります。 多くの場合、以前に一致し`_`ていない入力値と一致させるために、最後のパターンとしてワイルドカードパターン () を使用します。

次のコードは、 `match`式を使用するいくつかの方法を示しています。 使用可能なすべてのパターンのリファレンスと例については、「[パターン一致](pattern-matching.md)」を参照してください。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>パターンでのガード

句を`when`使用して、変数がパターンに一致するために満たす必要のある追加条件を指定できます。 このような句を*ガード*と呼びます。 `when`キーワードに続く式は、そのガードに関連付けられているパターンが一致しない限り評価されません。

次の例は、ガードを使用して、変数パターンの数値範囲を指定する方法を示しています。 複数の条件は、ブール演算子を使用して結合されることに注意してください。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

リテラル以外の値はパターンで使用できないため、入力の一部を値と`when`比較する必要がある場合は、句を使用する必要があることに注意してください。 これを次のコードに示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Union パターンがガードによってカバーされている場合、ガードは、最後のパターンだけでなく、**すべて**のパターンに適用されることに注意してください。 たとえば、次のコードがあるとします`when a > 12` 。ガードは`A a`と`B a`の両方に適用されます。

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [アクティブ パターン](active-patterns.md)
- [パターン一致](pattern-matching.md)
