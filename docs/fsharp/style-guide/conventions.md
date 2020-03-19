---
title: F# のコーディング規則
description: F# コードを記述する際の一般的なガイドラインとイディオムについて説明します。
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401149"
---
# <a name="f-coding-conventions"></a>F# のコーディング規則

次の規則は、大きな F# コードベースでの作業経験から定式化されています。 [優れた F# コードの 5 つの原則](index.md#five-principles-of-good-f-code)は、各推奨事項の基礎です。 これらは[F# コンポーネントの設計ガイドライン](component-design-guidelines.md)に関連していますが、ライブラリなどのコンポーネントだけでなく、F# コードに適用できます。

## <a name="organizing-code"></a>コードの整理

F# では、コードを整理する主な方法として、モジュールと名前空間の 2 種類があります。 これらは似ていますが、次の違いがあります。

* 名前空間は .NET 名前空間としてコンパイルされます。 モジュールは静的クラスとしてコンパイルされます。
* 名前空間は常に最上位レベルです。 モジュールは最上位レベルにすることができ、他のモジュール内でネストできます。
* 名前空間は複数のファイルにまたがることができます。 モジュールはできません。
* モジュールはとで`[<RequireQualifiedAccess>]`飾ることができます. `[<AutoOpen>]`

次のガイドラインは、これらを使用してコードを整理するのに役立ちます。

### <a name="prefer-namespaces-at-the-top-level"></a>最上位レベルで名前空間を優先する

パブリックに使用できるコードの場合、名前空間は最上位レベルのモジュールよりも優先されます。 これらの名前空間は .NET 名前空間としてコンパイルされるため、C# からは問題なく使用できます。

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

トップレベルモジュールを使用すると、F# からのみ呼び出されたときには違いが見えないかもしれませんが、C# コンシューマーの場合、呼び出`MyClass`し元`MyCode`はモジュールで修飾する必要があると驚くかもしれません。

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>慎重に適用`[<AutoOpen>]`

この`[<AutoOpen>]`構造は、発信者が利用できるものの範囲を汚染する可能性があり、何かがどこから来ているかの答えは「魔法」です。 これは良いことではありません。 この規則の例外は、F# コア ライブラリ自体です (ただし、この事実も少し議論の余地があります)。

ただし、パブリック API とは別に整理するパブリック API のヘルパー機能がある場合は便利です。

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

これにより、ヘルパーを呼び出すたびに完全に修飾しなくても、関数のパブリック API から実装の詳細を明確に分離できます。

さらに、名前空間レベルで拡張メソッドと式ビルダーを公開することは、 で`[<AutoOpen>]`きちんと表現できます。

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>名前`[<RequireQualifiedAccess>]`が競合する可能性がある場合や、読みやすさを感じた場合に使用する

モジュールに`[<RequireQualifiedAccess>]`属性を追加すると、モジュールが開かれていないこと、およびモジュールの要素への参照が明示的に修飾されたアクセスを必要とすることを示します。 たとえば、モジュールには`Microsoft.FSharp.Collections.List`この属性があります。

これは、モジュール内の関数と値の名前が、他のモジュールの名前と競合する可能性がある場合に便利です。 適格なアクセスを要求すると、ライブラリの長期的な保守性と進化性が大幅に向上します。

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>トポロジ`open`的にステートメントを並べ替える

F# では、宣言の順序は、ステートメントを`open`含めて重要です。 これは、ファイル内のステートメントの`using`順序に依存しない`using static`、およびの効果が関係ない C# とは異なる。

F# では、スコープに開かれた要素は、既に存在する他の要素をシャドウできます。 つまり、ステートメントの並`open`べ替えによってコードの意味が変わる可能性があります。 その結果、すべての`open`ステートメントの任意の並べ替え (英数字など) は推奨されません。

