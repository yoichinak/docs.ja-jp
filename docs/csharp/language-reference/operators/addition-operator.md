---
title: + 演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 0f04ba837f9c03107acd0b2174cbd07c14a8c213
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504471"
---
# <a name="-operator-c-reference"></a>+ 演算子 (C# リファレンス)

`+` 演算子は 2 つの形式でサポートされます。単項プラス演算子と二項加算演算子です。

## <a name="unary-plus-operator"></a>単項プラス演算子

単項 `+` 演算子によって、そのオペランドの値が返されます。 すべての数値型でサポートされます。

## <a name="numeric-addition"></a>数値加算

数値型の場合、`+` 演算子によってそのオペランドの合計が計算されます。

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

算術演算子の詳細については、「[Arithmetic operators](arithmetic-operators.md)」 (算術演算子) を参照してください。

## <a name="string-concatenation"></a>文字列連結

一方または両方のオペランドが[文字列](../keywords/string.md)型の場合、`+` 演算子によってそのオペランドの文字列表現が連結されます。

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

C# 6 以降、[文字列補間](../tokens/interpolated.md)という文字列を書式設定するより便利な方法が提供されます。

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>デリゲートの組み合わせ

[デリゲート](../keywords/delegate.md)型の場合、`+` 演算子によって、呼び出されたとき、最初のオペランドを呼び出し、次に 2 番目のオペランドを呼び出す新しいデリゲート インスタンスが返されます。 いずれかのオペランドが `null` の場合、`+` 演算子によって別のオペランドの値が返されます (`null` でもある場合があります)。 次の例では、デリゲートが `+` 演算子と組み合わされるしくみを説明しています。

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

デリゲート型の詳細については、[デリゲート](../../programming-guide/delegates/index.md)に関するページを参照してください。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

単項演算子と二項 `+` 演算子は、ユーザー定義型で[オーバーロード](../keywords/operator.md)できます。 二項 `+` 演算子をオーバーロードすると、[加算代入演算子](addition-assignment-operator.md) `+=` も暗黙的にオーバーロードされます。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](../language-specification/index.md)の[単項プラス演算子](~/_csharplang/spec/expressions.md#unary-plus-operator)と[加算演算子](~/_csharplang/spec/expressions.md#addition-operator)に関するセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [文字列補間](../tokens/interpolated.md)
- [方法: 複数の文字列を連結する](../../how-to/concatenate-multiple-strings.md)
- [デリゲート](../../programming-guide/delegates/index.md)
- [checked と unchecked](../keywords/checked-and-unchecked.md)
