---
title: ラムダ式:楽しいキーワード
description: "\"楽しい\" キーワードをF#使用してラムダ式を定義する方法について説明します。これは匿名関数です。"
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630661"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>ラムダ式:楽しいキーワード (F#)

`fun`キーワードは、ラムダ式、つまり匿名関数を定義するために使用されます。

## <a name="syntax"></a>構文

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Remarks

*パラメーターリスト*は、通常、名前と、必要に応じてパラメーターの型で構成されます。 一般的に、*パラメーター リスト*F# のパターンで構成することができます。 使用可能なパターンの完全な一覧については、「[パターン一致](../pattern-matching.md)」を参照してください。 有効なパラメーターの一覧を次の例に示します。

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

*式*は関数の本体であり、の最後の式で戻り値が生成されます。 有効なラムダ式の例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>ラムダ式の使用

ラムダ式は、リストまたは他のコレクションに対して操作を実行し、関数を定義する余分な作業を避ける必要がある場合に特に便利です。 多くF#のライブラリ関数は関数の値を引数として受け取り、そのような場合にラムダ式を使用すると特に便利です。 次のコードは、リストの要素にラムダ式を適用します。 この場合、匿名関数はリストのすべての要素に1を追加します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>関連項目

- [関数](index.md)
