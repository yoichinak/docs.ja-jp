---
title: F# のコーディング規則
description: 書き込み時に、一般的なガイドラインと表現方法を説明しますF#コード。
ms.date: 05/14/2018
ms.openlocfilehash: 4b292d0a844a4d9efc79aa865b054b4af2cb68c4
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052792"
---
# <a name="f-coding-conventions"></a>F# のコーディング規則

大規模な F# を使用した経験から、次の規則が確立されますコードベースです。 [優れた F# コードの 5 つの原則](index.md#five-principles-of-good-f-code)各推奨事項の基盤となっています。 関連している、 [F# コンポーネント デザインのガイドライン](component-design-guidelines.md)が、F# コード、ライブラリなどだけでなく、コンポーネントに適用できます。

## <a name="organizing-code"></a>コードを整理します。

F#コードを整理する主な方法は 2 つの機能: モジュールや名前空間。 これらは似ていますが、次の違いがあります。

* 名前空間は、.NET 名前空間としてコンパイルされます。 モジュールは、静的クラスとしてコンパイルされます。
* 名前空間は、常に最上位レベルです。 モジュールは、最上位と他のモジュール内の入れ子にできます。
* 名前空間は、複数のファイルにまたがることができます。 モジュールことはできません。
* モジュールで修飾できます`[<RequireQualifiedAccess>]`と`[<AutoOpen>]`します。

次のガイドラインを使用すると、これらを使用して、コードを整理できます。

### <a name="prefer-namespaces-at-the-top-level"></a>最上位レベルの名前空間を優先します。

公開コードに対して名前空間は、最上位レベルのモジュールに優先します。 .NET 名前空間としては、コンパイル、ため問題はありませんで c# から使用できるようにされます。

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

最上位レベルのモジュールを使用して表示が、F# からのみ呼び出されるとは異なるされません可能性がありますが、消費者向け C# は、呼び出し元を修飾することに驚かれる可能性があります`MyClass`で、`MyCode`モジュール。

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>慎重に適用します。 `[<AutoOpen>]`

`[<AutoOpen>]`コンストラクトが煩雑に呼び出し元に対して使用できる機能のスコープと、どこから何か取得の答えが「マジック」. これは一般に良いことです。 このルールの例外は、(ただし、このことは、少し意見の分かれるも) 自体 F# コア ライブラリです。

ただし、パブリック API そのパブリック API からとは別に整理するをヘルパー機能がある場合、利便性を勧めします。

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

これにより、関数のパブリック API から明確に別の実装の詳細メソッドを呼び出すたびに、ヘルパーを完全に修飾しなくてもできます。

さらに、拡張メソッドと名前空間レベルで式ビルダーを公開するきれいで表現できる`[<AutoOpen>]`します。

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>使用`[<RequireQualifiedAccess>]`たびに名前が競合する可能性がありますまたは読みやすさが容易になると思われる

追加、`[<RequireQualifiedAccess>]`属性をモジュールには、モジュールが開かれていないことと、アクセスを修飾するモジュールの要素への参照が明示的に必要なことを示します。 たとえば、`Microsoft.FSharp.Collections.List`モジュールにはこの属性があります。

これは、機能は、関数と、モジュール内の値は、他のモジュール名と競合する可能性のある名前を持つ場合に便利です。 修飾のアクセスを必要とすると、長期的な保守容易性とライブラリの発展が大幅に向上できます。

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>並べ替え`open`ステートメント位相的

F#、宣言問題などの順序`open`ステートメント。 これとは異なり、C# の場合は、場所の効果`using`と`using static`はファイルでこれらのステートメントの順序に依存しません。

F#、スコープに開かれた要素をシャドウする他のユーザーに既に存在します。 つまり、その並べ替え`open`ステートメントは、コードの意味を変更できます。 その結果、任意のすべての並べ替え`open`ステートメント (たとえば、アルファベット) は一般的に使用しないで、考えられるさまざまな動作を生成するようにします。

