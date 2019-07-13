---
title: 例外の種類
description: 定義して、F# の例外の種類を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: b7203dc042c7207bca95cfd0372790bfe52e0226
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645564"
---
# <a name="exception-types"></a>例外の種類

F# の例外の 2 つのカテゴリがあります: .NET 例外の種類と F# の例外の種類。 このトピックでは、定義して、F# の例外の種類を使用する方法について説明します。

## <a name="syntax"></a>構文

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Remarks

前の構文で*例外型*新しい F# の例外型の名前を指定および*引数の型*この種類の例外が発生するときに指定できる引数の型を表します。 タプル型を使用して複数の引数を指定することができます*引数型*します。

一般的な定義、F#例外、次のようです。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

使用してこの型の例外を生成することができます、`raise`関数は、次のようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

使用することができます、F#例外の種類でフィルター内で直接、`try...with`式は、次の例に示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

例外の種類で定義された、 `exception` F# でのキーワードはから継承する新しい型`System.Exception`します。

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外: `raise` 関数](the-raise-function.md)
- [例外階層](https://msdn.microsoft.com/library/z4c5tckx.aspx)
