---
title: 'ループ: for...to 式'
description: 参照してください方法 F# for….. ループ変数の値の範囲をループで反復処理する式に使用されます。
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626628"
---
# <a name="loops-forto-expression"></a>ループ: for...to 式

式`for...to`は、ループ内でループ変数の値の範囲を反復処理するために使用されます。

## <a name="syntax"></a>構文

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Remarks

識別子の型は、 *start*および*finish*式の型から推論されます。 これらの式の型は、32ビットの整数である必要があります。

技術的には式です`for...to`が、命令型プログラミング言語では従来のステートメントに似ています。 *本体式*の戻り値の型はで`unit`ある必要があります。 次の例では、 `for...to`式のさまざまな用途を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

このコードの出力は、次のようになります。

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [For`for...in`条件](loops-for-in-expression.md)
- [For`while...do`条件](loops-while-do-expression.md)
