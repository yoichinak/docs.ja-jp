---
title: 値のオプション
description: オプションの種類の構造体のバージョンでは、F# の値のオプションの種類について説明します。
ms.date: 02/06/2019
ms.openlocfilehash: e1036c83189c853b3704d94ca245e4818acc98c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982580"
---
# <a name="value-options"></a>値のオプション

値のオプションの種類でF#、次の 2 つの状況を保持しているときに使用します。

1. シナリオに適した、 [F# オプション](options.md)します。
2. 構造体を使用して自分のシナリオでパフォーマンス上の利点を提供します。

すべてのパフォーマンスが重視されるシナリオは、構造体を使用して、「解決」されます。 参照型の代わりに使用するときに、コピーの追加のコストを考慮する必要があります。 ただし、大規模なF#プログラムが通常ホット パスを通過する多くの省略可能な型をインスタンス化し、このような場合は、構造体は多くの場合、プログラムの有効期間の全体的なパフォーマンスの向上を生成します。

## <a name="definition"></a>定義

として値オプションが定義されている、[構造体の判別共用体](discriminated-unions.md#struct-discriminated-unions)参照オプションの種類に似ています。 その定義は、この方法の見なすことができます。

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

構造の等値と比較する値のオプションが準拠しています。 主な違いは、あるコンパイル済みの名前、型名、および大文字と小文字の名前を示す値型であります。

## <a name="using-value-options"></a>値のオプションを使用します。

値のオプションを使用して同様[オプション](options.md)します。 `ValueSome` 値が存在することを示すために使用し、`ValueNone`値が存在しない場合に使用されます。

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

同様[オプション](options.md)を返す関数の名前付け規則`ValueOption`の前にプレフィックスが、`try`します。

## <a name="value-option-properties-and-methods"></a>オプションの値のプロパティとメソッド

この時点で値のオプションの 1 つのプロパティがある:`Value`します。 <xref:System.InvalidOperationException>値には、このプロパティの呼び出し時に存在するがない場合に発生します。

## <a name="value-option-functions"></a>オプションの値関数

値のオプションの 1 つのモジュール連結関数が現在`defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

同様、`defaultArg`関数、`defaultValueArg`特定値オプションの基になる値を返しますが存在する。 それ以外の場合、指定した既定値を返します。

この時点では、値のオプションの場合は、他のモジュール連結関数はありません。

## <a name="see-also"></a>関連項目

- [オプション](options.md)
