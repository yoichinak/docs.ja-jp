---
title: 列挙
description: リテラルの代わりにF#列挙を使用して、コードを読みやすく、保守しやすくする方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630344"
---
# <a name="enumerations"></a>列挙

列挙*型とも*呼ばれる*列挙体*は、値のサブセットにラベルが割り当てられる整数型です。 リテラルの代わりに使用すると、コードの読み取りおよび保守が容易になります。

## <a name="syntax"></a>構文

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Remarks

列挙体は、値を指定できる点を除いて、単純な値を持つ判別共用体とよく似ています。 値は通常、0または1から始まる整数、またはビット位置を表す整数です。 列挙体がビット位置を表すことを目的としている場合は、 [Flags](xref:System.FlagsAttribute)属性も使用する必要があります。

列挙型の基になる型は、使用されるリテラルから決定されます。したがって、たとえば`1u`、、 `2u`などのサフィックスでリテラルを使用して、符号なし整数 (`uint32`) 型にすることができます。

名前付きの値を参照する場合は、列挙型自体の名前を修飾子として使用する必要があり`enum-name.value1`ます。これ`value1`は、だけではありません。 この動作は、判別共用体の動作とは異なります。 これは、列挙体には常に[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)属性が含まれているためです。

次のコードは、列挙体の宣言と使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

次のコードに示すように、適切な演算子を使用して、列挙型を基になる型に簡単に変換できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

列挙`sbyte`型は`byte` 、、`char`、 `uint16` 、`int32` 、、`uint32`、、、、およびのいずれかの基になる型を持つことができます。 `int64` `int16` `uint16` `uint64` 列挙型は、から`System.Enum`継承される型として .NET Framework で表されます。これは、から`System.ValueType`継承されます。 したがって、これらは、スタックに配置されている値型、または親オブジェクトのインラインにある値型であり、基になる型の値は列挙体の有効な値です。 これは、名前のない値をキャッチするパターンを指定する必要があるため、列挙値でパターンマッチングを行う場合に非常に重要です。

`enum`関数の F# ライブラリで使用できます、定義済みの以外の値も、列挙値を生成する名前付きの値。 関数は次`enum`のように使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

既定`enum`の関数は、型`int32`で動作します。 そのため、基になるその他の型を持つ列挙型では使用できません。 代わりに、次のものを使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

さらに、列挙型のケースは常`public`にとして出力されます。 これは、とその他のC# .net プラットフォームとの連携を行うためのものです。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [キャストと変換](casting-and-conversions.md)
