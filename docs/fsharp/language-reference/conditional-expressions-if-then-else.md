---
title: '条件式: if...そうしたら。。。さも'
description: でF#条件式を記述して、異なるコードの分岐を実行する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 825149bf296eded3cc2b4d8847ba4d82bea40cdc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630398"
---
# <a name="conditional-expressions-ifthenelse"></a>条件式:`if...then...else`

式`if...then...else`は、コードの異なる分岐を実行し、指定されたブール式に応じて別の値に評価されます。

## <a name="syntax"></a>構文

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Remarks

前の構文では 、ブール式がに`true`評価されると、expression1 が実行されます。それ以外の場合は、 *expression2*が実行されます。

他の言語`if...then...else`とは異なり、コンストラクトはステートメントではなく、式です。 つまり、値が生成されます。これは、が実行される分岐の最後の式の値です。 各分岐で生成される値の型が一致している必要があります。 明示的`else`な分岐がない場合、その型`unit`はになります。 したがって、 `then`分岐の型が以外`unit`の型である場合は、同じ戻り値`else`の型を持つ分岐が存在する必要があります。 式を連結する場合は、の`else if`代わりに`elif`キーワードを使用できます。これらは等価です。 `if...then...else`

## <a name="example"></a>例

次の例は、式の`if...then...else`使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
