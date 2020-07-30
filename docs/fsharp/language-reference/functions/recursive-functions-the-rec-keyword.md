---
title: '再帰関数: rec キーワード'
description: "再帰関数を定義するために、' let ' キーワードと共に F # ' rec ' キーワードを使用する方法について説明します。"
ms.date: 05/16/2016
ms.openlocfilehash: c9a3b7dc27f4ed86948a08b7783d7e8e8b60e57f
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426977"
---
# <a name="recursive-functions-the-rec-keyword"></a>再帰関数: rec キーワード

キーワードは、 `rec` `let` 再帰関数を定義するためにキーワードと共に使用されます。

## <a name="syntax"></a>構文

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>解説

再帰関数は、それ自体を呼び出す関数で、F # 言語で明示的に識別されます。 これにより、定義されている識別子が関数のスコープで使用できるようになります。

次のコードは、数学的定義を使用して*n*<sup>番目</sup>のフィボナッチ数を計算する再帰関数を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> 実際には、前のサンプルのようなコードは、既に計算されている値を unecessarily しているため、理想的ではありません。 これは、この記事で詳しく説明されている末尾の再帰ではないためです。

メソッドは、型の中で暗黙的に再帰的になります。キーワードを追加する必要はありません `rec` 。 クラス内のバインディングは暗黙的に再帰的ではありません。

## <a name="tail-recursion"></a>Tail 再帰

再帰関数によっては、より "純粋な" 定義を[末尾の再帰](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)型にリファクタリングする必要があります。 これにより、不要なの再計算が行われなくなります。 たとえば、前のフィボナッチ数ジェネレーターは次のように書き換えることができます。

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

これはより複雑な実装です。 フィボナッチ数を生成することは、数学的に純粋だが実用的ではない "単純な" アルゴリズムの好例です。 いくつかの側面では、F # で効率的に実行できますが、再帰的に定義されています。

* という名前の再帰的な内部関数 `loop` (慣用的な F # パターン)。
* 2つのアキュムレータパラメーター。累積値を再帰呼び出しに渡します。
* の値をチェックして、特定の累積値を `n` 返します。

この例がループで繰り返し記述されている場合、コードは、特定の条件が満たされるまで、2つの異なる値を累積したものと似ています。

再帰呼び出しでは、呼び出し履歴に値を保存する必要がないため、これが末尾再帰の原因です。 計算されるすべての中間値は、内部関数への入力によって累積されます。 これにより、F # コンパイラは、ループのようなものを記述した場合と同じように、コードを最適化することもでき `while` ます。

前の例で示したように、内部関数と外部関数を使用して何かを再帰的に処理する F # コードを記述するのが一般的です。 内部関数は、末尾の再帰を使用します。一方、外側の関数は、呼び出し元に対してより適切なインターフェイスを備えています。

## <a name="mutually-recursive-functions"></a>相互再帰関数

場合によっては、関数が*相互に再帰的*であることを意味します。これは、呼び出しが円を形成することを意味します。この場合、1つ目の関数はを呼び出し、その間に任意の数の呼び出しを呼び出します。 このような関数は、1つのバインディングで定義し `let` 、キーワードを使用してそれらをリンクする必要があり `and` ます。

次の例は、2つの相互再帰関数を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>関連項目

- [関数](index.md)
