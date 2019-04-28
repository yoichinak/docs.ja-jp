---
title: 列挙
description: 使用する方法について説明しますF#読みやすく、保守しやすいコードにするためのリテラルの代わりに列挙体。
ms.date: 05/16/2016
ms.openlocfilehash: a8839b73de074f62606b70ffe969a53b3db753bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921577"
---
# <a name="enumerations"></a>列挙

*列挙体*とも呼ばれます*列挙型*、および整数型は、ラベルが割り当てられ、値のサブセットにします。 リテラルの代わりに使用すると、コードの読み取りおよび保守が容易になります。

## <a name="syntax"></a>構文

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Remarks

値を指定する点を除いてを単純な値を持つ判別共用体と同様、列挙型を検索します。 通常、値は、0 または 1 から始まる整数またはビット位置を表す整数です。 またを使用する必要がある列挙体のビット位置を表す場合は、[フラグ](xref:System.FlagsAttribute)属性。

、たとえば、を使用できるようにリテラル、サフィックスを持つように、使用されるリテラルから列挙体の基になる型が決定されます`1u`、 `2u`、で、符号なし整数 (`uint32`) 型。

名前付きの値を参照するときにする必要がありますとして使用する列挙型自体の名前、修飾子は、`enum-name.value1`だけでなく、`value1`します。 この動作は、判別共用体の動作とは異なります。 これは、列挙型が常にあるため、 [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)属性。

次のコードでは、宣言と列挙型の使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

適切な演算子を使用して基になる型には、次のコードに示すように、列挙型を変換できます簡単にします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

列挙型は、次の基になる型のいずれかを指定できます: `sbyte`、 `byte`、 `int16`、 `uint16`、 `int32`、 `uint32`、 `int64`、 `uint16`、 `uint64`、および`char`します。 列挙型は、.NET Framework でから継承された型として表されます。 `System.Enum`、から継承順番`System.ValueType`します。 したがって、スタックまたは親オブジェクトでのインラインに配置されている値型では、基になる型の任意の値が列挙体の有効な値。 これは重要な場合、パターン マッチに列挙値の名前のない値をキャッチするパターンを指定する必要があるためです。

`enum`関数の F# ライブラリで使用できます、定義済みの以外の値も、列挙値を生成する名前付きの値。 使用する、`enum`次のように機能します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

既定の`enum`関数は型で機能`int32`します。 そのため、基になるその他の型を持つ列挙型で使用できません。 代わりに、次を使用します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

さらに、ケースの列挙型として常に出力されます。`public`します。 これは、c# および .NET プラットフォームの残りの部分に配置します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [キャストと変換](casting-and-conversions.md)