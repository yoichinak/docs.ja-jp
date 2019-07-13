---
title: '例外: raise 関数'
description: エラーまたは例外条件が発生したことを示す F# の 'raise' 関数を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 9e2515ad7b85c1025bc3aa0aa2a6929a8d35436d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641958"
---
# <a name="exceptions-the-raise-function"></a>例外: raise 関数

`raise`関数は、エラーまたは例外条件が発生したことを示すために使用します。 エラーに関する情報は、例外オブジェクトでキャプチャされます。

## <a name="syntax"></a>構文

```fsharp
raise (expression)
```

## <a name="remarks"></a>Remarks

`raise`関数は、例外オブジェクトを生成し、スタック アンワインド プロセスを開始します。 スタック アンワインド プロセスは、他の任意の .NET 言語ではこのプロセスの動作は同じように、共通言語ランタイム (CLR) によって管理されます。 スタックのアンワインド プロセスは、生成された例外に一致する例外ハンドラーの検索です。 現在の検索を開始`try...with`式、1 つを使用する必要がある場合。 各パターンで、`with`の順序で、ブロックをチェックします。 一致する例外ハンドラーが見つかると、例外が処理済みと見なされますそれ以外の場合、スタックがアンワインドされますと`with`一致するハンドラーが見つかるまで呼び出しチェーンのブロックがチェックされます。 すべて`finally`スタック アンワインドとして、呼び出しチェーンに含まれるブロックがシーケンスの実行もします。

`raise`関数と同等の`throw`c# または C++ でします。 使用`reraise`を同じ例外呼び出しチェーンの上位に伝達する catch ハンドラーにします。

次のコード例は、の使用を示しています、`raise`例外を生成する関数。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise`次の例に示すようにも、関数を使用、.NET 例外を発生させることができます。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...with`式](the-try-with-expression.md)
- [例外: `try...finally`式](the-try-finally-expression.md)
- [例外: `failwith`関数](the-failwith-function.md)
- [例外: `invalidArg`関数](the-invalidArg-function.md)
