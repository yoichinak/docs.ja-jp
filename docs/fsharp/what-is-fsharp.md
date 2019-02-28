---
title: 新機能F#
description: どのような F# プログラミング言語とはなどの F# プログラミングについて説明します。 豊富なデータ型、関数、およびそれらをまとめる方法について説明します。
ms.date: 08/03/2018
ms.openlocfilehash: ea82147e4e6d3c980fb224eeafd805c7ed53f8f2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966961"
---
# <a name="what-is-f"></a>F とは\#

F#関数型プログラミング言語を適切な保守しやすいコードを記述するが容易にするにです。

F#主にプログラミングするには、型と型推論され、自動的に汎用化されている関数を定義する必要があります。 これにより、問題のドメインとプログラミングの詳細ではなく、そのデータの操作上に残すに専念できます。

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

F#など、多数の機能があります。

* 軽量構文
* 既定では変更できません。
* 型の推論と自動ジェネリック化
* ファーストクラス関数
* 強力なデータ型
* パターン マッチング
* 非同期プログラミング

機能の完全なセットが記載されて、 [F# 言語リファレンス](language-reference/index.md)します。

## <a name="rich-data-types"></a>豊富なデータ型

などのデータ型[レコード](language-reference/records.md)と[判別共用体](language-reference/discriminated-unions.md)複雑なデータとドメインを表現することができます。

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

F#レコード、判別共用体は、null 以外、変更できない、および簡単に使用できるように、既定では同等です。

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>関数およびパターン マッチングで正確性を強制

F#関数は、宣言する簡単で実際には強力です。 組み合わせると[パターン マッチング](language-reference/pattern-matching.md)コンパイラが正確性が適用される動作を定義することができます。

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

F#関数は、ファースト クラス、つまりパラメーターとして渡され、その他の関数から返されることができますも。

## <a name="functions-to-define-operations-on-objects"></a>オブジェクトに対する操作を定義する関数

F#有用なデータ型は、blend のデータと機能する必要がある場合、オブジェクトの完全サポートしています。 F#オブジェクトを操作する関数が使用されます。

```fsharp
type Set<[<EqualityConditionOn>] ‘T when ‘T: comparison>(elements: seq<'T>) =
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

内のオブジェクト指向コードを記述するのではなくF#、オブジェクトを操作する関数として別のデータ型を処理するコードを記述する多くの場合。 などの機能[ジェネリック インターフェイス](language-reference/interfaces.md)、[オブジェクト式](language-reference/object-expressions.md)とを賢く利用[メンバー](language-reference/members/index.md)は大規模な F# プログラムでは一般的です。

## <a name="next-steps"></a>次の手順

多数の F# の機能の詳細については、チェック アウト、 [F# のツアー](tour.md)します。