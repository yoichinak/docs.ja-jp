---
title: null 値
description: F#プログラミング言語での null 値の使用方法について説明します。
ms.date: 03/22/2019
ms.openlocfilehash: 2038c0a461fec9884c51edd50c3c9f336104e30e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630807"
---
# <a name="null-values"></a>null 値

このトピックでは、F# で null 値を使用する方法について説明します。

## <a name="null-value"></a>Null 値

Null 値は通常使用されません F# での値または変数。 ただし、null は、特定の状況では異常な値として表示されます。 しない限り、null がない通常の値として許可 F# の型が定義されている場合、 [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)属性型に適用されます。 Null は使用可能な値型は、他の .NET 言語で定義されているが場合と、F# コードで null 値を発生可能性があるこのような型と相互運用するときにします。

F# で定義されているし、F# から厳密に使用される型、F# ライブラリを直接使用して null 値を作成する唯一の方法は使用する[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)または[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)します。 ただし、F# 型の他の .NET 言語から使用されるまたは null 値が発生することがその型を使用して、F# など、.NET Framework で記述されていない API を使用している場合。

使用することができます、 `option` F# 参照変数を別の .NET 言語で使用できる null 値で使用するときに入力します。 オブジェクトがない場合は、 F# `option` null の代わりに型を使用`None`して、オプションの値を使用します。 オブジェクトがある場合は`Some(obj)` 、オプションの`obj`値をオブジェクトと共に使用します。 詳細については、[オプション](../options.md)に関するページを参照してください。 `null`では`Some x` 、で`x`ある場合に値をオプションにパックすることもできます。 `null` このため、値が`None` `null`の場合はを使用することが重要です。

`null`キーワードは、F# 言語では、有効なキーワードと、.NET Framework Api または他の .NET 言語で記述されている他の Api を使用しているときに使用する必要があります。 Null 値が必要になる可能性がある2つの状況は、.NET API を呼び出し、引数として null 値を渡す場合と、.NET メソッド呼び出しからの戻り値または出力パラメーターを解釈する場合です。

.Net メソッドに null 値を渡すには、呼び出し元の`null`コードでキーワードを使用するだけです。 これを次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

.NET メソッドから取得した null 値を解釈するには、可能であれば、パターンマッチングを使用します。 次のコード例は、パターン一致を使用して、入力ストリームの末尾を越え`ReadLine`て読み取ろうとしたときにから返される null 値を解釈する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

使用する場合など、他の方法で F# 型の null 値を生成することも`Array.zeroCreate`、呼び出す`Unchecked.defaultof`します。 Null 値をカプセル化するためには、このようなコードに注意する必要があります。 専用の F# ライブラリでは、すべての関数で null 値をチェックする必要はありません。 他の .net 言語との相互運用のためにライブラリを記述する場合は、または Visual Basic コードの`ArgumentNullException` C#場合と同様に、null 入力パラメーターのチェックを追加し、をスローすることが必要になる場合があります。

次のコードを使用すると、任意の値が null かどうかを確認できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>関連項目

- [値](index.md)
- [match 式](../match-expressions.md)
