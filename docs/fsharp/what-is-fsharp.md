---
title: F# とは
description: どのような F# プログラミング言語とはなどの F# プログラミングについて説明します。 豊富なデータ型、関数、およびそれらがどのように組み合わされているかについて説明します。
ms.date: 08/03/2018
ms.openlocfilehash: 0c576fe49fadebd68e4fc9d2b20ea8f0cb991af5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630463"
---
# <a name="what-is-f"></a>F とは\#

F#は、適切で保守が容易なコードを簡単に記述できるようにする関数型プログラミング言語です。

F#プログラミングでは、主に、型が推論され、自動的に一般化される型と関数を定義する必要があります。 これにより、プログラミングの詳細ではなく、問題のドメインにとどまり、そのデータを操作することができます。

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn "%s" greeting)

    0
```

F#には、次のようなさまざまな機能があります。

* 簡易構文
* 既定で変更不可
* 型の推論と自動汎化
* ファーストクラス関数
* 強力なデータ型
* パターン マッチング
* 非同期プログラミング

機能の完全なセットが記載されて、 [F# 言語リファレンス](./language-reference/index.md)します。

## <a name="rich-data-types"></a>豊富なデータ型

[レコード](./language-reference/records.md)や[判別共用体](./language-reference/discriminated-unions.md)などのデータ型を使用すると、複雑なデータとドメインを表すことができます。

```fsharp
// Group data with Records
type SuccessfulWithdrawal = {
    Amount: decimal
    Balance: decimal
}

type FailedWithdrawal = {
    Amount: decimal
    Balance: decimal
    IsOverdraft: bool
}

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

F#レコードと判別共用体は、null ではなく、変更できず、既定では比較可能であるため、非常に使いやすくなっています。

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>関数とパターンマッチングでの強制的な正確性

F#関数は、実際には簡単に宣言でき、非常に強力です。 [パターンマッチング](./language-reference/pattern-matching.md)と組み合わせると、コンパイラによって正確性が強制される動作を定義できます。

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f" s.Amount
    | InsufficientFunds f -> printfn "Failed: balance is %f" f.Balance
    | CardExpired d -> printfn "Failed: card expired on %O" d
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

F#関数もファーストクラスであり、パラメーターとして渡し、他の関数から返すことができます。

## <a name="functions-to-define-operations-on-objects"></a>オブジェクトに対する操作を定義する関数

F#では、オブジェクトが完全にサポートされています。これは、データと機能をブレンドする必要がある場合に便利なデータ型です。 F#関数は、オブジェクトの操作に使用されます。

```fsharp
type Set<[<EqualityConditionOn>] 'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

[<RequireQualifiedAccess>]
module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

でF#は、オブジェクト指向のコードを記述するのではなく、多くの場合、オブジェクトを操作する関数の別のデータ型として扱うコードを記述します。 などの機能[ジェネリック インターフェイス](./language-reference/interfaces.md)、[オブジェクト式](./language-reference/object-expressions.md)とを賢く利用[メンバー](./language-reference/members/index.md)は大規模な F# プログラムでは一般的です。

## <a name="next-steps"></a>次の手順

多数の F# の機能の詳細については、チェック アウト、 [F# のツアー](tour.md)します。
