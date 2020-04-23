---
title: F# コードのフォーマットに関するガイドライン
description: F# コードの書式設定に関するガイドラインを学習します。
ms.date: 11/04/2019
ms.openlocfilehash: dd48380a90ee92b2c1edaaabc116fa1cd8010390
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102490"
---
# <a name="f-code-formatting-guidelines"></a>F# コードのフォーマットに関するガイドライン

この記事では、F# コードが次のコードになるようにコードを書式設定する方法のガイドラインを示します。

* より読みやすい
* Visual Studio および他のエディターでツールを書式設定によって適用される規則に従って
* オンラインの他のコードと同様

これらのガイドラインは[、Anh-Dung Phan](https://github.com/dungpa)による[F# フォーマット規則の包括的なガイド](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)に基づいています。

## <a name="general-rules-for-indentation"></a>インデントの一般的な規則

F# では、既定で大きな空白を使用します。 以下のガイドラインは、この問題を両立させる方法についてのガイダンスを提供することを目的としています。

### <a name="using-spaces"></a>スペースの使用

インデントが必要な場合は、タブではなくスペースを使用する必要があります。 少なくとも 1 つのスペースが必要です。 組織では、インデントに使用するスペースの数を指定するコーディング標準を作成できます。インデントが発生する各レベルで、2、3、または 4 つのインデントのスペースが一般的です。

**インデントごとに 4 つのスペースを使用することをお勧めします。**

しかし、プログラムのインデントは主観的な問題です。 バリエーションは問題ありませんが、最初に従うべきルールは*インデントの一貫性です*。 一般的に受け入れられているインデントスタイルを選択し、コードベース全体で体系的に使用します。

## <a name="formatting-white-space"></a>空白の書式設定

F# は空白に依存します。 空白からのセマンティクスのほとんどは適切なインデントで覆われていますが、考慮すべき点がいくつかあります。

### <a name="formatting-operators-in-arithmetic-expressions"></a>算術式での演算子の書式設定

常に二項算術式の周囲に空白を使用します。

```fsharp
let subtractThenAdd x = x - 1 + 3
```

単項`-`演算子は、常に、否定する値の直後に置く必要があります。

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

演算子の後に空白文字を追加`-`すると、他のユーザーが混乱する可能性があります。

要約すると、常に重要です。

* 空白で二項演算子を囲む
* 単項演算子の後に末尾の空白文字が表示されない

二項算術演算子のガイドラインは特に重要です。 バイナリ`-`演算子を囲まなかった場合、特定の書式設定の選択肢と組み合わせると、それを単項`-`として解釈する可能性があります。

### <a name="surround-a-custom-operator-definition-with-white-space"></a>カスタム演算子定義を空白で囲む

オペレーター定義を囲むには、必ず空白を使用します。

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

で始まり、複数の`*`文字を持つカスタム演算子の場合、定義の先頭に空白を追加して、コンパイラのあいまいさを避ける必要があります。 このため、すべての演算子の定義を単一の空白文字で囲むだけですることをお勧めします。

### <a name="surround-function-parameter-arrows-with-white-space"></a>空白を使用して関数パラメーターの矢印を囲む

関数のシグネチャを定義する場合は、記号の周囲に空白`->`を使用します。

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>関数の引数を空白で囲む

関数を定義する場合は、各引数の前後に空白を使用します。

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a>長いメンバー定義の新しい行にパラメーターを配置する

メンバー定義が非常に長い場合は、新しい行にパラメーターを配置し、1 つのスコープをインデントします。

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

これは、コンストラクターにも適用されます。

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>注釈を入力する

#### <a name="right-pad-function-argument-type-annotations"></a>右パッド関数引数タイプの注釈

型の注釈を使用して引数を定義する場合は、記号`:`の後に空白を使用します。

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>空白で戻り値の型の注釈を囲む

let バインド関数または値型の注釈 (関数の場合は戻り値の型) では、記号の前後`:`に空白を使用します。

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>空白行の書式設定

* 最上位の関数とクラス定義を 2 行の空白行で区切ります。
* クラス内のメソッド定義は、1 行の空白行で区切られます。
* 関連する関数のグループを分けるために、余分な空白行を使用できます (控えめに)。 一連の関連するワンライナー (ダミー実装など) の間では、空白行を省略できます。
* 関数では、控えめに、論理セクションを示すために空白行を使用します。

## <a name="formatting-comments"></a>コメントの書式設定

一般的には、ML スタイルのブロック コメントよりも複数のダブルスラッシュコメントを好みます。

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

インラインコメントは、最初の文字を大文字にする必要があります。

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>名前付け規則

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>クラスバインド、式バインド、パターンバインド値および関数に対して camelCase を使用する

ローカル変数として、またはパターン一致と関数定義でバインドされているすべての名前に camelCase を使用することは、一般的で受け入れられている F# スタイルです。

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

クラス内のローカルバインド関数も camelCase を使用する必要があります。

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>モジュールバインドされたパブリック関数に camelCase を使用する

モジュールバインド関数がパブリック API の一部である場合は、camelCase を使用する必要があります。

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>内部およびプライベートモジュールバインド値および関数に camelCase を使用する

次のようなプライベート モジュールバインド値には、camelCase を使用します。

* スクリプト内のアドホック関数

* モジュールまたは型の内部実装を構成する値

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>パラメーターにキャメルケースを使用する

すべてのパラメータは.NETの命名規則に従って camelCase を使用する必要があります。

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>モジュールに PascalCase を使用する

すべてのモジュール (最上位、内部、プライベート、ネスト) は PascalCase を使用する必要があります。

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>型宣言、メンバー、およびラベルに PascalCase を使用する

クラス、インターフェイス、構造体、列挙体、デリゲート、レコード、および判別共用体は、すべて PascalCase で名前を付ける必要があります。 レコードおよび判別共用体の型およびラベル内のメンバーも、PascalCase を使用する必要があります。

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>NET に固有の構造に PascalCase を使用する

名前空間、例外、イベント、およびプロジェクト名`.dll`も PascalCase を使用する必要があります。 これにより、他の .NET 言語からの消費が消費者にとってより自然に感じられますが、.NET の名前付け規則と一致することもあります。

### <a name="avoid-underscores-in-names"></a>名前にアンダースコアを付けないようにする

歴史的に、一部の F# ライブラリは名前にアンダースコアを使用していました。 しかし、.NET の名前付け規則と競合しているため、これは広く受け入れられません。 しかし、一部の F# プログラマは、歴史的な理由の一部でアンダースコアを使用しており、寛容さと尊敬が重要です。 しかし、スタイルは、それを使用するかどうかの選択肢を持っている他の人によってしばしば嫌われていることに注意してください。

1 つの例外には、アンダースコアが一般的なネイティブ コンポーネントとの相互運用が含まれます。

### <a name="use-standard-f-operators"></a>標準 F# 演算子を使用する

次の演算子は、F# 標準ライブラリで定義されており、同等の演算子を定義する代わりに使用する必要があります。 コードを読みやすく慣用化する傾向にあるため、これらの演算子を使用することをお勧めします。 OCaml やその他の関数型プログラミング言語のバックグラウンドを持つ開発者は、さまざまなイディオムに慣れているかもしれません。 次の一覧は、推奨される F# 演算子をまとめたものです。

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>ジェネリックのプレフィックス構文 (`Foo<T>`) を優先して後置構文`T Foo`( ) に使用する

F# は、ジェネリック型の名前付けの後置 ML スタイル`int list`(たとえば) とプレフィックス .NET スタイル`list<int>`(たとえば) を継承します。 次の 5 種類の特定の種類を除き、.NET スタイルを優先します。

1. F# リストの場合は、後置形式`int list`ではなく`list<int>`、 を使用します。
2. F# オプションの場合は、後置形式`int option`ではなく`option<int>`、 を使用します。
3. F# 値オプションの場合は、後置形式`int voption`ではなく`voption<int>`、 を使用します。
4. F# 配列の場合は、 または`int[]``int array``array<int>`ではなく構文名を使用します。
5. [参照セル]`int ref`には、 `ref<int>` `Ref<int>`または ではなく を使用します。

その他のすべての型では、プレフィックス フォームを使用します。

## <a name="formatting-tuples"></a>タプルの書式設定

組のインスタンス化はかっこで囲み、その中の区切りコンマの後にはスペースを 1 つ`(1, 2)`入れる必要があります。 `(x, y, z)`

タプルのパターンマッチングでは、括弧を省略することが一般的に認められています。

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

また、関数の戻り値がタプルである場合は、括弧を省略することも一般的に受け入れられます。

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

要約すると、括弧で囲まれたタプルのインスタンス化を優先しますが、パターンマッチングや戻り値にタプルを使用する場合は、括弧を使用しないようにすると考えられます。

## <a name="formatting-discriminated-union-declarations"></a>判別共用体宣言のフォーマット

4`|`つのスペースで型定義をインデントします。

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a>判別共用体の書式設定

複数行に分割されたインスタンス化された判別共用体は、含まれるデータにインデントを伴う新しいスコープを与える必要があります。

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

閉じ括弧は新しい行にすることもできます。

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>レコード宣言の書式設定

型定義`{`で 4 つのスペースでインデントし、同じ行でフィールド リストを開始します。

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

レコードにインターフェイス実装またはメンバーを宣言する場合は、開始トークンを新しい行に配置し、終了トークンを新しい行に配置することをお勧めします。

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>レコードの書式設定

短いレコードは 1 行で書くことができます。

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

長いレコードは、ラベルに新しい行を使用する必要があります。

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

開始トークンを新しい行に配置し、コンテンツを 1 つのスコープにタブ付けし、新しい行に閉じるトークンを配置することをお勧めします。

* インデントスコープが異なるコード内でレコードを移動する
* 関数にパイピング

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

リスト要素と配列要素にも同じ規則が適用されます。

## <a name="formatting-copy-and-update-record-expressions"></a>コピーと更新のレコード式の書式設定

コピーと更新のレコード式はレコードであるため、同様のガイドラインが適用されます。

短い式は、1 行に収めることができます。

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

長い式では、新しい行を使用する必要があります。

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

また、レコード ガイダンスと同様に、かっこを個別に行に配置し、式で 1 つのスコープを右にインデントすることもできます。 かっこを使用せずにオプションで値をラップするなど、特殊なケースでは、次のように 1 行にかっこを使用する必要があります。

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a>リストと配列の書式設定

演算子`x :: l`の周囲にスペース`::`を入`::`れる (インフィックス演算子なので、スペースで囲まれた) を使用して書き込みます。

単一行で宣言されたリストと配列は、開始ブラケットの後、右括弧の前にスペースを置く必要があります。

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

2 つの異なる中かっこのような演算子の間には、常に少なくとも 1 つのスペースを使用してください。 たとえば、 と の`[`間にはスペースを`{`残します。

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

同じガイドラインが、タプルのリストまたは配列にも当てはまります。

複数の行に分割されたリストと配列は、レコードと同様の規則に従います。

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

レコードと同様に、最初と右の角かっこを独自の行に宣言すると、コードの移動や関数へのパイプ処理が簡単になります。

配列とリストをプログラムで生成する場合は`->`、`do ... yield`値が常に生成される場合よりも優先されます。

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

古いバージョンの F# 言語では`yield`、条件付きでデータが生成される場合や、評価する連続した式が存在する場合に指定する必要がありました。 古い F#`yield`言語バージョンでコンパイルする必要がある場合を除き、これらのキーワードを省略することをおすすめします。

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

場合によっては、`do...yield`読みやすさを助けるかもしれません。 主観的ではあるが、これらのケースは考慮すべきである。

## <a name="formatting-if-expressions"></a>式の場合の書式設定

条件のインデントは、条件を構成する式のサイズによって異なります。 が`cond``e1`短い`e2`場合は、1 行に書くだけです。

```fsharp
if cond then e1 else e2
```

または`cond``e2`より`e1`長いが複数行でない場合は、次の手順を実行します。

```fsharp
if cond
then e1
else e2
```

式のいずれかが複数行の場合:

```fsharp
if cond then
    e1
else
    e2
```

を使用して`elif`複数の`else`条件を設定し、同じスコープでインデント`if`します。

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>パターンマッチングコンストラクト

インデントを`|`指定しない一致の各句に a を使用します。 式が短い場合は、各部分式も単純である場合は、1 行を使用することを検討できます。

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

パターンマッチング矢印の右側の式が大きすぎる場合は、次の行に移動し、1 ステップインデントします`match`/`|`。

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

で始まる`function`匿名関数のパターンマッチングは、通常、インデントしすぎないようにします。 たとえば、次のように 1 つのスコープをインデントすると問題ありません。

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

で定義`let`された関数のパターンマッチング`let rec`は、 キーワードが使用されている場合`let``function`でも、 の開始後に 4 つのスペースをインデントする必要があります。

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

矢印の位置合わせはお勧めしません。

## <a name="formatting-trywith-expressions"></a>数式を使用して書式設定する

例外の種類でのパターンマッチングは、 と`with`同じレベルでインデントする必要があります。

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>書式設定機能パラメータアプリケーション

一般に、ほとんどの関数パラメーター・アプリケーションは同じ行で行われます。

新しい行の関数にパラメータを適用する場合は、1 つのスコープでインデントします。

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

ラムダ式には、関数の引数と同じガイドラインが適用されます。 ラムダ式の本体の場合、本体は、1 つのスコープでインデントされた別の行を持つことができます。

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

ただし、ラムダ式の本体が複数の行である場合は、複数行のコンストラクトを関数に単一の引数として適用するのではなく、別の関数に組み込みます。

### <a name="formatting-infix-operators"></a>インフィックス演算子の書式設定

演算子はスペースで区切ります。 この規則の明白な例外は`!`、`.`演算子と演算子です。

インフィックス式は、同じ列にラインナップしても問題があります。

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>パイプライン演算子の書式設定

パイプライン`|>`演算子は、操作する式の下に移動する必要があります。

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a>モジュールのフォーマット

ローカル モジュール内のコードはモジュールに対してインデントする必要がありますが、最上位モジュールのコードはインデントしないでください。 名前空間要素はインデントする必要はありません。

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a>オブジェクトの式とインターフェイスの書式設定

オブジェクト式とインタフェースは、4 つのスペースの後`member`にインデントされるのと同じように整列する必要があります。

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>式の空白の書式設定

F# 式では、余分な空白を避けてください。

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

名前付き引数にも、 を囲`=`むスペースを持たないようにする必要があります。

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>属性の書式設定

[属性](../language-reference/attributes.md)は、次の構成要素の上に配置されます。

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a>パラメータの属性の書式設定

属性は、パラメーターに配置することもできます。 この場合は、パラメータと同じ行に、名前の前に置きます。

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>複数の属性の書式設定

パラメータではないコンストラクトに複数の属性が適用される場合、行ごとに 1 つの属性が存在するように配置する必要があります。

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

パラメーターに適用する場合、それらは同じ行にあり、区切り記号で`;`区切られている必要があります。

## <a name="formatting-literals"></a>リテラルの書式設定

[属性を使用する F# リテラルは](../language-reference/literals.md)、属性を独自の行に配置し、PascalCase の名前付けを使用する必要があります。 `Literal`

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

属性を値と同じ行に配置しないでください。
