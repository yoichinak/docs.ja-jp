---
title: 例外:failwith 関数
description: "'Failwith' 関数は F# の例外を生成する方法について説明します。"
ms.date: 05/16/2016
ms.openlocfilehash: f2c86362d5bdde7bab55751f019965a5f4ca6236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630324"
---
# <a name="exceptions-the-failwith-function"></a>例外:failwith 関数

`failwith`関数は F# の例外を生成します。

## <a name="syntax"></a>構文

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Remarks

前の構文の*エラーメッセージ文字列*は、リテラル文字列または型`string`の値です。 これは、 `Message`例外のプロパティになります。

によって生成される例外`failwith`は、`System.Exception`例外があり、名前を持つ参照`Failure`F# コードにします。 次の`failwith`コードは、を使用して例外をスローする方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...with`式](the-try-with-expression.md)
- [例外: `try...finally`式](the-try-finally-expression.md)
- [例外: `raise` 関数](the-raise-function.md)
