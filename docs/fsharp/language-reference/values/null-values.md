---
title: null 値
description: Null 値を使用する方法について説明します、F#プログラミング言語。
ms.date: 03/22/2019
ms.openlocfilehash: 93ac48eddf36981b9df550e76405c3175ae92e0a
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409641"
---
# <a name="null-values"></a>null 値

このトピックでは、F# で null 値を使用する方法について説明します。

## <a name="null-value"></a>Null 値

Null 値は通常使用されません F# での値または変数。 ただし、特定の状況で、外れ値として null が表示されます。 しない限り、null がない通常の値として許可 F# の型が定義されている場合、 [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)属性型に適用されます。 Null は使用可能な値型は、他の .NET 言語で定義されているが場合と、F# コードで null 値を発生可能性があるこのような型と相互運用するときにします。

F# で定義されているし、F# から厳密に使用される型、F# ライブラリを直接使用して null 値を作成する唯一の方法は使用する[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)または[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)します。 ただし、F# 型の他の .NET 言語から使用されるまたは null 値が発生することがその型を使用して、F# など、.NET Framework で記述されていない API を使用している場合。

使用することができます、 `option` F# 参照変数を別の .NET 言語で使用できる null 値で使用するときに入力します。 Null の場合、代わりに、 F# `option`型、オプションの値を使用する`None`オブジェクトが存在しない場合。 オプションの値を使用する`Some(obj)`オブジェクト`obj`オブジェクトがある場合。 詳細については、[オプション](../options.md)に関するページを参照してください。 まだをパックすることに注意してください、`null`オプションに値の場合の`Some x`、`x`たまたま`null`。 このためが使用する重要な`None`、値が`null`します。

`null`キーワードは、F# 言語では、有効なキーワードと、.NET Framework Api または他の .NET 言語で記述されている他の Api を使用しているときに使用する必要があります。 Null 値をする必要があります、2 つの状況は、.NET API を呼び出すし、引数として null 値を渡すされ、戻り値または .NET メソッドの呼び出しからの出力パラメーターを解釈するときに。

.NET メソッドに null 値を渡すだけ使用して、`null`呼び出しコードのキーワード。 これを次のコード例に示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

.NET メソッドから取得した null 値を解釈するには、可能な場合に一致するパターンを使用します。 次のコード例は、パターン マッチングを使用して、返される null 値を解釈する方法を示しています。`ReadLine`入力ストリームの末尾を越えて読み取りを実行しようとする場合。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

使用する場合など、他の方法で F# 型の null 値を生成することも`Array.zeroCreate`、呼び出す`Unchecked.defaultof`します。 このようなコードをカプセル化された null 値を保持するには注意が必要です。 専用の F# ライブラリでは、すべての関数で null 値をチェックする必要はありません。 他の .NET 言語と相互運用ライブラリを作成する場合 null チェックが入力パラメーターと、スローを追加する必要があります、 `ArgumentNullException`、c# または Visual Basic コードで行うのと同様です。

次のコードを使用すると、任意の値が null を確認します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>関連項目

- [値](index.md)
- [match 式](../match-expressions.md)
