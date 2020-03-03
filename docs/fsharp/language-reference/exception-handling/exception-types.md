---
title: 例外の種類
description: 定義して、F# の例外の種類を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630314"
---
# <a name="exception-types"></a>例外の種類

F# の例外の 2 つのカテゴリがあります: .NET 例外の種類と F# の例外の種類。 このトピックでは、定義して、F# の例外の種類を使用する方法について説明します。

## <a name="syntax"></a>構文

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Remarks

前の構文で*例外型*新しい F# の例外型の名前を指定および*引数の型*この種類の例外が発生するときに指定できる引数の型を表します。 *引数の型*にタプル型を使用すると、複数の引数を指定できます。

F#例外の一般的な定義は、次のようになります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

この型の例外を生成するには、次`raise`のように関数を使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

次の例にF#示すように、 `try...with`式のフィルターでは、例外の種類を直接使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

例外の種類で定義された、 `exception` F# でのキーワードはから継承する新しい型`System.Exception`します。

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外: `raise` 関数](the-raise-function.md)
- [例外階層](https://msdn.microsoft.com/library/z4c5tckx.aspx)
