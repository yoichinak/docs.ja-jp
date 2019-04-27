---
title: 'ループ: for...to 式'
description: 参照してください方法 F# for….. ループ変数の値の範囲をループで反復処理する式に使用されます。
ms.date: 05/16/2016
ms.openlocfilehash: 041e98fa4bcc140aa3cd699f6ed35bf52c8b4175
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904034"
---
# <a name="loops-forto-expression"></a>ループ: for...to 式

`for...to`ループ変数の値の範囲をループで反復処理する式を使用します。

## <a name="syntax"></a>構文

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Remarks

識別子の型の型から推論されます、*開始*と*完了*式。 これらの式の型は、32 ビット整数である必要があります。

式では技術的には、`for...to`は命令型プログラミング言語では、従来のステートメントのようにします。 戻り値の型、*式の本体*あります`unit`します。 次の例では、さまざまな使用、`for...to`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

このコードの出力は、次のようになります。

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [ループ:`for...in` 式](loops-for-in-expression.md)
- [ループ:`while...do` 式](loops-while-do-expression.md)