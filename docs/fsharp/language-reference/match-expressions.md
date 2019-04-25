---
title: Match 式
description: について説明しますが、どのようにF#match 式が式のパターンのセットとの比較に基づいている分岐を制御を提供します。
ms.date: 04/19/2018
ms.openlocfilehash: 8972cc012d2746cb720eeed1acee403948941425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903956"
---
# <a name="match-expressions"></a>Match 式

`match`式が式のパターンのセットとの比較に基づいている分岐を制御を提供します。

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

パターン マッチング式は、複雑なパターンのセットとテスト式の比較に基づく、分岐の許可されます。 `match`式、*テスト式*でを有効にして、対応する一致が見つかった場合は、各パターンと比較されます*結果式*評価は、結果として得られる値はmatch 式の値として返されます。

前の構文に示すように関数を一致するパターンは、パターン マッチが行われますすぐに、引数にラムダ式です。 前の構文に示すように関数を一致するパターンは、次のと同じです。

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

ラムダ式の詳細については、次を参照してください。[ラムダ式。`fun`キーワード](functions/lambda-expressions-the-fun-keyword.md)します。

パターンのセット全体には、入力変数の考えられるすべての一致する必要がありますについて説明します。 ワイルドカード パターンを使用する多くの場合、(`_`)、比類のない以前の入力値と一致する最後のパターンとして。

次のコードはいくつかの方法を示しています、`match`式を使用します。 参照および使用できるすべてのパターンの例では、「[パターン マッチング](pattern-matching.md)します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>パターンのガード

使用することができます、`when`がパターンに一致する変数が満たす必要がある追加の条件を指定する句。 このような句として参照されます、*ガード*します。 続く式、`when`警備員に関連付けられているパターンに一致が行われた場合を除き、キーワードは評価されません。

次の例では、変数パターンの数値範囲を指定するガードの使用を示します。 ブール演算子を使用して複数の条件がまとめられることに注意してください。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

パターンのリテラル以外の値を使用することはできません、する必要がありますを使用することに注意してください、`when`句の値に対する入力の一部を比較した場合。 これは、次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

共用体パターンは、ガードでカバーされる、ときに、保護に適用されることに注意してください。**すべて**最後の 1 つだけでなく、パターンの。 たとえば、次のコードでは、ガードを与える`when a > 12`両方に適用されます`A a`と`B a`:

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