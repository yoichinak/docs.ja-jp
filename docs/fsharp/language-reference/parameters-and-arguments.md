---
title: パラメーターと引数
description: パラメーターを定義して、関数、メソッド、およびプロパティに引数を渡すのための F# 言語サポートについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: b68b3fdd14a66a7312efa5adb709adaeceaae282
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352284"
---
# <a name="parameters-and-arguments"></a>パラメーターと引数

このトピックでは、パラメーターを定義して、関数、メソッド、およびプロパティに引数を渡すのための言語サポートについて説明します。 定義して、可変個の引数を取ることがメソッドを使用する方法と、参照渡しする方法の詳細情報が含まれます。

## <a name="parameters-and-arguments"></a>パラメーターと引数

用語*パラメーター*を指定すると予想される値の名前を表すために使用します。 用語*引数*に各パラメーターに指定された値のために使用します。

タプル、カリー化形式、または 2 つの組み合わせで、パラメーターを指定できます。 明示的なパラメーターの名前を使用して引数を渡すことができます。 メソッドのパラメーターを省略可能として指定し、既定値を指定できます。

## <a name="parameter-patterns"></a>パラメーターのパターン

関数やメソッドに指定されたパラメーターとは、一般に、スペースで区切られたパターンを指します。 これは、原則として、パターンのいずれかの説明では意味[一致式](match-expressions.md)関数またはメンバーのパラメーター リストで使用できます。

メソッドは、通常は引数の受け渡しの組形式を使用します。 タプル形式の .NET メソッドで引数が渡される方法に一致するため、他の .NET 言語の観点からのわかりやすい結果が得られます。

カリー化されたフォームを使用して作成した関数でよく使用`let`バインドします。

次の疑似コードは、タプルとカリー化された引数の例を示します。

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

タプルにいくつかの引数があり、一部がする場合は、結合されたフォームです。

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

その他のパターンは、パラメーター リストでも使用できますが、実行時に不完全な一致が存在できる可能性がありますパラメーターのパターンが可能なすべての入力が一致しない場合。 例外`MatchFailureException`引数の値がパラメーター リストで指定されたパターンと一致しない場合に生成されます。 パラメーターのパターンは、不完全な一致の場合、コンパイラは警告を発行します。 他に少なくとも 1 つのパターンは、パラメーター リストの一般的に便利ですし、ワイルドカード パターンです。 提供される引数を無視するだけの場合にパラメーター リストでワイルドカード パターンを使用するとします。 次のコードでは、引数リスト内のワイルドカード パターンの使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

ワイルドカード パターンには、通常次のコードのように、文字列の配列として指定されるコマンドライン引数が必要ないときに、プログラムのメイン エントリ ポイントなど、渡された引数を必要としないときに便利です。 を指定できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

引数で使用されることが他のパターンは、`as`パターン、および判別共用体とアクティブ パターンに関連付けられた識別子パターン。 次のように単一ケースの判別共用体パターンを使用することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

出力は次のとおりです。

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

アクティブ パターンは、引数を次の例のように、目的の形式に変換するときに、たとえば、パラメーターとして役立ちます。

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

使用することができます、`as`パターンを次のコード行に示すように、ローカルの値として、一致した値を格納します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

使用されることがもう 1 つのパターンは、関数の本文として提供して、名前のない最後の引数を関数では、すぐに、暗黙的な引数をパターン マッチングを実行するラムダ式です。 この例では、次のコード行です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

このコードをジェネリック リストを受け取りを返す関数を定義する`true`リストが空の場合と`false`それ以外の場合。 このような手法を使用すると、コードが読みにくくします。

場合によっては、不完全な一致を含むパターンは便利です、たとえば、プログラムに含まれる一覧は、のみの 3 つの要素である場合は、可能性がありますで使用する、次のようなパターン パラメーター リスト。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

不完全な一致パターンの使用は、クイック プロトタイプを作成し、その他の一時的な使用に最適な予約されています。 コンパイラでは、このようなコードの警告を発行します。 このようなパターンは、すべての可能な入力の一般的なケースを取り上げることはできません、そのため、コンポーネント Api に適したはありません。

## <a name="named-arguments"></a>名前付き引数

メソッドの引数は、引数のコンマ区切りリストでは、位置によって指定できます。 またはができるメソッドに渡される、明示的に続けて等号 (=) とで渡される値の名前。 名前を提供することで指定した場合は、宣言で使用するとは異なる順序で表示されることができます。

