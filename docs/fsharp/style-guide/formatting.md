---
title: F#コードの書式設定に関するガイドライン
description: 書式設定するためのガイドラインについて説明しますF#コード。
ms.date: 02/08/2019
ms.openlocfilehash: 0a72f96119181650837657afea6ca9d555ce9e5a
ms.sourcegitcommit: 8080271c246b57f4fb68c28369634bff46843424
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59553863"
---
# <a name="f-code-formatting-guidelines"></a>F#コードの書式設定に関するガイドライン

この記事では、F# コードが実行されるように、コードを書式設定する方法に関するガイドラインを提供します。

* 一般に読みやすくとして表示
* Visual Studio のツールとその他のエディターの書式設定が適用される規則に従って、します。
* その他のコードをオンラインに似ています

これらのガイドラインに基づいています[F# の書式設定規則に包括的なガイド](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)によって[Anh 協力 Phan](https://github.com/dungpa)します。

## <a name="general-rules-for-indentation"></a>インデントの一般的な規則

F#既定では、有意の空白を使用します。 次のガイドラインはこれをかけることがいくつかの課題を使い分ける方法についてのガイダンスを提供するためのものです。

### <a name="using-spaces"></a>スペースを使用します。

インデントが必要な場合は、スペース、タブではなくを使用する必要があります。 少なくとも 1 つの領域が必要です。 組織がインデントに使用する空白文字の数を指定するコーディング規則を作成できます。各レベルのインデントを設定するインデントの 2 つ、3 つまたは 4 つのスペースが一般的です。

**インデントあたり 4 つのスペースをお勧めします。**

ただし、プログラムのインデントは主観的な問題。 バリエーションが [ok] が最初の規則に従う必要がありますが、*インデントの一貫性*します。 インデントの一般的に受け入れられるスタイルを選択し、コードベース全体で体系的に使用します。

## <a name="formatting-white-space"></a>空白文字を書式設定

F#機密性の高い空白などです。 適切なインデントによってカバーされて空白からほとんどのセマンティクスは、その他の考慮事項があります。

### <a name="formatting-operators-in-arithmetic-expressions"></a>算術式の演算子を書式設定

二項演算式の周囲の空白を常に使用するには。

```fsharp
let subtractThenAdd x = x - 1 + 3
```

単項`-`が否定されますが、値が演算子の直後に。

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

後の空白文字を追加、`-`演算子は、他のユーザーの混乱を招くことができます。

要約すると、常に重要ですが。

* 空白文字で二項演算子のブロックの挿入
* 単項演算子の後に末尾の空白文字があることはありません。

二項算術演算子のガイドラインは、特に重要です。 バイナリ ブロックの挿入に失敗する`-`演算子、特定の書式設定が選択されている項目と組み合わせたときに、単項演算子として解釈する可能性があります`-`します。

### <a name="surround-a-custom-operator-definition-with-white-space"></a>空白文字でカスタム演算子の定義ブロックの挿入

常に演算子の定義を囲む空白を使用します。

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

始まる任意のカスタム演算子の`*`と 1 つ以上の文字を持つ、コンパイラのあいまいさを避けるために、定義の先頭に空白文字を追加する必要があります。 このため、単に 1 つの空白文字を持つすべての演算子の定義を囲むことをお勧めします。

### <a name="surround-function-parameter-arrows-with-white-space"></a>空白文字で関数パラメーターの矢印を囲む

関数のシグネチャを定義するときに、周囲の空白を使用して、`->`シンボル。

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a>空白行を書式設定

* 独立したトップレベル関数やクラスの定義 2 つの空白行を含む。
* クラス内でメソッドの定義は、単一の空白行で区切られます。
* 余分な空白行は、関連する関数のグループを区切る (控えめ) に使用する可能性があります。 一連の関連困ら (たとえば、ダミーの実装のセット) の間の空白行は省略できます。
* 論理的なセクションを示すために、関数では、空白行を使用します。

## <a name="formatting-comments"></a>コメントの書式設定

一般に ML スタイル ブロックのコメントを複数のコメントをダブル スラッシュを好みます。

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

インライン コメントは、最初の文字を大文字にする必要があります。

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>名前付け規則

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>キャメル ケースを使用して、クラス バインド、バインド式とパターン バインドの値と関数

一般的な camelCase を使用して、すべての名前を指定できる F# スタイルには、ローカル変数として、またはパターン マッチと関数定義がバインドされています。

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

クラスのローカルにバインドされた関数は、camelCase を使用してもする必要があります。

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>キャメル ケースを使用してバインド モジュールのパブリック関数

モジュール連結関数は、パブリック API の一部が、camelCase を使用します。

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>キャメル ケースを使用して、内部、プライベート モジュール連結値および関数

プライベート モジュール連結値は、次のようには、camelCase を使用します。

* スクリプトでアドホック関数

* モジュールまたは型の内部実装を作成する値

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>パラメーターにキャメル ケースを使用します。

すべてのパラメーターは、.NET の名前付け規則に従って、camelCase を使用してください。

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>PascalCase モジュールを使用します。

(最上位レベル、内部、プライベートの入れ子になった) のすべてのモジュールは PascalCase を使用する必要があります。

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>PascalCase を使用して、型宣言、メンバー、およびラベル

クラス、インターフェイス、構造体、列挙、デリゲート、レコード、および判別共用体がすべての名前は PascalCase です。 型およびレコード、判別共用体のラベル内のメンバーは、PascalCase を使用してもする必要があります。

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>PascalCase を使用して、.NET に固有の構成要素

名前空間、例外、イベント、およびプロジェクト/`.dll`名も PascalCase を使用します。 だけでなく、これにより、コンシューマーに自然に感じられる他の .NET 言語から消費も発生する可能性がある .NET の名前付け規則と一致します。

### <a name="avoid-underscores-in-names"></a>名前にアンダー スコアを回避します。

従来、一部の F# ライブラリは、名前にアンダー スコアを使用するが。 ただし、これが不要になった広く受け入れられて .NET の名前付け規則と衝突ためです。 ただし、F# プログラマによってアンダー スコアは使用頻度の高い、一部の歴史的な理由と許容範囲と点が重要です。 ただし、スタイルが使用するかどうかの選択肢を持つ他のユーザーによって多くの場合、我慢しなければならないこともあります。

いくつかの例外には、アンダー スコアが非常に一般的であるネイティブのコンポーネントとの相互運用が含まれています。

### <a name="use-standard-f-operators"></a>標準的な F# 演算子を使用します。

次の演算子は、F# の標準ライブラリで定義され、対応を定義する代わりに使用する必要があります。 読みやすく、慣用コードを作成する傾向が、これらの演算子の使用をお勧めします。 OCaml またはその他の関数型プログラミング言語の背景を持つ開発者は、さまざまな表現方法に慣れて可能性があります。 次の一覧は、推奨の F# 演算子をまとめたものです。

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>ジェネリックのプレフィックスの構文を使用して (`Foo<T>`) 方が優先的後置構文 (`T Foo`)

F#ジェネリック型の名前付けの両方、後置 ML スタイルを継承 (たとえば、 `int list`) .NET スタイルのプレフィックスと (たとえば、 `list<int>`)。 次の 4 つの特定の型を除く、.NET スタイルを優先するには。

1. F#後置形式を使用して、リスト、:`int list`なく`list<int>`します。
2. F#オプションを使用して、後置形式:`int option`なく`option<int>`します。
3. F#構文の名前を使用して、配列、`int[]`なく`int array`または`array<int>`します。
4. 参照セルを使用して`int ref`なく`ref<int>`または`Ref<int>`します。

他のすべての種類では、前置形式を使用します。

## <a name="formatting-tuples"></a>タプルの書式設定

タプル インスタンス化はかっこで囲まれた、する必要があり、内で使用する区切りコンマをたとえば、1 つのスペースで従う必要が: `(1, 2)`、`(x, y, z)`します。

タプルのパターン マッチングでは、かっこを省略することがよく受け入れられます。

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

タプルが関数の戻り値の場合は、かっこを省略することもよく受け入れられます。

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```
要約すると、かっこで囲まれたタプルのインスタンス化、必要に応じてをパターンに一致するか、戻り値のタプルを使用する場合と見なされるかっこを回避するために問題ありません。

## <a name="formatting-discriminated-union-declarations"></a>判別共用体の宣言の書式設定

インデント`|`によって 4 つのスペースの種類の定義。

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

複数行にわたって判別の共用体はインスタンス化されたはインデントで新しいスコープに含まれているデータを提供する必要があります。

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

新しい行の終わりかっこのこともできます。

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>レコードの宣言を書式設定

インデント`{`4 で定義型で空白し、同じ行にフィールド リストの先頭します。

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

開始トークンを配置する、新しい行で、新しい行に終了トークンは、レコードのメンバー、またはインターフェイスの実装を宣言する場合に推奨されます。

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>レコードを書式設定

1 行では、短いレコードを記述することができます。

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

長いレコードは、新しい行を使用して、ラベルの必要があります。

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

開始を配置して、タブ付きトークンを新しい行に、内容、1 つのスコープ、新しい行に終了トークンがいる場合に適しています。

* インデントの異なるスコープを使用したコード内でレコードを移動します。
* 関数にパイプすること

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

リストと配列の要素の場合と同じ規則が適用されます。

## <a name="formatting-copy-and-update-record-expressions"></a>レコードのコピーと更新の式を書式設定

レコードのコピーと更新式はまだ、レコードのようなガイドラインが適用されます。

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

として、レコードのガイダンスとすることも、中かっこの別々 の行を割り当てるし、式の右側に 1 つのスコープにインデントを設定します。 でかっこがない場合、オプションの値をラッピングなどのいくつかの特殊なケースでする必要があります 1 行に中かっこを保持することを確認してください。

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

## <a name="formatting-lists-and-arrays"></a>書式設定のリストと配列

書き込み`x :: l`の前後のスペースで、`::`演算子 (`::`が空白で囲まれたため、挿入演算子)。

リストと 1 つの行で宣言された配列は、角かっこと終わりかっこの前にスペースを入れる必要があります。

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

常に 2 つの個別の中かっこのような演算子の間に少なくとも 1 つの領域を使用します。 たとえば、間に空白のままに、`[`と`{`します。

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

リストまたは組の配列と同じガイドラインが適用されます。

リストと複数行にわたって配列は、同様のルール、レコードと同様に従います。

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

レコードと同様、独自の行の開始タグと終了の角かっこを宣言することは簡単に移動コードと関数にパイプします。

## <a name="formatting-if-expressions"></a>書式設定の if 式

条件文のインデントは、それらを構成する式のサイズによって異なります。 場合`cond`、`e1`と`e2`短く、単純に 1 行に書き込むには。

```fsharp
if cond then e1 else e2
```

いずれか`cond`、`e1`または`e2`は長くなりますが、複数行にありません。

```fsharp
if cond
then e1
else e2
```

複数行の式のいずれかの場合。

```fsharp
if cond then
    e1
else
    e2
```

複数の条件で`elif`と`else`と同じスコープでインデントは、 `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>パターン マッチング

使用して、`|`インデントなしの一致の各句。 式が短い場合は、各部分式が単純でもある場合は、1 行を使用を検討できます。

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

パターン マッチングの矢印の右側の式が大きすぎる場合は、次の行のインデントが設定された 1 つの手順に移動、 `match` /`|`します。

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

パターン マッチングして以降、匿名関数の`function`、遠すぎていないインデントする必要があります一般にします。 たとえば、次のように 1 つのスコープをインデントも可能です。

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

パターン マッチングで定義されている関数に`let`または`let rec`の開始後にインデントが設定された 4 つのスペースにする必要があります`let`場合でも、`function`キーワードの使用します。

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

矢印の整列はお勧めしません。

## <a name="formatting-trywith-expressions"></a>書式設定してみてください/式を

例外の種類に一致するパターンと同じレベルでインデントする`with`します。

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

## <a name="formatting-function-parameter-application"></a>関数パラメーターのアプリケーションを書式設定

一般に、関数パラメーターのほとんどのアプリケーションは、同じ行に行われます。

新しい行に関数にパラメーターを適用する場合は、1 つのスコープでインデントします。

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

関数の引数としてラムダ式と同じガイドラインが適用されます。 ラムダ式の本体の本文には別の行を設定できる場合は、1 つのスコープでインデント

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

ただし、ラムダ式の本体が 1 つ以上の行の場合は、別の関数にファクタリング アウトを検討してくださいではなく 1 つの引数として関数に適用される複数行の構築します。

### <a name="formatting-infix-operators"></a>挿入演算子を書式設定

スペースで別の演算子。 このルールの明確な例外は、`!`と`.`演算子。

挿入辞の式では、[ok] を同じ列に編成します。

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>パイプライン演算子を書式設定

パイプライン`|>`演算子は、上で動作する式の下に移動する必要があります。

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

### <a name="formatting-modules"></a>モジュールの書式設定

モジュールの基準としたローカル モジュール内のコードのインデントを設定する必要がありますが、最上位レベルのモジュール内のコードはインデントされませんする必要があります。 Namespace 要素は、インデントを設定するのにはありません。

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a>オブジェクトの式とインターフェイスの書式設定

同じ方法では、オブジェクトの式とインターフェイスを配置する必要があります`member`される 4 つのスペース後の分だけインデントされます。

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>式内の空白の書式設定

余分な空白文字を避けるためF#式。

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

名前付き引数も必要はありません領域を囲む、 `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>属性の書式設定

[属性](../language-reference/attributes.md)コンス トラクターを上に配置されます。

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

### <a name="formatting-attributes-on-parameters"></a>パラメーターに属性を書式設定

属性は、パラメーターの場所をこともできます。 ここでは、名の前に、パラメーターとして同じ行にし、配置します。

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>複数の属性を書式設定

パラメーターではないコンストラクトに適用されると、複数の属性は、1 行につき 1 つの属性が存在するようなに配置する必要があります。

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

同じ行に配置する必要がありで区切られた、パラメーターに適用するときに、`;`区切り記号。

## <a name="formatting-literals"></a>書式設定リテラル

[F#リテラル](../language-reference/literals.md)を使用して、`Literal`属性が独自の行に属性を配置し、camelCase 名前付けを使用する必要があります。

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

属性値と同じ行を配置しないでください。
