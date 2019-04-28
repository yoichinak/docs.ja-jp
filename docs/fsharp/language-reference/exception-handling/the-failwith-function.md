---
title: 例外:failwith 関数
description: "'Failwith' 関数は F# の例外を生成する方法について説明します。"
ms.date: 05/16/2016
ms.openlocfilehash: 05d385ddfc98a910779a6f59949a7187c38f0812
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772685"
---
# <a name="exceptions-the-failwith-function"></a>例外:failwith 関数

`failwith`関数は F# の例外を生成します。

## <a name="syntax"></a>構文

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Remarks

*エラー メッセージの文字列*リテラル文字列または型の値は、前の構文で`string`します。 `Message`例外のプロパティ。

によって生成される例外`failwith`は、`System.Exception`例外があり、名前を持つ参照`Failure`F# コードにします。 次のコードの使用を示します`failwith`例外をスローします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...with`式](the-try-with-expression.md)
- [例外: `try...finally`式](the-try-finally-expression.md)
- [例外: `raise` 関数](the-raise-function.md)