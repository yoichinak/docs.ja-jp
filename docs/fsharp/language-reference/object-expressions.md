---
title: オブジェクト式
description: 名前付きの型コードを追加し、新たに作成するために必要なオーバーヘッドを回避するときに、F# オブジェクト式を使用する方法をについて説明します。
ms.date: 02/08/2019
ms.openlocfilehash: 63f2c1d7128721b7b8c744e4cf02d73c2a8b4a07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157853"
---
# <a name="object-expressions"></a>オブジェクト式

*オブジェクト式*は動的に作成された、匿名のオブジェクトの種類の新しいインスタンスを作成する式が、既存の基本型、インターフェイス、またはインターフェイスのセットに基づいてです。

## <a name="syntax"></a>構文

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Remarks

前の構文で、 *typename*既存のクラス型またはインターフェイス型を表します。 *型 params*省略可能なジェネリック型パラメーターについて説明します。 *引数*コンス トラクターのパラメーターを必要とするクラス型にのみ使用されます。 *メンバー定義*は基底クラスのメソッドのオーバーライドまたは基底クラスまたはインターフェイスのいずれかの抽象メソッドの実装。

次の例は、さまざまな種類のオブジェクト式を示しています。

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn "%A" obj1

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a>オブジェクトの式の使用

余分なコードと名前付きの型を新しく作成する必要なオーバーヘッドを回避する場合に、オブジェクトの式を使用します。 プログラムで作成された型の数を最小限に抑えるには、オブジェクト表現を使用する場合のコード行の数を削減し、型の不要な急増を回避できます。 特定の状況に対処するためだけに多くの種類を作成する代わりには、既存の種類をカスタマイズできます。 または、特定の状況に適切なインターフェイスの実装を提供するオブジェクト式を使用することができます。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
