---
title: '- および -= 演算子 - C# リファレンス'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 9f43a863de69122e251204668af2ea989fcc993c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300089"
---
# <a name="--and---operators-c-reference"></a>- および -= 演算子 (C# リファレンス)

`-` 演算子は、組み込み数値型と[デリゲート](../keywords/delegate.md)型でサポートされています。

算術演算子 `-` については、「[算術演算子 (C# リファレンス)](arithmetic-operators.md)」の記事の「[単項プラス演算子と単項マイナス演算子](arithmetic-operators.md#unary-plus-and-minus-operators)」セクションと「[減算演算子 -](arithmetic-operators.md#subtraction-operator--)」セクションを参照してください。

## <a name="delegate-removal"></a>デリゲートの削除

同じ[デリゲート](../keywords/delegate.md)型のオペランドに対しては、`-` 演算子は、次のように計算されるデリゲート インスタンスを返します。

- 両方のオペランドが null ではなく、2 番目のオペランドの呼び出しリストが最初のオペランドの呼び出しリストの適切な連続するサブリストの場合は、演算の結果は 2 番目のオペランドのエントリを最初のオペランドの呼び出しリストから削除することによって取得される新しい呼び出しリストとなります。 2 番目のオペランドのリストが、最初のオペランドのリストで複数の連続するサブリストと一致する場合、右端の一致するサブリストのみが削除されます。 削除によりリストが空になる場合、結果は `null` になります。
- 2 番目のオペランドの呼び出しリストが最初のオペランドの呼び出しリストの適切な連続するサブリストでない場合は、演算結果は最初のオペランドになります。
- 最初のオペランドが `null` の場合は、演算結果は `null` になります。 2 番目のオペランドが `null` の場合は、演算結果は最初のオペランドになります。

次の例は、`-` 演算によるデリゲートの削除方法を示しています。

[!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

## <a name="subtraction-assignment-operator--"></a>減算代入演算子 -=

次のような `-=` 演算子を使用する式があるとします

```csharp
x -= y
```

上記の式は、次の式と同じです。

```csharp
x = x - y
```

ただし、`x` が評価されるのは 1 回だけです。
  
`-=` 演算子の使用例を次に示します。

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

[イベント](../keywords/event.md)から登録を解除するときに、`-=` 演算子を使用して削除するイベント ハンドラー メソッドを指定することもできます。 詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型は `-` 演算子を[オーバーロード](../keywords/operator.md)できます。 2 項 `-` 演算子をオーバーロードすると、`-=` 演算子も暗黙的にオーバーロードされます。 ユーザー定義型では、`-=` 演算子の明示的なオーバーロードはできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](../language-specification/index.md)の[単項マイナス演算子](~/_csharplang/spec/expressions.md#unary-minus-operator)と[減算演算子](~/_csharplang/spec/expressions.md#subtraction-operator)に関するセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [デリゲート](../../programming-guide/delegates/index.md)
- [イベント](../../programming-guide/events/index.md)
- [checked と unchecked](../keywords/checked-and-unchecked.md)
- [算術演算子](arithmetic-operators.md)
- [+ および += 演算子](addition-operator.md)
