---
title: '&amp; 演算子 - C# リファレンス'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 67d60709e1c6c76071ecfb7aac74c83dec6f372a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310045"
---
# <a name="amp-operator-c-reference"></a>&amp; 演算子 (C# リファレンス)

`&` 演算子は 2 つの形式でサポートされます。単項 address-of 演算子と二項論理演算子です。

## <a name="unary-address-of-operator"></a>単項 address-of 演算子

単項 `&` 演算子によって、そのオペランドのアドレスが返されます。 詳細については、「[方法: 変数のアドレスを取得する](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md)」を参照してください。

address-of 演算子 `&` には [unsafe](../keywords/unsafe.md) コンテキストが必要です。

## <a name="integer-logical-bitwise-and-operator"></a>整数論理ビット演算 AND 演算子

整数型の場合、`&` 演算子がそのオペランドの論理ビット演算 AND を計算します。

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> 上記の例では、[C# 7.0 で導入され](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements)、[C# 7.2 で強化された](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals)バイナリ リテラルを使用しています。

整数型に対する演算は一般的に列挙型でも許可されているため、`&` 演算子は [enum](../keywords/enum.md) オペランドもサポートします。

## <a name="boolean-logical-and-operator"></a>ブール論理 AND 演算子

[bool](../keywords/bool.md) オペランドの場合、`&` 演算子がそのオペランドの論理 AND を計算します。 `x` と `y` の両方が `true` であれば、`x & y` の結果は `true` です。 それ以外の場合、結果は `false` です。

`&` 演算子は最初のオペランドが `false` と評価されても両方のオペランドを評価するため、結果は 2 番目のオペランドの値に関係なく、必ず `false` になります。 次の例は、その動作を示します。

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

[条件付き AND 演算子](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` もそのオペランドの論理 AND を計算しますが、最初のオペランドが `false` と評価された場合、2 番目のオペランドは評価されません。

Null 許容型ブールのオペランドの場合、`&` 演算子の動作は、SQL の 3 値論理と一致します。 詳細については、「[Boolean logical operators (ブール論理演算子)](boolean-logical-operators.md)」記事の「[Nullable Boolean logical operators (null 許容論理演算子)](boolean-logical-operators.md#nullable-boolean-logical-operators)」セクションを参照してください。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型は二項 `&` 演算子を[オーバーロード](../keywords/operator.md)できます。 二項 `&` 演算子をオーバーロードすると、[AND 代入演算子](and-assignment-operator.md) `&=` も暗黙的にオーバーロードされます。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の [address-of 演算子](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)と[論理演算子](~/_csharplang/spec/expressions.md#logical-operators)に関するセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [ブール論理演算子](boolean-logical-operators.md)
- [ポインター型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [| 演算子](or-operator.md)
- [^ 演算子](xor-operator.md)
- [~ 演算子](bitwise-complement-operator.md)
