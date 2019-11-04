---
title: 値のオプション
description: F# Value オプションの型について説明します。これは、オプションの型の構造体のバージョンです。
ms.date: 02/06/2019
ms.openlocfilehash: 4dc3f7217943345b7aaf1165fd648ab2e01bd727
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424013"
---
# <a name="value-options"></a>値のオプション

次の2つのF#状況では、の値オプションの種類が使用されます。

1. シナリオは、 [ F#オプション](options.md)に適しています。
2. 構造体を使用すると、シナリオにおけるパフォーマンス上の利点が得られます。

すべてのパフォーマンスを重視するシナリオは、構造体を使用して "解決" されるわけではありません。 参照型の代わりに使用する場合は、コピーにかかる追加コストを考慮する必要があります。 ただし、大F#規模なプログラムでは、多くの場合、ホットパスを通過する多くの省略可能な型がインスタンス化されるため、多くの場合、構造体はプログラムの有効期間全体のパフォーマンスを向上させることができます。

## <a name="definition"></a>定義

Value オプションは、参照オプションの型に似た[構造体の判別共用体](discriminated-unions.md#struct-discriminated-unions)として定義されます。 その定義は、次のように考えることができます。

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

値オプションは構造的等価性と比較に準拠しています。 主な違いは、コンパイルされた名前、型名、およびケース名はすべて、値型であることを示しています。

## <a name="using-value-options"></a>Value オプションの使用

値のオプションは、[オプション](options.md)と同じように使用されます。 値が存在することを示すために `ValueSome` を使用し、値が存在しない場合は `ValueNone` を使用します。

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

[オプション](options.md)と同様に、`ValueOption` を返す関数の名前付け規則は、`try`にプレフィックスを付けることです。

## <a name="value-option-properties-and-methods"></a>Value オプションのプロパティとメソッド

現時点では、Value オプションには、`Value`の1つのプロパティがあります。 このプロパティが呼び出されたときに値が存在しない場合は、<xref:System.InvalidOperationException> が発生します。

## <a name="value-option-functions"></a>Value オプションの関数

現時点では、値のオプションにはモジュールバインド関数が1つ `defaultValueArg`。

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

`defaultArg` 関数と同様に、`defaultValueArg` は、指定された Value オプションが存在する場合は、基になる値を返します。それ以外の場合は、指定された既定値を返します。

現時点では、値オプション用のモジュールバインド関数は他にありません。

## <a name="see-also"></a>関連項目

- [Options](options.md)
