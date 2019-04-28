---
title: '条件式: if... then... else'
description: 条件式を記述する方法について説明しますF#コードの別の分岐を実行します。
ms.date: 05/16/2016
ms.openlocfilehash: eade8c20c1b62a2e9a54700550d832798308f368
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766040"
---
# <a name="conditional-expressions-ifthenelse"></a>条件式: `if...then...else`

`if...then...else`式は、コードの別の分岐を実行し、指定されたブール式に応じて異なる値に評価されます。

## <a name="syntax"></a>構文

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Remarks

前の構文で*expression1*ブール式を評価するときに実行される`true`、それ以外の*expression2*を実行します。

異なり、他の言語で、`if...then...else`コンストラクトは式、ステートメントではありません。 つまり、実行する分岐の最後の式の値では、値が生成されます。 各分岐で生成された値の型が一致する必要があります。 明示的ながある場合`else`ブランチ、その型は、`unit`します。 そのため場合の種類、`then`分岐以外の任意の型は、 `unit`、必要があります、`else`ブランチと同じ戻り値の型。 チェーンと`if...then...else`キーワードを使用することができます、併せて式`elif`の代わりに`else if`; が等しい。

## <a name="example"></a>例

次の例を使用する方法を示しています、`if...then...else`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)