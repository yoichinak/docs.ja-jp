---
title: 'ループ: for...in 式'
description: 参照してください方法 F# for….. 式で列挙可能なコレクション内のパターンの一致を反復処理するループ コンストラクトが使用されます。
ms.date: 05/16/2016
ms.openlocfilehash: 5346713b1747227f3fe79e308455d976e506f968
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641811"
---
# <a name="loops-forin-expression"></a>ループ: for...in 式

このループの構造は、範囲表現、シーケンス、リスト、配列、または列挙型をサポートするその他の構成要素などの列挙可能なコレクション内のパターンの一致を反復処理に使用されます。

## <a name="syntax"></a>構文

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Remarks

`for...in`に式を比較できるように、`for each`他の .NET 言語でステートメントをループ処理する列挙可能なコレクション内の値に使用されています。 ただし、`for...in`も全体のコレクションを反復処理だけではなくコレクションに対する一致パターンをサポートします。

列挙可能なコレクションとして、またはを使用して、列挙可能な式を指定することができます、`..`整数型の範囲として、演算子。 列挙可能なコレクションには、リスト、シーケンス、配列、セット、マップ、およびなどが含まれます。 実装する任意の型`System.Collections.IEnumerable`ことができます。

使用して範囲を表現するときに、`..`オペレーターは、次の構文を使用することができます。

*開始*. *[完了] します。*

呼ばれる、インクリメントを含むバージョンを使用することもできます、*スキップ*次のコードのようにします。

*開始*. *スキップ*. *[完了] します。*

反復処理ごとに、1 つのカウンター変数をインクリメントする通常の動作は、パターンとして整数の範囲と単純なカウンター変数を使用する場合が、カウンターは skip 値が代わりにインクリメントされます範囲には、skip 値が含まれている場合。

パターンに一致した値は、式の本体でも使用できます。

次のコード例は、の使用を示しています、`for...in`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

出力は次のとおりです。

```
1
5
100
450
788
```

次の例では、単純な変数ではなくタプル パターンを使用する方法と、シーケンス全体をループする方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

出力は次のとおりです。

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

次の例では、単純な整数の範囲をループする方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Function1 の出力は次のとおりです。

```
1 2 3 4 5 6 7 8 9 10
```

次の例では、範囲の他のすべての要素を含む、2 のスキップを含む範囲をループする方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

出力`function2`のとおりです。

```
1 3 5 7 9
```

次の例では、文字の範囲を使用する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

出力`function3`のとおりです。

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

次の例では、逆順イテレーションの負の値のスキップの値を使用する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

出力`function4`のとおりです。

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

先頭と範囲の終了には、次のコードのように、関数などの式ことができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

出力`function5`この入力は次のようにします。

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

次の例では、ワイルドカード文字の使用 (\_) 要素が、ループ内で必要ない場合。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

出力は次のとおりです。

```
Number of elements in list1: 5
```

`Note` 使用することができます`for...in`シーケンス式とその他のコンピュテーション式で、カスタマイズされたバージョンの場合、`for...in`式を使用します。 詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [ループ:`for...to` 式](loops-for-to-expression.md)
- [ループ:`while...do` 式](loops-while-do-expression.md)
