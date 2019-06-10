---
title: () 演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 8f7382a49c81b6fd8e104b864ffc2f70db7fe4a6
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758114"
---
# <a name="-operator-c-reference"></a>() 演算子 (C# リファレンス)

通常、かっこ (`()`) は、メソッドまたはデリゲートの呼び出し、またはキャスト式内で使用されます。

式に含まれる演算を評価する順序を指定する場合にもかっこを使用します。 詳細については、「[演算子](../../programming-guide/statements-expressions-operators/operators.md)」記事の「[かっこの追加](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses)」セクションを参照してください。 優先順位順に並べられた演算子の一覧については、「[C# 演算子](index.md)」を参照してください。

## <a name="method-invocation"></a>メソッドの呼び出し

メソッド (引数を指定した場合と指定しない場合) とデリゲートを呼び出す方法の例を次に示します。

[!code-csharp-interactive[use for invocation](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

かっこは、[`new`](../keywords/new-operator.md) 演算子を使用して[コンストラクター](../../programming-guide/classes-and-structs/constructors.md)を呼び出すときにも使用します。

メソッドの詳細については、「[メソッド](../../programming-guide/classes-and-structs/methods.md)」を参照してください。 デリゲートの詳細については、「[デリゲート](../../programming-guide/delegates/index.md)」を参照してください。

## <a name="cast-expression"></a>キャスト式

`(T)E` という形式のキャスト式で、変換演算子が呼び出され、式 `E` の値が型 `T` に変換されます。 型 `E` から型 `T` への明示的な変換が存在しない場合は、コンパイル時エラーが発生します。 変換演算子を定義する方法については、[明示的なキーワード](../keywords/explicit.md)と[暗黙的なキーワード](../keywords/implicit.md)に関する記事を参照してください。

数値間の型変換の例を次に示します。

[!code-csharp-interactive[use for cast](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

数値型間の事前に定義された明示的な変換については、「[明示的な数値変換の一覧表](../keywords/explicit-numeric-conversions-table.md)」を参照してください。

詳細については、「[キャストと型変換](../../programming-guide/types/casting-and-type-conversions.md)」と「[変換演算子](../../programming-guide/statements-expressions-operators/conversion-operators.md)」を参照してください。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

`()` 演算子はオーバーロードできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の「[Invocation 式](~/_csharplang/spec/expressions.md#invocation-expressions)」セクションと「[キャスト式](~/_csharplang/spec/expressions.md#cast-expressions)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
