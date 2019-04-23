---
title: Byref
description: Byref と F# での低レベルのプログラミングに使用される byref のような種類について説明します。
ms.date: 09/02/2018
ms.openlocfilehash: c0bad26672fbb9eb315eee1c3e275183ddeb9297
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59055366"
---
# <a name="byrefs"></a>Byref

F#低レベルのプログラミングの領域で処理する 2 つの主要な機能領域があります。

* `byref` / `inref` / `outref`マネージ ポインターである型。 使用量に制限があるできるように、実行時に無効なプログラムをコンパイルすることはできません。
* A `byref`-これは構造体のように、[構造](structures.md)のようなセマンティクスと同じコンパイル時の制限を持つ`byref<'T>`します。 1 つの例は、<xref:System.Span%601>します。

## <a name="syntax"></a>構文

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a>Byref、inref、および outref

3 つの形式がある`byref`:

* `inref<'T>`、基になる値を読み取るためのマネージ ポインター。
* `outref<'T>`、基になる値を書き込むためのマネージ ポインター。
* `byref<'T>`、基になる値の読み取りと書き込み用のマネージ ポインター。

A`byref<'T>`を渡すことができます、`inref<'T>`が必要です。 同様に、`byref<'T>`を渡すことができます、`outref<'T>`が必要です。

## <a name="using-byrefs"></a>Byref を使用します。

使用する、 `inref<'T>`、ポインター値を取得する必要がある`&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    
let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

使用して、ポインターに書き込む、`outref<'T>`または`byref<'T>`へのポインターを取得する値を行う必要があります`mutable`します。

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

読み取りではなくポインターのみを記述する場合は、使用を検討して`outref<'T>`の代わりに`byref<'T>`します。

### <a name="inref-semantics"></a>Inref セマンティクス

次のコードがあるとします。

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

意味は次の意味としては。

* 所有者、`x`ポインターにのみ使用できますが、値の読み取り。
* ポインターが取得される`struct`内で入れ子になったフィールド`SomeStruct`型を指定して、`inref<_>`します。

次に示します。 また場合は true。

* ない暗黙的の他のスレッドまたはエイリアスへの書き込みアクセスはありません。`x`します。
* 意味はありませんが`SomeStruct`して不変`x`されている、 `inref`。

ただし、F# のある値型**は**、変更できない、`this`ポインターは、推論、`inref`します。

一緒にこれらのルールのすべてからの所有者といって、`inref`ポインターは、即時に示されるメモリの内容を変更できません。

### <a name="outref-semantics"></a>Outref セマンティクス

目的は、`outref<'T>`をからポインターを読み取るだけことを示すことです。 予期せず、`outref<'T>`名前とは異なり値の読み取り、基になることができます。 これは、互換性のため。 意味としては、`outref<'T>`は変わりません`byref<'T>`します。

### <a name="interop-with-c"></a>C との相互運用\#

C# のサポート、`in ref`と`out ref`に加えて、キーワード`ref`を返します。 次の表は、F# を解釈する方法と C# は出力を示しています。

|コンス トラクター (C#)|F#推論|
|------------|---------|
|`ref` 戻り値|`outref<'T>`|
|`ref readonly` 戻り値|`inref<'T>`|
|`in ref` パラメーター|`inref<'T>`|
|`out ref` パラメーター|`outref<'T>`|

次の表では、どのような F# は出力を示します。

|F#コンス トラクター|生成されたコンス トラクター|
|------------|-----------------|
|`inref<'T>` 引数|`[In]` 引数の属性|
|`inref<'T>` 戻り値|`modreq` 値の属性|
|`inref<'T>` 抽象スロットまたは実装|`modreq` 引数または戻り値|
|`outref<'T>` 引数|`[Out]` 引数の属性|

### <a name="type-inference-and-overloading-rules"></a>型の推定とオーバー ロードの規則

`inref<'T>`型は、次の場合に F# コンパイラによって推論されます。

1. .NET パラメーターまたは戻り値型を持つ、`IsReadOnly`属性。
2. `this`変更可能なフィールドを持たない構造体の型のポインター。
3. メモリの場所のアドレスが別の派生`inref<_>`ポインター。

暗黙的なアドレスのとき、`inref`が行われている、型の引数とオーバー ロード`SomeType`型の引数とオーバー ロードに優先`inref<SomeType>`。 例えば:

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

どちらを取るオーバー ロード`System.DateTime`を取るオーバー ロードではなく解決`inref<System.DateTime>`します。

## <a name="byref-like-structs"></a>Byref のような構造体

加え、 `byref` / `inref` / `outref`の 3 つに従うことができます独自の構造体を定義する`byref`-などのセマンティクスです。 これは、<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>属性。

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` 限りません`Struct`します。 両方は、型に存在する必要があります。

A"`byref`のような"F# の構造体はスタック バインド値の型。 マネージ ヒープに割り当てられることはありません。 A `byref`-と同様に、強力な確認については、有効期間と非キャプチャのセットをそのポリシーが適用されて、構造体です、高性能なプログラミングに便利です。 規則は次のとおりです。

* メソッドを返します関数パラメーター、メソッド パラメーター、ローカル変数を使用ができます。
* 静的またはインスタンス クラスまたは構造体を通常のメンバーができません。
* 任意のクロージャ コンストラクトをキャプチャできない (`async`メソッドまたはラムダ式)。
* これらは、ジェネリック パラメーターとして使用できません。

この最後の点が F# パイプライン スタイル プログラミングでは、非常に重要として`|>`はその入力の型をパラメーター化されるジェネリック関数です。 この制限を緩和することがあります`|>`今後は、インライン、本体内にインライン展開の非ジェネリック関数への呼び出しを行いません。

これらの規則は、使用状況を制限する非常に強く、それによって、安全な方法でのハイ パフォーマンス コンピューティングの約束を実行するためにします。

## <a name="byref-returns"></a>Byref 戻り値します。

Byref 返しますF#関数またはメンバーを生成および使用されます。 使用するときに、 `byref`-メソッドを返すには、値が暗黙的に逆参照します。 例:

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

複数の連鎖呼び出しを使って参照を渡すなど、暗黙の型の逆参照を回避するために使用`&x`(場所`x`値です)。

戻り値を割り当てることができますも直接`byref`します。 次の (非常に命令的) プログラムを検討してください。

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

出力結果は次のとおりです。

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Byref の範囲の設定

A `let`-バインドされた値の参照が定義された範囲を超えることはできません。 たとえば、次は許可されません。

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

こうと、最適化をオンまたはオフをコンパイルする場合に応じて異なる結果を取得します。