名前付き引数できるようにコードより読みやすくより適応性のある特定の種類のメソッドのパラメーターの順序変更など、API の変更します。

名前付き引数がなく、メソッドに対してのみ許可されます`let`-関数、関数値、またはラムダ式をバインドします。

次のコード例では、名前付き引数の使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

クラスのコンス トラクターの呼び出しでは、名前付き引数と同様の構文を使用して、クラスのプロパティの値を設定できます。 次の例では、この構文を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

詳細については、次を参照してください。[コンス トラクター (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)します。

## <a name="optional-parameters"></a>省略可能なパラメーター

パラメーター名の前に疑問符を使用して、メソッドのオプションのパラメーターを指定できます。 使用して、オプションの種類がクエリを通常の方法でそのクエリを実行できるように、省略可能なパラメーターは F# オプションの種類として解釈されます、`match`式`Some`と`None`します。 省略可能なパラメーターを使用して作成した関数ではなく、メンバーでのみ許可`let`バインドします。

既存の省略可能な値に渡せるメソッドをパラメーター名のなど`?arg=None`または`?arg=Some(3)`または`?arg=arg`します。 これは、別のメソッドに省略可能な引数を渡すメソッドを構築するときに役立ちます。

関数を使用することもできます。 `defaultArg`、省略可能な引数の既定値を設定します。 `defaultArg`関数は、最初の引数と省略可能なパラメーターと、2 つ目として、既定値を受け取ります。

次の例では、省略可能なパラメーターの使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

出力は次のとおりです。

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

目的でC#および属性を使用する Visual Basic の相互運用`[<Optional; DefaultParameterValue<(...)>]`でF#、呼び出し元がオプションとして、引数を参照してください。 オプションとして、引数を定義するのと同じC#うに`MyMethod(int i = 3)`します。

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

パラメーターの既定値として、新しいオブジェクトを指定することもできます。 たとえば、`Foo`メンバーが省略可能なことが`CancellationToken`代わりに入力として。

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

引数として指定された値`DefaultParameterValue`パラメーターの型に一致する必要があります。 たとえば、次は許可されていません。

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

この場合、コンパイラは警告が生成され、両方の属性を完全に無視されます。 なお、既定値`null`型の注釈がある必要がありますそれ以外の場合、問題の型の推測コンパイラつまり`[<Optional; DefaultParameterValue(null:obj)>] o:obj`します。

## <a name="passing-by-reference"></a>参照渡しで渡す

渡す、F#参照によって値が含まれます[byref](byrefs.md)、マネージ ポインター型であります。 使用する型は次のようにガイダンス:

* 使用`inref<'T>`のみをポインターを読み取る必要がある場合。
* 使用`outref<'T>`のみ、ポインターを記述する必要がある場合。
* 使用`byref<'T>`から読み取るし、ポインターへの書き込みの両方に必要な場合。

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

パラメーターがポインター値が変更可能なため、値への変更は、関数の実行後に保持されます。

戻り値として組を使用して格納できる`out`.NET ライブラリのメソッドのパラメーター。 または、扱うことができます、`out`パラメーターとして、`byref`パラメーター。 次のコード例では、両方の方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>パラメーター配列

場合によっては任意の数の異機種混在型のパラメーターを受け取る関数を定義する必要です。 アカウントのために使用できるすべての種類を使用できるオーバー ロードされたメソッドを作成するは実用的はできません。 .NET 実装では、パラメーター配列の機能では、このようなメソッドがサポートされます。 任意の数のパラメーターでは、そのシグニチャにパラメーター配列を受け取るメソッドを提供できます。 パラメーターは、配列に格納されます。 配列の要素の型は、関数に渡すことができるパラメーターの型を決定します。 パラメーター配列を定義する場合`System.Object`要素の型として、クライアント コードできます値を渡す任意の型。

F#、パラメーター配列は、メソッドでのみ定義できます。 これらは、スタンドアロン関数またはモジュールで定義されている関数で使用できません。

使用して、パラメーター配列を定義する、`ParamArray`属性。 `ParamArray`属性は、最後のパラメーターにのみ適用できます。

次のコードは、パラメーター配列を受け取るメソッドを持つ F# では、パラメーター配列と型の定義を .NET メソッドを呼び出して両方を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

プロジェクトで実行すると、前のコードの出力のとおりです。

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>関連項目

- [メンバー](members/index.md)
