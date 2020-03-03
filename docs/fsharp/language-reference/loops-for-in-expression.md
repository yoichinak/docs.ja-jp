---
title: 'ループ: for...in 式'
description: 詳細についF#ては、in 式ループコンストラクトは、列挙可能なコレクション内のパターンの一致を反復処理するために使用されます。
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216453"
---
# <a name="loops-forin-expression"></a>ループ: for...in 式

このループ構造は、列挙可能なコレクション内のパターンの一致を反復処理するために使用されます。たとえば、範囲式、シーケンス、リスト、配列、または列挙をサポートするその他の構造体です。

## <a name="syntax"></a>構文

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>コメント

式は、他の .net 言語`for each`のステートメントと比較できます。これは、列挙可能なコレクションの値をループ処理するために使用されるためです。 `for...in` ただし、 `for...in`では、コレクション全体に対して反復処理を行うのではなく、コレクションに対するパターンマッチングもサポートしています。

列挙可能な式は、整数型の範囲として、列挙`..`可能なコレクションとして指定することも、演算子を使用して指定することもできます。 列挙可能なコレクションには、リスト、シーケンス、配列、セット、マップなどがあります。 を実装`System.Collections.IEnumerable`する任意の型を使用できます。

`..`演算子を使用して範囲を表現する場合は、次の構文を使用できます。

*開始*... *終わっ*

次のコードのように、 *skip*と呼ばれるインクリメントを含むバージョンを使用することもできます。

*開始*... *スキップ*.. *終わっ*

整数の範囲と単純なカウンター変数をパターンとして使用する場合の一般的な動作は、各反復処理でカウンター変数を1ずつインクリメントすることですが、範囲に skip 値が含まれている場合は、代わりに skip 値によってカウンターがインクリメントされます。

パターンに一致した値は、本文の式でも使用できます。

次のコード例は、 `for...in`式の使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

出力は次のとおりです。

```console
1
5
100
450
788
```

次の例は、シーケンスをループ処理する方法と、単純な変数の代わりに組パターンを使用する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

出力は次のとおりです。

```console
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

次の例は、単純な整数範囲をループ処理する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Function1 の出力は次のようになります。

```console
1 2 3 4 5 6 7 8 9 10
```

次の例では、範囲の他のすべての要素を含む、skip が2の範囲をループ処理する方法を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

の出力は`function2`次のとおりです。

```console
1 3 5 7 9
```

文字範囲を使用する方法を次の例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

の出力は`function3`次のとおりです。

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

次の例では、逆の反復処理で負の skip 値を使用する方法を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

の出力は`function4`次のとおりです。

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

次のコードのように、範囲の先頭と末尾には、関数などの式を指定することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

この入力に`function5`よるの出力は次のとおりです。

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

次の例は、ループで要素が不要な\_場合に、ワイルドカード文字 () を使用する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

出力は次のとおりです。

```console
Number of elements in list1: 5
```

`Note`は、シーケンス`for...in`式やその他のコンピュテーション式で使用できます。その場合は、 `for...in`式のカスタマイズされたバージョンが使用されます。 詳細については、「[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [For`for...to`条件](loops-for-to-expression.md)
- [For`while...do`条件](loops-while-do-expression.md)
