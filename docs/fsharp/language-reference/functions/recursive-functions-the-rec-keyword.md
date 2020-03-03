---
title: 再帰関数:Rec キーワード
description: 再帰関数の定義に 'let' キーワードを使用して、F# の 'rec' キーワードが使用される方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630656"
---
# <a name="recursive-functions-the-rec-keyword"></a>再帰関数:Rec キーワード

キーワードは、再帰関数を定義`let`するためにキーワードと共に使用されます。 `rec`

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

## <a name="remarks"></a>Remarks

再帰関数は、自身を呼び出す関数は、F# 言語で明示的に識別されます。 これにより、定義されている識別子が関数のスコープで使用できるようになります。

次のコードは、 *n*<sup>番目</sup>のフィボナッチ数列を計算する再帰関数を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> 実際には、上記のコードのようなコードでは、以前に計算された値の再計算が関係するため、メモリとプロセッサ時間が無駄になります。

メソッドは、型の中で暗黙的に再帰的になります。`rec`キーワードを追加する必要はありません。 クラス内のバインディングは暗黙的に再帰的ではありません。

## <a name="mutually-recursive-functions"></a>相互再帰関数

場合によっては、関数が*相互に再帰的*であることを意味します。これは、呼び出しが円を形成することを意味します。この場合、1つ目の関数はを呼び出し、その間に任意の数の呼び出しを呼び出します。 このような関数は、1つ`let`のバインディングで定義し、 `and`キーワードを使用してそれらをリンクする必要があります。

次の例は、2つの相互再帰関数を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>関連項目

- [関数](index.md)
