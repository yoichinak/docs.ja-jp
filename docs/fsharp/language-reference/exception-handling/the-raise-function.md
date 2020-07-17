---
title: '例外: raise 関数'
description: エラーまたは例外条件が発生したことを示す F# の 'raise' 関数を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630290"
---
# <a name="exceptions-the-raise-function"></a>例外: raise 関数

関数`raise`は、エラーまたは例外的な条件が発生したことを示すために使用されます。 エラーに関する情報は、例外オブジェクトでキャプチャされます。

## <a name="syntax"></a>構文

```fsharp
raise (expression)
```

## <a name="remarks"></a>Remarks

関数`raise`は、例外オブジェクトを生成し、スタックアンワインドプロセスを開始します。 スタックアンワインドプロセスは共通言語ランタイム (CLR) によって管理されているため、このプロセスの動作は、他の .NET 言語と同じになります。 スタックアンワインドプロセスは、生成された例外に一致する例外ハンドラーを検索します。 現在`try...with`の式 (存在する場合) で検索が開始されます。 `with`ブロック内の各パターンは順番にチェックされます。 一致する例外ハンドラーが見つかった場合、例外は処理されたと見なされます。それ以外の場合は、スタック`with`がアンワインドされ、一致するハンドラーが見つかるまで呼び出しチェーンのブロックアップがチェックされます。 呼び出し`finally`チェーンで検出されたすべてのブロックも、スタックのアンワインドとして順番に実行されます。

関数は、 C#またC++はの`throw`と同じです。 `raise` Catch `reraise`ハンドラーでを使用して、同じ例外を呼び出しチェーンの上位に伝達します。

次のコード例は、 `raise`関数を使用して例外を生成する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

関数`raise`は、次の例に示すように、.net の例外を発生させるためにも使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...with`式](the-try-with-expression.md)
- [例外: `try...finally`式](the-try-finally-expression.md)
- [例外: `failwith`関数](the-failwith-function.md)
- [例外: `invalidArg`関数](the-invalidArg-function.md)