並べ替えたりする代わりに、推奨[位相的](https://en.wikipedia.org/wiki/Topological_sorting); は、注文、`open`順序内のステートメント_レイヤー_システムの定義します。 英数字のトポロジの異なるレイヤー内での並べ替えを行うことがありますも見なされます。

たとえば、次の F# コンパイラ サービス パブリック API ファイル トポロジカルソートに示します。

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

行の区切りが各レイヤーが後で並べ替えられる英数字順にトポロジのレイヤーを分離に注意してください。 これは、クリーンに誤って値をシャドウすることがなくコードを整理します。

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>副作用がある値を含むクラスを使用します。

値を初期化して、データベースまたはその他のリモート リソースへのコンテキストをインスタンス化するなどの副作用を持つことができる場合回数があります。 モジュールには、このような点を初期化し、後続の関数で使用することも考えです。

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

これは、いくつかの理由から悪い考えでは頻繁に。

アプリケーションの構成をコードベースにプッシュする最初に、`dep1`と`dep2`します。 これより大きなコードベースで保守が困難です。

第 2 に、静的に初期化されたデータは、コンポーネントはそれ自体を使用して複数のスレッドの場合、スレッド セーフではない値を含めないでください。 これは明らかに違反`dep3`します。

最後に、モジュールの初期化は、静的コンス トラクターに、コンパイル ユニット全体をコンパイルします。 としてそのモジュール内の let バインドされた値の初期化でエラーが発生した場合、この制限を`TypeInitializationException`アプリケーションの有効期間にわたって、キャッシュされています。 診断は困難なことができます。 内部例外については、理由を試みることができますが、通常は、ない場合、根本原因を示します。

代わりに、依存関係を保持するのにだけの単純なクラスを使用します。

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

これにより、次のできます。

1. API 自体の外部の依存の状態をプッシュします。
2. 構成は、API の外部で今すぐ実行できます。
3. 従属変数の値の初期化でエラーされない可能性があるとしてマニフェストを`TypeInitializationException`します。
4. API は、テストしやすくなります。

## <a name="error-management"></a>エラー管理

大規模なシステムでエラーの管理は複雑で微妙努力をし、silver、システムを保証するために行頭文字はフォールト トレランスと適切に動作はありません。 次のガイドラインは、この難しい領域内を移動するガイダンスを提供する必要があります。

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>エラー ケースと、ドメインに固有の種類に無効な状態を表す

[判別共用体](../language-reference/discriminated-unions.md)、F# できるようにする、型システムで障害があるプログラムの状態を表すため。 例えば:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

ここでは、銀行口座からお金を現金で失敗する 3 つの既知の方法があります。 各エラーの場合は、型が表示され、したがってで対処できるように安全に、プログラム全体でします。

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

一般に、さまざまな方法をモデル化する場合のことができます**失敗**ドメイン内のエラー処理コードが不要になったとして扱われます何か通常のプログラム フローのほかに対処する必要があります。 通常のプログラム フローの一部だけとは見なされません**例外的な**します。 この 2 つの主な利点があります。

1. ドメインが時間の経過と共に変化を維持するために簡単です。
2. エラーの場合は、単体テストを容易にします。

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>エラーの種類を表すことができないときに例外を使用します。

問題ドメインでは、すべてのエラーを表すことができます。 この種のエラーは*例外的な*そのため、本質的に発生して、F# の例外をキャッチする機能。

まず、お勧めお読みになる、[例外のデザイン ガイドライン](../../standard/design-guidelines/exceptions.md)します。 またこれらは、F# に当てはまります。

次の優先順位では、例外の発生の目的での F# で使用できる主な構造を検討してください。

| 関数 | 構文 | 目的 |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | 発生させる、`System.ArgumentNullException`指定された引数の名前を持つ。 |
| `invalidArg` | `invalidArg "argumentName" "message"` | 発生させる、`System.ArgumentException`指定された引数名とメッセージを使用します。 |
| `invalidOp` | `invalidOp "message"` | 発生させる、`System.InvalidOperationException`指定したメッセージ。 |
|`raise`| `raise (ExceptionType("message"))` | 例外をスローする汎用メカニズムです。 |
| `failwith` | `failwith "message"` | 発生させる、`System.Exception`指定したメッセージ。 |
| `failwithf` | `failwithf "format string" argForFormatString` | 発生させる、`System.Exception`メッセージ書式指定文字列とその入力によって決まります。 |

使用`nullArg`、`invalidArg`と`invalidOp`をスローするためのメカニズムとして`ArgumentNullException`、`ArgumentException`と`InvalidOperationException`適切な場合。

`failwith`と`failwithf`関数は、基本を起動するため、一般に避ける必要がある`Exception`入力と、特定の例外ではありません。 に従って、[例外のデザイン ガイドライン](../../standard/design-guidelines/exceptions.md)、可能な場合より詳細な例外を生成します。

### <a name="using-exception-handling-syntax"></a>例外処理構文を使用してください。

F#使用して例外のパターンをサポートしている、`try...with`構文。

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

調整パターン マッチで例外が発生した場合に実行する機能にコードをクリーンに保持したい場合に、少し難しいことができます。 これを処理するためにこのような方法の 1 つは、使用することです。[アクティブ パターン](../language-reference/active-patterns.md)自体が例外で、エラー ケースを囲むグループ機能するための手段として。 たとえばを例外をスローしたときに、例外のメタデータで貴重な情報を囲む API を使用することがあります。 アクティブ パターン内でキャプチャされた例外の本文内に有効な値のラップを解除して、いくつかの状況で便利な値であることを返します。

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>モナディックのエラーに例外を置き換える処理を使用しないでください。

例外は、関数型プログラミングにややタブーと見なされます。 実際には、例外のません機能を検討するには安全では、純粋性に違反します。 ただし、コードが実行する必要がありますとそのランタイム エラーが発生することが実際には、これは無視されます。 一般に、ほとんどの機能は純粋なもでも合計、不愉快な事件を最小限に抑えることを前提としてコードを記述します。

それは、core 長所/の次の側面例外に関して、関連性と、全体として、.NET ランタイムと言語間のエコシステムで適切かどうかを検討してください。

1. 問題をデバッグするときに非常に便利ですが、詳細な診断情報が含まれます。
2. これらは、ランタイムおよび他の .NET 言語でよく理解されています。
3. 重要な定型コードがその方法を外になるコードと比較した場合に削減できます*回避*臨機応変に、セマンティクスの一部のサブセットを実装することで例外。

この 3 番目の点が重要です。 無視できないほど複雑な操作で例外の使用に失敗する可能性がこのような構造を処理するとき。

```fsharp
Result<Result<MyType, string>, string list>
```

「入力 stringly」エラー時に一致するパターンと同様に脆弱なコードに簡単につながります。

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

さらに、「より良い」の型を返す「単純な」関数の目的で例外を処理することも考えを指定できます。

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

残念ながら、`tryReadAllText`無数のモ ノのファイル システムで実行できるに基づいて多数の例外をスローすることができ、このコードがどのような場合がありますが実際に環境内で問題がについて離れたを破棄します。 結果の型にこのコードを置き換えると場合、その場合は「stringly 入力」のエラー メッセージの解析に。

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

例外オブジェクト自体を配置することで、`Error`コンス トラクターが常に、関数ではなく、呼び出しサイトでの例外の種類と適切に対処します。 これを効果的に行う API の呼び出し元として扱うにたいへん楽しいものではない、チェックされた例外を作成します。

上記の例に適切な代替手段は、キャッチする*特定*例外とその例外のコンテキストで意味のある値を返します。 変更する場合、`tryReadAllText`関数の次のように、`None`意味を持たせるには。

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

キャッチ オールとしてではなく、この関数は今すぐを正しく処理場合ファイルが見つからなかったし、その意味を戻り値を割り当てます。 この戻り値は、そのエラーの場合にいない任意のコンテキスト情報を破棄またはその時点で、コードに関連することができない可能性があるケースを処理する呼び出し元に強制中にマップできます。

などの型`Result<'Success, 'Error>`入れ子になっていないし、F# の省略可能な型がいずれかの戻り値が何か時を表すために最適な場所に基本的な操作に適した*もの*または*nothing*. 例外については、代わりにはなりません、され、使わないでの試行で例外を置換します。 はなく、それらを適用慎重例外とエラー管理ポリシーの特定の側面をアドレスに対象となる方法で。

## <a name="partial-application-and-point-free-programming"></a>一部のアプリケーションおよびポイントのないプログラミング

F#ポイント フリー スタイルでは、一部のアプリケーションとそのため、プログラムをさまざまな方法をサポートしています。 有益モジュールや、なんらかの実装内でコードを再利用できますが、一般的にないパブリックに公開するものです。 一般に、ポイントのないプログラミングでは、自体の長所でないし、スタイルに専念した状態ではない方のため大きな cognitive バリアを追加できます。

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>一部のアプリケーションとパブリック Api でカリー化を使用しないでください。

ほとんどの例外を除き、パブリック Api での部分的なアプリケーションの使用はコンシューマーが混乱することはできます。 通常、 `let`-F# コードでバインドされた値は**値**ではなく、**関数値**します。 などの演算子と組み合わせている場合に特に cognitive のオーバーヘッドがかなりと引き換えコードの行の数が少ないの保存中に発生できます値と関数の値がまとめ`>>`関数を作成します。

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>ポイント無料プログラミング ツールへの影響を検討してください。

カリー化関数には、その引数がラベル付けしません。 ツールへの影響があります。 次の 2 つの関数を検討してください。

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

有効な関数は、両方ともが`funcWithApplication`カリー化された関数です。 エディターでその型をポイントするときにこの参照してください。

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

呼び出しサイトでは、Visual Studio などのツール ヒントは与えない何か意味のある情報、`string`と`int`入力型が実際に表します。

ような点のないコードが発生した場合`funcWithApplication`公開は、すべての η 展開を実行するツールできますでわかりやすい名前を引数に推奨です。

さらに、ポイントのないコードのデバッグが容易では、不可能でない場合。 デバッグ ツールは、名前にバインドされている値に依存して (たとえば、`let`バインド) 実行途中の中間値を検査するようにします。 コードには、検査する値がない、何もないをデバッグします。 今後、進化し、以前に実行されたパスに基づくこれらの値を合成するデバッグ ツールは、おすすめコンテンツをヘッジにすることをお勧めではありません*潜在的な*機能をデバッグします。

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>内部の定型コードを削減する手法として部分的なアプリケーションを検討してください。

前のポイントとは対照的は、部分的なアプリケーションは、アプリケーションまたは API のより深い内部の中での定型コードを削減するためのすばらしいツールです。 これは、単体テストの定型コードが扱い苦痛では多くの場合より複雑な Api の実装に役立ちます。 たとえば、実行する方法を次のコードに示すどのような最もモック作成フレームワークを提供するフレームワークなどの外部の依存関係を行わず、bespoke API の学習、関連します。

たとえば、次のソリューション構造があるとします。

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` などのコードに公開する可能性があります。

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

単体テスト`Transactions.doTransaction`で`ImplementationLogic.Tests.fspoj`は簡単です。

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

部分的に適用する`doTransaction`モック作成のコンテキストでオブジェクトを使うたびに、モックのコンテキストを構築することがなくすべての単体テストで関数を呼び出してできます。

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

この手法は普遍的に適用されません、コードベース全体ですが、複雑な内部構造とそれらの内部構造のテスト単位の定型コードを削減することをお勧めします。

## <a name="access-control"></a>アクセス制御

F#複数のオプションが[アクセス制御](../language-reference/access-control.md)、.NET ランタイムで使用できる新から継承されました。 これらは型の使用可能なだけではありません - 関数の場合もに使用できます。

* 必要に応じて非`public`型とメンバーに公開する必要があるまでです。 これには、どのようなコンシューマー結合するも最小限に抑えます。
* すべてのヘルパー機能を保持するよう努める`private`します。
* 使用を検討`[<AutoOpen>]`プライベート ヘルパー関数の場合、多数のモジュールにします。

## <a name="type-inference-and-generics"></a>型の推定とジェネリック

型の推定では、多数の定型入力を保存できます。 で自動ジェネリック化、F#コンパイラを使用して、ユーザー側でほとんどない余分な労力でより汎用的なコードを記述できます。 ただし、これらの機能は、優れた汎用的ではありません。

* パブリック Api での明示的な型の引数名のラベルを付けるし、この型の推定に依存しません。

    この理由は**する**API、コンパイラではないの形状のコントロールにする必要があります。 コンパイラは、の型の推論でジョブを正常に行うことができますは、依存内部の型が変更された場合は、API の変更の図形を含めることは可能です。 必要がありますが、下流のコンシューマーが、対処する必要があります、互換性に影響する API に変更がほぼ確実に発生します。 代わりに、パブリック API の形状を明示的に制御する場合は、これらの重大な変更を制御できます。 DDD の用語では、破損対策レイヤーとしてこの考えることができます。

* ジェネリック引数に意味のある名前を付けることを検討してください。

    特定のドメインに固有でない真に汎用のコードを記述する場合を除き、わかりやすい名前が他のプログラマで作業している、ドメインの理解に役立ちます。 たとえば、という名前の型パラメーター`'Document`ドキュメントとの対話のコンテキストでデータベースでわかりやすく、関数またはメンバーを使用する汎用的なドキュメントの種類を受け入れられることができます。

* PascalCase を持つジェネリック型パラメーターの名前を付けることを検討してください。

    これは、一般的なやり方では .NET では、ため snake_case またはキャメル ケースではなく、PascalCase を使用することをお勧めです。

最後に、自動ジェネリック化とは限りません F# や大規模なコードベースを初めて使用するユーザーにとってメリットがあります。 一般的なコンポーネントを使用して cognitive オーバーヘッドがあります。 さらに場合に、自動的にさまざまな入力の種類 (let そのために使用することは想定されている場合のみ)、汎用化された関数は使用されませんし、その時点でジェネリックを実際のメリットはありません。 常に記述するコードは汎用から利点が実際にかどうかに検討してください。

## <a name="performance"></a>パフォーマンス

F#値は変更不可で、既定値は、特定のクラス (特に、関係する同時実行と並列処理) のバグを回避することができます。 ただし、場合によっては、実行時間やメモリの割り当ての最適な (または妥当なでも) の効率を実現するために作業の範囲を最適な実装することによる状態の変化をインプレースします。 これが可能と F# でオプトイン単位で、`mutable`キーワード。

ただし、使用`mutable`F# で純粋性の機能に対応していない感じる可能性があります。 これは純粋性をからの期待を調整する場合は問題ありません。[参照の透過性](https://en.wikipedia.org/wiki/Referential_transparency)します。 参照の透過性のない純粋性 - は、F# の関数の記述する場合の最終目標です。 これにより、パフォーマンス クリティカルなコードの変異ベースの実装を上回る機能インターフェイスを記述することができます。

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>不変インターフェイスで変更可能なコードをラップします。

目標としてその参照の透過性とパフォーマンスが重要な機能の変更可能な大打撃を公開しないコードを記述するが重要です。 たとえば、次のコード実装、`Array.contains`関数の F# コア ライブラリ。

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

この関数を複数回呼び出すことで、基になる配列が変更されません。 またそれを利用することで、変更可能な状態を維持する必要。 コード内のほぼすべての行は、変異を使用していてがしいものに透過的です。

### <a name="consider-encapsulating-mutable-data-in-classes"></a>クラスの変更可能なデータをカプセル化することを検討してください。

前の例では、変更可能なデータを使用して操作をカプセル化するのに 1 つの関数を使用します。 複雑なデータ セットのための十分なこれとは限りません。 次の関数のセットを検討してください。

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

このコードは、パフォーマンスの高いですが、呼び出し元が保守を担当する変異ベースのデータ構造を公開します。 これは、基になるメンバーを変更することでクラスの内部でラップできます。

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table` 基になるデータ構造を維持するために呼び出し元を強制しません、基になる変異ベースのデータ構造をカプセル化します。 クラスは、データとは、呼び出し元の詳細を公開することがなく変異ベースのルーチンをカプセル化する強力な方法です。

### <a name="prefer-let-mutable-to-reference-cells"></a>必要に応じて`let mutable`セルを参照する

参照セルは、値そのものではなく、値への参照を表す方法です。 パフォーマンス クリティカルなコードを使用できますが、一般に、推奨されません。 次に例を示します。

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

参照セルの使用は、逆参照し、基になるデータを再度参照する必要があるすべての後続のコードを「汚染」。 代わりに、 `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

ラムダ式の途中で変化の 1 つのポイントとは別に他のすべてのコードを触れる`acc`、通常の使用状況と同じ方法で行うこと`let`-変更不可の値をバインドします。 これは、ため、時間の経過と共に変化しやすく、されます。

## <a name="object-programming"></a>オブジェクトのプログラミング

F#オブジェクトとオブジェクト指向 (OO) の概念を完全にサポートしています 多くのオブジェクト指向の概念には、強力で便利ですが、それらのすべては使用に最適です。 次の一覧は、高レベルのオブジェクト指向の機能のカテゴリのガイダンスを提供します。

**多くの状況でのこれらの機能の使用を検討してください。**

* ドット表記 (`x.Length`)
* インスタンス メンバー
* 暗黙的なコンス トラクター
* 静的メンバー
* インデクサー表記 (`arr.[x]`)
* 名前付きの省略可能な引数
* インターフェイスおよびインターフェイスの実装

**最初に、これらの機能に到達しないは慎重に適用して問題を解決する便利なとき。**

* メソッドのオーバーロード
* 変更可能なデータをカプセル化
* 型の演算子
* 自動プロパティ
* 実装する`IDisposable`と `IEnumerable`
* 型の拡張機能
* イベント
* 構造体
* デリゲート
* 列挙体

**それらを使用する必要がありますしない限り、これらの機能が一般に避けてください。**

* 型の継承に基づく階層と実装の継承
* Null 値と `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>継承より構成を優先します。

[継承より構成](https://en.wikipedia.org/wiki/Composition_over_inheritance)は、長期にわたる手法な F# コードが従うことができます。 基本的な原則は、する必要がありますいない基底クラスを公開機能を取得する基本クラスから継承するように呼び出し元を強制です。

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>オブジェクト式を使用してクラスを必要としない場合、インターフェイスを実装するには

[オブジェクト式](../language-reference/object-expressions.md)するクラスの内部で行う必要はありません値に実装されたインターフェイスをバインドをその場でインターフェイスを実装できるようにします。 これは、便利な場合に特にする_のみ_インターフェイスを実装し、完全なクラスの必要性があるないする必要があります。

たとえばで実行されるコードをここでは[ionide の概要](http://ionide.io/)を持っていないシンボルを追加した場合、コード修正アクションを提供する、`open`ステートメント。

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

Visual Studio Code の API と対話するときに、クラスの必要はありません、ため、オブジェクトの式は、この最適なツールです。 単体テスト、しのぎの方法でテスト ルーチンを持つインターフェイスをスタブする場合に役に立つもいます。

## <a name="type-abbreviations"></a>型略称

[省略形を入力](../language-reference/type-abbreviations.md)関数シグネチャ、またはより複雑な型などの別の型にラベルを割り当てるに便利です。 たとえば、次のエイリアスがそのと計算の定義に必要なものにラベルを割り当てます[CNTK](https://docs.microsoft.com/cognitive-toolkit/)、ディープ ラーニング ライブラリ。

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation`名がエイリアスがシグネチャと一致する任意の関数を示すために便利な方法です。 このような型の省略形を使用しては便利なより簡潔なコードができます。

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>ドメインを表す型の省略形は使用しないでください。

型の省略形は関数のシグネチャに名前を付ける場合に便利ですが、それらはわかりにくい他の種類を続けた場合。 この省略形を考慮してください。

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

これは、複数の方法で混乱を招くことができます。

* `BufferSize` 抽象化です。整数のもう 1 つの名前です。
* 場合`BufferSize`公開されるパブリック api では、そのことができます簡単に誤って解釈されるという意味では単に`int`します。 一般に、ドメインの種類に複数の属性し、などのプリミティブ型ではない`int`します。 この省略形には、仮定に違反しています。
* 大文字小文字の区別`BufferSize`(PascalCase) は、この型がより多くのデータを保持していることを意味します。
* このエイリアスは関数の名前付き引数を提供することと比較してわかりやすくを提供していません。
* コンパイルされた IL; で、省略形が明らかにはこれは整数だけと、このエイリアスは、コンパイル時の構成要素。

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

要約すると、型の省略形の落とし穴はある**いない**続けたは、型を抽象化します。 前の例では、`BufferSize`だけが、`int`実際には、追加データがないも内容だけでなく、型システムからのすべての特典`int`が既にします。
