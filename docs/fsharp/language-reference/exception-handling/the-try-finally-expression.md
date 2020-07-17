---
title: 例外:try...finally 式
description: 学習方法、F# 'try… 最後に' 式では、コードのブロックが例外をスローする場合でも、クリーンアップ コードを実行することができます。
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083004"
---
# <a name="exceptions-the-tryfinally-expression"></a>例外:try...finally 式

`try...finally`式を使用すると、コードのブロックで例外がスローされた場合でもクリーンアップコードを実行できます。

## <a name="syntax"></a>構文

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Remarks

式は、 *expression1*の実行中に例外が生成されたかどうかに関係なく、前の構文で expression2 のコードを実行するために使用できます。 `try...finally`

*Expression2*の型は、式全体の値には影響しません。例外が発生しないときに返される型は、 *expression1*の最後の値です。 例外が発生した場合、値は返されず、制御のフローは、コールスタックの上位にある次の一致する例外ハンドラーに転送されます。 例外ハンドラーが見つからない場合、プログラムは終了します。 一致するハンドラー内のコードが実行されるか、プログラムが終了する前に`finally` 、分岐内のコードが実行されます。

次のコードは、 `try...finally`式の使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

コンソールへの出力は次のとおりです。

```console
Closing stream
Exception handled.
```

出力からわかるように、外側の例外が処理される前にストリームが閉じられてい`test.txt`ます。また`test1`、ファイルには、例外が転送されたにもかかわらず、バッファーがフラッシュされ、ディスクに書き込まれたことを示すテキストが含まれています。外側の例外ハンドラーに制御します。

コンストラクトは、 `try...with` `try...finally`コンストラクトとは別のコンストラクトであることに注意してください。 したがって、コードに`with`ブロック`finally`とブロックの両方が必要な場合は、次のコード例に示すように、2つの構造体を入れ子にする必要があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

シーケンス式と非同期ワークフローを含むコンピュテーション式のコンテキストでは、.. **.最後**の式には、カスタム実装を含めることができます。 詳細については、「[コンピュテーション式](../computation-expressions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外: `try...with`式](the-try-with-expression.md)
