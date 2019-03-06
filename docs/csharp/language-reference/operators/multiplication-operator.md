---
title: '* 演算子 - C# リファレンス'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: a5e120d26614f1e38cc2f2db02949552140b594e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977345"
---
# <a name="-operator-c-reference"></a>* 演算子 (C# リファレンス)

`*` 演算子は 2 つの形式でサポートされています。単項ポインター間接参照演算子、または二項乗算演算子です。

## <a name="pointer-indirection-operator"></a>ポインター間接参照演算子

単項 `*` 演算子を使って、ポインター型のオペランドが指す変数を取得します。 詳細については、[ポインター変数の値を取得する方法](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md)に関する記事をご覧ください。

ポインター間接参照演算子 `*` には [unsafe](../keywords/unsafe.md) コンテキストが必要です。

## <a name="multiplication-operator"></a>乗算演算子

数値型の場合、`*` 演算子によってそのオペランドの積が計算されます。

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型は二項 `*` 演算子を[オーバーロード](../keywords/operator.md)できます。 二項 `*` 演算子をオーバーロードすると、[乗算代入演算子](multiplication-assignment-operator.md) `*=` も暗黙的にオーバーロードされます。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](../language-specification/index.md)の「[Pointer indirection (ポインターの間接参照)](~/_csharplang/spec/unsafe-code.md#pointer-indirection)」と「[Multiplication operator (乗算演算子)](~/_csharplang/spec/expressions.md#multiplication-operator)」セクションをご覧ください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [ポインター型](../../programming-guide/unsafe-code-pointers/pointer-types.md)