代わりに、[トポロジ的](https://en.wikipedia.org/wiki/Topological_sorting)に並べ替えることをお勧めします。つまり、システムの`open`_層_が定義されている順序でステートメントを並べ替えます。 異なるトポロジー層内で英数字のソートを行うことも考慮されるかもしれません。

例として、F# コンパイラ サービスパブリック API ファイルのトポロジ並べ替えを次に示します。

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

改行はトポロジ レイヤーを分離し、各レイヤーは後で英数字でソートされることに注意してください。 これにより、誤ってシャドウする値を使用せずに、コードが整理されます。

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>副作用のある値をクラスに格納する

データベースやその他のリモート リソースにコンテキストをインスタンス化するなど、値の初期化に副作用が発生する場合が多くあります。 モジュール内でこのようなことを初期化し、後続の関数で使用するのは魅力的です。

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

これは、いくつかの理由からしばしば悪い考えです:

まず、 と を使用`dep1`して、アプリケーション構成が`dep2`コードベースにプッシュされます。 これは、大規模なコードベースでの維持が困難です。

第 2 に、静的に初期化されたデータには、コンポーネント自体が複数のスレッドを使用する場合にスレッド セーフではない値を含めないようにします。 これは明らかに. `dep3`

最後に、モジュールの初期化は、コンパイル単位全体の静的コンストラクターにコンパイルされます。 そのモジュールの let バインド値の初期化でエラーが発生した場合は、アプリケーションの`TypeInitializationException`有効期間全体をキャッシュするとしてマニフェストされます。 これは診断が難しい場合があります。 通常、推論しようとする内部例外がありますが、存在しない場合は、根本的な原因が何であるかを知りません。

代わりに、単純なクラスを使用して依存関係を保持するだけです。

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

これにより、次のことが可能になります。

1. API 自体の外部に依存状態をプッシュします。
2. 構成は API の外部で行えるようになりました。
3. 依存値の初期化のエラーは、 としては現れ`TypeInitializationException`ないでしょう。
4. API のテストが簡単になりました。

## <a name="error-management"></a>エラー管理

大規模なシステムでのエラー管理は複雑で微妙な努力であり、システムがフォールトトレラントでうまく動作することを保証する銀色の弾丸はありません。 次のガイドラインは、この困難な領域をナビゲートする際のガイダンスを提供する必要があります。

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>ドメイン固有の型でエラーケースと不正な状態を表す

[判別共用体](../language-reference/discriminated-unions.md)を使用すると、F# は、型システムでプログラムの状態に障害があることを表す機能を提供します。 次に例を示します。

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

この場合、銀行口座からのお金を引き出す方法が 3 つあると、失敗する可能性があります。 各エラーケースは型で表され、プログラム全体で安全に対処できます。

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

一般に、ドメイン内で何かが**失敗**する可能性のあるさまざまな方法をモデル化できる場合、エラー処理コードは通常のプログラムフローに加えて対処する必要があるものとして扱われなくなります。 これは単に通常のプログラムフローの一部であり、**例外的**とは考えられません。 これには、主に 2 つの利点があります。

1. ドメインが時間の経過とともに変化するため、保守が容易になります。
2. エラーケースは単体テストが簡単です。

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>エラーを型で表すことができない場合は例外を使用する

問題のあるドメインですべてのエラーを表すわけではありません。 このようなエラーは*本質的に例外的*であるため、F# で例外を発生およびキャッチする機能があります。

まず、「[例外設計ガイドライン](../../standard/design-guidelines/exceptions.md)」を読むことをお勧めします。 これらは F# にも適用できます。

例外を発生させる目的で F# で使用できる主な構成要素は、次の優先順位で考慮する必要があります。

| Function | 構文 | 目的 |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | 指定した引数`System.ArgumentNullException`名を持つ a を発生させます。 |
| `invalidArg` | `invalidArg "argumentName" "message"` | 引数名と`System.ArgumentException`メッセージを指定して a を発生させます。 |
| `invalidOp` | `invalidOp "message"` | 指定したメッセージ`System.InvalidOperationException`を持つ a を発生させます。 |
|`raise`| `raise (ExceptionType("message"))` | 例外をスローするための汎用メカニズム。 |
| `failwith` | `failwith "message"` | 指定したメッセージ`System.Exception`を持つ a を発生させます。 |
| `failwithf` | `failwithf "format string" argForFormatString` | フォーマット文字列とその`System.Exception`入力によって決定されるメッセージを持つ を発生させます。 |

を`nullArg``invalidArg`使用し`invalidOp`、スローするメカニズムとして`ArgumentNullException`、`ArgumentException`必要`InvalidOperationException`に応じてを使用します。

と`failwith``failwithf`関数は、特定の例外ではなく基本`Exception`型を発生させるため、一般的には避けるべきです。 [例外設計ガイドライン](../../standard/design-guidelines/exceptions.md)に従って、可能な場合は、より具体的な例外を発生させる必要があります。

### <a name="using-exception-handling-syntax"></a>例外処理構文の使用

F# は、次の`try...with`構文を使用して例外パターンをサポートします。

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

コードをクリーンに保ちたいなら、パターンマッチングを使用して例外に直面して実行する機能を調整するのは少し難しいかもしれません。 これを処理する方法の 1 つは、エラーケースを囲む機能を例外自体にグループ化する手段として[アクティブパターン](../language-reference/active-patterns.md)を使用することです。 たとえば、例外をスローしたときに、例外メタデータに貴重な情報を含む API を使用している場合があります。 アクティブ パターン内でキャプチャされた例外の本体で有用な値をラップ解除し、その値を返すと、状況によっては役立ちます。

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>例外を置き換えるためにモナディックエラー処理を使用しない

関数型プログラミングでは、例外はややタブーと見なされます。 実際、例外は純度に違反するため、機能していないと考えても安全です。 ただし、これはコードが実行される場所の現実を無視し、ランタイム エラーが発生する可能性があります。 一般に、ほとんどのものが純粋でもトータルでもないという前提でコードを書いて、不愉快な驚きを最小限に抑えます。

.NET ランタイムおよび言語間のエコシステム全体における関連性と妥当性に関して、次の主な長所と側面を考慮することが重要です。

1. 問題をデバッグする際に非常に役立つ詳細な診断情報が含まれています。
2. ランタイムや他の .NET 言語ではよく理解されています。
3. 例外を回避するために例外を*回避*するコードと比較すると、意味の一部をアドホックベースで実装することで、重要な定型文を削減できます。

この3番目のポイントは非常に重要です。 複雑でない操作では、例外を使用しないと、次のような構造体が処理される可能性があります。

```fsharp
Result<Result<MyType, string>, string list>
```

これは簡単に「文字列型付き」エラーでパターンマッチングのような脆弱なコードにつながる可能性があります。

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

さらに、"より素敵な" 型を返す "単純な" 関数の欲求の例外を飲み込むのは魅力的です。

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

残念`tryReadAllText`ながら、ファイル システムで発生する可能性のある無数の処理に基づいて多数の例外をスローする可能性があり、このコードは、実際に環境で問題が発生している可能性のある情報を破棄します。 このコードを結果の型に置き換える場合は、"文字列型" エラー メッセージの解析に戻ります。

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

さらに、`Error`例外オブジェクト自体をコンストラクタに配置すると、関数ではなく呼び出しサイトで例外の種類を適切に処理する必要があります。 これを効果的に行うと、API の呼び出し元として扱うのも楽しくない、チェックされた例外が効果的に作成されます。

上記の例の代わりに、*特定*の例外をキャッチし、その例外のコンテキストで意味のある値を返す方法があります。 関数を`tryReadAllText`次のように変更すると、`None`より多くの意味があります。

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

catch-all として機能する代わりに、この関数はファイルが見つからなかった場合を適切に処理し、その意味を戻りに割り当てます。 この戻り値は、コンテキスト情報を破棄したり、コードのその時点で関係のないケースを呼び出し元に強制したりしながら、そのエラーケースにマップできます。

たとえば`Result<'Success, 'Error>`、入れ子になっていない基本的な操作に適した型や、F# のオプション型は、*何かが何かを*返す可能性がある場合と*何も返さない*場合に表現するのに最適です。 ただし、例外の代わりとなるものではありません。 むしろ、例外およびエラー管理ポリシーの特定の側面に対して、対象を絞った方法で対応するために、慎重に適用する必要があります。

## <a name="partial-application-and-point-free-programming"></a>部分的なアプリケーションとポイントフリープログラミング

F# は部分的なアプリケーションをサポートしているため、ポイントフリー のスタイルでプログラミングするさまざまな方法がサポートされます。 これは、モジュール内でコードを再利用したり、何かの実装を行う場合に役立ちますが、公開するものではありません。 一般に、ポイントフリープログラミングはそれ自体の美徳ではなく、スタイルに没頭していない人々にとって重要な認知障壁を追加することができます。

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>パブリック API で部分的なアプリケーションとカリー化を使用しない

例外を除いて、パブリック API で部分的なアプリケーションを使用すると、コンシューマーにとって混乱を招く可能性があります。 通常、F#`let`コードの -バインド値は**値**であり、**関数値**ではありません。 値と関数値を混在させると、特に関数を構成するなどの演算子と組み合わせる場合、認知オーバーヘッドのかなりの部分と引き換えに、少数`>>`のコード行を節約できます。

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>ポイントフリープログラミングに対するツールの影響を考慮する

カリー化関数は、引数にラベルを付けないでください。 これは、ツールに影響を与えます。 次の 2 つの関数を検討してください。

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

どちらも有効な関数ですが`funcWithApplication`、カリー化された関数です。 エディタでタイプにカーソルを合わせると、次のことがわかります。

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

呼び出しサイトでは、Visual Studio などのツールのツールヒントは、入力型と`string``int`入力型が実際に何を表すのか、意味のある情報を提供しません。

そのような`funcWithApplication`ポイントフリーコードが一般に消耗品である場合は、ツールが引数の意味のある名前を拾うことができるように、完全なη拡張を行うことをお勧めします。

さらに、ポイントフリーコードのデバッグは、不可能ではないにしても困難な場合があります。 デバッグ ツールは、名前にバインドされた値 (`let`たとえば、バインディング) に依存するため、中間値を実行の途中で検査できます。 コードに検査する値がない場合、デバッグする必要はありません。 将来、デバッグ ツールは、以前に実行されたパスに基づいてこれらの値を合成するように進化する可能性がありますが、*潜在的な*デバッグ機能に対する賭けをヘッジすることはお勧めします。

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>内部定型法を削減する手法として部分的なアプリケーションを検討する

前の点とは対照的に、部分アプリケーションはアプリケーション内部または API のより深い内部の定型を減らすための素晴らしいツールです。 これは、多くの場合、定型文が対処する苦痛である、より複雑なAPIの実装を単体テストするのに役立ちます。 たとえば、次のコードは、このようなフレームワークに外部依存関係を持たずに、関連する別注 API を学習することなく、ほとんどのモック フレームワークが提供する内容を実現する方法を示しています。

たとえば、次のソリューションの地形を考えてみましょう。

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`次のようなコードを公開する可能性があります。

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

での`Transactions.doTransaction``ImplementationLogic.Tests.fsproj`単体テストは簡単です:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

モック コンテキスト`doTransaction`オブジェクトを使用して部分的に適用すると、モック コンテキストを毎回構築する必要なく、すべての単体テストで関数を呼び出すことができます。

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

この手法は、コードベース全体に対して汎用的に適用されるべきではありませんが、複雑な内部とそれらの内部を単体テストする際の定型化を減らすには良い方法です。

## <a name="access-control"></a>アクセス制御

F# には、.NET ランタイムで使用できるオプションから継承された[アクセス制御](../language-reference/access-control.md)の複数のオプションがあります。 これらは型に対して使用できるだけでなく、関数にも使用できます。

* 非型と`public`メンバーをパブリックに消耗品にする必要があるまで、非型とメンバーを優先します。 これにより、消費者のカップルが何を組み合わせるかを最小限に抑えることができます。
* すべてのヘルパー機能`private`を維持するよう努める 。
* ヘルパー関数が多数`[<AutoOpen>]`になる場合は、プライベートモジュールでの使用を検討してください。

## <a name="type-inference-and-generics"></a>型の推論とジェネリック

型の推論により、多くの定型文を入力する手間を省くことができます。 また、F# コンパイラの自動汎化は、追加の作業をほとんど行わなく、より汎用的なコードを記述するのに役立ちます。 しかし、これらの機能は普遍的に良いものではありません。

* パブリック API では明示的な型を持つ引数名にラベルを付け、この型の推論に依存しないようにします。

    この理由**は、コンパイラ**ではなく、API の形状を制御する必要があるためです。 コンパイラは、型を推論する際に細かい処理を行うことができますが、依存している内部が型を変更した場合、API の形状を変更することができます。 これはあなたが望むものかもしれませんが、下流の消費者が対処しなければならない画期的なAPI変更をもたらす可能性はほぼ間違いいます。 代わりに、パブリック API の形状を明示的に制御する場合は、これらの変更を制御できます。 DDD の用語では、これは腐敗防止レイヤーと考えることができます。

* 汎用引数に意味のある名前を付けることを検討してください。

    特定のドメインに固有ではない本当に汎用的なコードを記述していない限り、意味のある名前を付けて、他のプログラマが自分が作業しているドメインを理解するのに役立ちます。 たとえば、ドキュメント データベースとの`'Document`対話のコンテキストで名前が付けられた型パラメーターは、汎用ドキュメント型が、使用している関数またはメンバーによって受け入れられることを明確にします。

* PascalCase を使用してジェネリック型パラメーターの名前を付けることを検討してください。

    これは .NET で行う一般的な方法なので、snake_caseやキャメルケースではなく、PascalCase を使用することをお勧めします。

最後に、自動汎化は、F# や大規模なコードベースを使い始めた人にとっては、必ずしも恩恵であるとは限りません。 汎用的なコンポーネントを使用する場合には、認知的オーバーヘッドがあります。 さらに、自動汎用化関数が異なる入力タイプで使用されない場合(もちろん、それらがそのように使用される予定であれば)、その時点でジェネリックであることには本当の利点はありません。 作成するコードが実際にジェネリックであることからメリットがあるかどうかを常に考慮してください。

## <a name="performance"></a>パフォーマンス

### <a name="prefer-structs-for-small-data-types"></a>小さなデータ型の構造体を優先する

構造体 (Value Types とも呼ばれる) を使用すると、通常はオブジェクトの割り当てを回避するため、一部のコードのパフォーマンスが向上する場合があります。 ただし、構造体は常に "高速" ボタンとは限りません: 構造体内のデータのサイズが 16 バイトを超える場合、データをコピーすると、参照型を使用するよりも多くの CPU 時間が消費される場合があります。

構造体を使用する必要があるかどうかを判断するには、次の条件を考慮してください。

- データのサイズが 16 バイト以下の場合。
- これらのデータ型の多くが実行中のプログラムのメモリに常駐している可能性がある場合。

最初の条件が当てはまる場合は、通常は構造体を使用する必要があります。 両方を適用する場合は、ほとんどの場合、構造体を使用する必要があります。 前の条件が当てはまる場合もありますが、構造体の使用は参照型を使用するよりも良くも悪くもありませんが、まれに発生する可能性があります。 しかし、このような変更を行うときは常に測定し、仮定や直感に基づいて動作しないことが重要です。

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>小さな値型をグループ化する場合は構造体の組を優先する

次の 2 つの関数を検討してください。

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

[BenchmarkDotNet](https://benchmarkdotnet.org/)のような統計的ベンチマークツールを使用してこれらの関数をベンチマークすると、構造体の組を使用`runWithStructTuple`する関数は 40% 高速でメモリを割り当てません。

ただし、これらの結果は、必ずしも独自のコードに当てはまるとは限りません。 関数を`inline`としてマークすると、参照タプルを使用するコードに追加の最適化が行われるか、割り当てるコードを簡単に最適化できます。 パフォーマンスが懸念される場合は常に結果を測定し、仮定や直感に基づいて決して動作しないでください。

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>データ型が小さい場合は構造体レコードを優先する

前述の経験則は、 [F# レコードの種類](../language-reference/records.md)にも当てはまる。 それらを処理する次のデータ型と関数を検討してください。

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

これは前のタプルコードと似ていますが、今回の例ではレコードとインライン内部関数を使用しています。

[BenchmarkDotNet](https://benchmarkdotnet.org/)のような統計的ベンチマークツールを使用してこれらの関数をベンチマークすると、60%`processStructPoint`近く高速に実行され、マネージ ヒープに何も割り当てられていないことがわかります。

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>データ型が小さい場合は、構造体の判別共用体を優先する

構造体の組とレコードを使用したパフォーマンスに関する以前の観測は[、F# 判別共用体にも当てはめます](../language-reference/discriminated-unions.md)。 次のコードについて考えてみましょう。

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

ドメイン モデリングでは、単一ケースの判別共用体を次のように定義するのが一般的です。 [BenchmarkDotNet](https://benchmarkdotnet.org/)のような統計的ベンチマークツールを使用してこれらの関数をベンチマークすると、小さな文字列よりも`structReverseName``reverseName`約 25% 高速に実行されることがわかります。 大きな文字列の場合、どちらも同じ動作をします。 したがって、この場合は、構造体を使用することが常に望ましいです。 前述したように、常に測定し、仮定や直感に基づいて動作しません。

前の例では、構造体の判別共用体の方がパフォーマンスが向上することが示されましたが、ドメインをモデル化する際に、より大きな判別共用体を持つことは一般的です。 そのような大きなデータ型は、より多くのコピーが必要になる可能性があるため、構造体の場合は、その操作によってはうまく機能しない場合があります。

### <a name="functional-programming-and-mutation"></a>関数型プログラミングと変異

F# 値は既定で変更不可であり、特定のクラスのバグ (特に同時実行と並列処理を伴うバグ) を回避できます。 しかし、特定の場合において、実行時間またはメモリ割り当ての最適な(あるいは合理的な)効率を達成するために、作業のスパンは、インプレース状態の突然変異を使用して最適に実装することができる。 これは、キーワードを使用して F# を使用したオ`mutable`プトインベースで可能です。

F#`mutable`での使用は、機能的な純度と対立する可能性があります。 これは理解できますが、機能純度はどこでもパフォーマンス目標と対立する可能性があります。 妥協点は、呼び出し元が関数を呼び出したときに何が起こるかを気にする必要がないように、変異をカプセル化することです。 これにより、パフォーマンスに重要なコードの変異ベースの実装を介して機能インターフェイスを記述できます。

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>変更できないインターフェイスでの変更可能なコードのラップ

参照の透明性を目標として使用する場合、パフォーマンスに重要な関数の変更可能な下腹を公開しないコードを記述することが重要です。 たとえば、次のコードは、F#`Array.contains`コア ライブラリに関数を実装します。

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

この関数を複数回呼び出しても、基になる配列は変更されず、また、それを使用する際に変更可能な状態を維持する必要もありません。 これは、その中のほとんどすべてのコード行がミューテーションを使用しているにもかかわらず、参照的に透過的です。

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>クラスに変更可能なデータをカプセル化することを検討してください

前の例では、1 つの関数を使用して、変更可能なデータを使用して操作をカプセル化しました。 複雑なデータセットでは、この方法で十分ではありません。 次の関数のセットを検討してください。

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

このコードはパフォーマンスが高いが、呼び出し元が管理する必要がある、変更に基づくデータ構造を公開します。 これは、変更できる基になるメンバーがないクラスの内部でラップできます。

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table`は、基になる変異ベースのデータ構造をカプセル化するため、呼び出し元が基になるデータ構造を維持することを強制しません。 クラスは、呼び出し元に詳細を公開せずに、変更に基づくデータとルーチンをカプセル化する強力な方法です。

#### <a name="prefer-let-mutable-to-reference-cells"></a>参照`let mutable`セルを優先する

参照セルは、値自体ではなく、値への参照を表す方法です。 パフォーマンスに重要なコードに使用できますが、推奨されません。 次の例を確認してください。

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

参照セルの使用は、基礎となるデータを逆参照して再参照する必要がある、後続のすべてのコードを「汚染」するようになりました。 代わりに、`let mutable`次の点を考慮してください。

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

ラムダ式の途中での単一の変異点を除いて、タッチ`acc`する他のすべてのコードは、通常`let`バインドされた不変値の使用法と変わらない方法で行うことができます。 これにより、時間の経過と同時に変更が容易になります。

## <a name="object-programming"></a>オブジェクトプログラミング

F# は、オブジェクトとオブジェクト指向 (OO) の概念を完全にサポートしています。 多くの OO 概念は強力で便利ですが、すべての概念が使用に適しているわけではありません。 以下のリストは、OO 機能のカテゴリに関する概要を示しています。

**これらの機能は、多くの状況で使用することを検討してください。**

* ドット表記 (`x.Length`)
* インスタンス メンバー
* 暗黙的コンストラクター
* 静的メンバー
* インデクサー表記`arr.[x]`( )
* 名前付き引数とオプション引数
* インターフェイスとインターフェイスの実装

**最初にこれらの機能に手を伸ばさないでくださいが、問題を解決するのに便利なときに慎重に適用してください。**

* メソッドのオーバーロード
* カプセル化された変更可能データ
* 型の演算子
* 自動プロパティ
* 実装`IDisposable`と`IEnumerable`
* 型の拡張機能
* events
* 構造体
* デリゲート
* 列挙型

**通常、これらの機能は、次の機能を使用する必要がない限り、使用しないでください。**

* 継承ベースの型階層と実装の継承
* ヌルと`Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>継承よりもコンポジションを優先する

[継承に対する合成](https://en.wikipedia.org/wiki/Composition_over_inheritance)は、優れた F# コードが従うことができる長年の慣用句です。 基本原則は、基本クラスを公開せず、機能を取得するために呼び出し元にその基本クラスから継承させる必要があります。

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>クラスが必要ない場合は、オブジェクト式を使用してインターフェイスを実装する

[オブジェクト式](../language-reference/object-expressions.md)を使用すると、インターフェイスを実行時に実装し、実装されたインターフェイスをクラス内で行う必要なく値にバインドできます。 これは、特にインターフェイスを実装する必要_があり_、フル クラスを必要としない場合に便利です。

たとえば、次のコードは、`open`ステートメントがないシンボルを追加した場合にコード修正アクションを提供するために[Ionide](http://ionide.io/)で実行されます。

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

Visual Studio コード API を操作する際にクラスを使用する必要がないため、オブジェクト式はこれに最適なツールです。 また、テスト ルーチンを使用するインターフェイスをアドホックにスタブアウトする場合は、単体テストにも役立ちます。

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>署名を短くする型の省略形を考慮する

[型省略形](../language-reference/type-abbreviations.md)は、関数シグネチャや複雑な型など、別の型にラベルを割り当てるのに便利な方法です。 たとえば、次のエイリアスは、ディープ ラーニング ライブラリである[CNTK](https://docs.microsoft.com/cognitive-toolkit/)で計算を定義するために必要な情報にラベルを割り当てます。

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

この`Computation`名前は、エイリアス化しているシグネチャに一致する関数を表す便利な方法です。 このような型の略語を使用すると便利で、より簡潔なコードが可能になります。

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>ドメインを表す型の省略形を使用しないようにする

型の省略形は関数シグネチャに名前を付ける場合に便利ですが、他の型を省略すると混乱する可能性があります。 次の省略形を考えてみましょう。

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

これは、複数の方法で混乱を招く可能性があります。

* `BufferSize`は抽象化ではありません。これは整数の別の名前にすぎません。
* パブリック`BufferSize`API で公開されている場合、単なる`int`意味以上の意味を持つ可能性が簡単に誤って解釈される可能性があります。 一般に、ドメイン型には複数の属性があり、 のような`int`プリミティブ型ではありません。 この省略形は、その仮定に違反します。
* (PascalCase) の`BufferSize`大文字と小文字は、この型がより多くのデータを保持することを意味します。
* このエイリアスは、関数に名前付き引数を指定する場合と比較して、明確性を高めるものではありません。
* 省略形はコンパイルされた IL では現われません。これは単なる整数であり、このエイリアスはコンパイル時の構成要素です。

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

要約すると、型の省略形の落とし穴は、それらが省略型の型に対する抽象化**ではない**ということです。 前の例では、`BufferSize`追加のデータ`int`がなく、すでに持っているもの`int`以外にも型システムからの利点を持たない、ただのカバーの下にあります。

型の省略形を使用してドメインを表す方法として、単一ケースの判別共用体を使用する方法があります。 前のサンプルは次のようにモデリングできます。

```fsharp
type BufferSize = BufferSize of int
```

の値と基になる値の観点から`BufferSize`動作するコードを記述する場合は、任意の整数を渡すのではなく、1 つを構築する必要があります。

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

これにより、呼び出し元が関数を呼び出`send`す前に値をラップする型`BufferSize`を構築する必要があるため、関数に誤って任意の整数を渡す可能性が低くなります。
