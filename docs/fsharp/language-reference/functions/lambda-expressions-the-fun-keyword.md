---
title: ラムダ式:Fun キーワード
description: 使用する方法について説明します、F#匿名関数は、ラムダ式を定義する '楽しい' キーワード。
ms.date: 05/16/2016
ms.openlocfilehash: 6ad15173bb8643bff330e3ca3823cba5d43ad445
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941025"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>ラムダ式:Fun キーワード (F#)

`fun`キーワードの使用をラムダ式、つまり、匿名関数を定義します。

## <a name="syntax"></a>構文

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Remarks

*パラメーター リスト*通常の名前と、必要に応じて、パラメーターの型で構成されます。 一般的に、*パラメーター リスト*F# のパターンで構成することができます。 可能なパターンの完全な一覧を参照してください。[パターン マッチング](../pattern-matching.md)します。 有効なパラメーターのリストには、次の例が含まれます。

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

*式*うち、最後の式が戻り値を生成、関数の本文です。 有効なラムダ式の例を以下に示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>ラムダ式の使用

ラムダ式は、リストまたはその他のコレクションで操作を実行し、追加の関数を定義する作業を回避するために必要な場合に特に便利です。 多くF#ライブラリ関数が引数として関数の値を受け取るし、ラムダ式を使用して、そのような場合に特に便利であることができます。 次のコードでは、リストの要素にラムダ式が適用されます。 この場合、匿名関数では、一覧のすべての要素に 1 を追加します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>関連項目

- [関数](index.md)