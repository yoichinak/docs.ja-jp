---
title: 例外:try...finally 式
description: 学習方法、F# 'try… 最後に' 式では、コードのブロックが例外をスローする場合でも、クリーンアップ コードを実行することができます。
ms.date: 05/16/2016
ms.openlocfilehash: 24613185818c8ea30b27dcf639b22af320c4b401
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611621"
---
# <a name="exceptions-the-tryfinally-expression"></a>例外:try...finally 式

`try...finally`式では、コードのブロックが例外をスローする場合でも、クリーンアップ コードを実行することができます。

## <a name="syntax"></a>構文

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Remarks

`try...finally`でコードを実行する式を使用できます*expression2*の実行中に例外を生成するかどうかに関係なく、上記の構文で*expression1*します。

型*expression2* ; 式全体の値には含まれません、例外が発生していないときに返される型の最後の値は、 *expression1*します。 例外が発生した場合、値は返されません、コントロールのフローは、コール スタックの上の次の一致する例外ハンドラーに転送します。 例外ハンドラーが見つからない場合、プログラムを終了します。 一致するハンドラーのコードが実行されるかプログラムが終了すると、コードでは、前に、`finally`分岐が実行されます。

次のコードの使用を示します、`try...finally`式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

コンソールに出力は次のとおりです。

```
Closing stream
Exception handled.
```

外側の例外が処理された、前にストリームが閉じた出力からわかるとファイル`test.txt`テキストを含む`test1`バッファーがフラッシュされ、場合でも、例外の転送をディスクに書き込まれたことを示します外側の例外ハンドラーに制御します。

なお、`try...with`コンストラクトが別のコンストラクトから、`try...finally`構築します。 そのため、コードでは、両方が必要な場合、`with`ブロックと`finally`ブロック、次のコード例のように、2 つの構造を入れ子にする必要があります。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

コンピュテーション式のコンテキストで、シーケンス式と非同期のワークフローを含む**try… finally**式は、カスタム実装を持つことができます。 詳細については、[コンピュテーション式](../computation-expressions.md)を参照してください。

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外処理:`try...with`式](the-try-with-expression.md)