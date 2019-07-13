---
title: 匿名のレコード
description: コンストラクトを使用して、データの操作に役立つ言語機能、匿名のレコードを使用する方法について説明します。
ms.date: 06/12/2019
ms.openlocfilehash: e576210d4fb76ccfd09f8feb157ef4542aa94ccf
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041806"
---
# <a name="anonymous-records"></a>匿名のレコード

匿名のレコードは、単純な集計の名前付きの値を使用する前に宣言する必要はありません。 構造体、または参照型として宣言できます。 既定では参照型です。

## <a name="syntax"></a>構文

次の例では、匿名のレコードの構文を示します。 項目の区切りとして`[item]`は省略可能です。

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>基本的な使用方法

匿名のレコードが最適なとして考えるF#レコードの種類をインスタンス化する前に宣言する必要はありません。

たとえば、ここで、関数とやり取りする方法が生成されます匿名のレコード。

```fsharp

open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

次の例の展開では、前に、`printCircleStats`匿名のレコードの入力として受け取る関数。

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

呼び出す`printCircleStats`匿名のレコード種類の入力の型はコンパイルに失敗すると、同じ「形状」がないとします。

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>構造体の匿名のレコード

匿名のレコードは、構造体で、オプションとして定義することも`struct`キーワード。 構造体の匿名のレコードの作成と、前の例を次の例には。

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a>Structness の推論

構造体の匿名のレコードについても、「structness の推定」を指定する必要がない場所、`struct`呼び出しサイトにキーワードを指定します。 Elide するこの例で、`struct`キーワードを呼び出すときに`printCircleStats`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

逆のパターンで指定する`struct`入力の型が構造体の匿名レコードの場合にコンパイルに失敗します。

## <a name="embedding-anonymous-records-within-other-types"></a>その他の種類内の匿名のレコードの埋め込み

宣言すると便利な[判別共用体](discriminated-unions.md)がの場合はレコード。 レコード内のデータが判別共用体と同じ型の場合は、相互に再帰すべての種類を定義する必要があります。 匿名のレコードを使用してこの制限を回避できます。 例は、次に上にあるパターンと一致する型と関数。

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a>コピーして、式の更新

匿名のレコードでの構築をサポートする[コピーして、式を更新](copy-and-update-record-expressions.md)します。 たとえば、ここでは、1 つの既存のコピーを匿名のレコードの新しいインスタンスを作成する方法のデータ。

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

ただし、名前付きのレコードとは異なり匿名のレコード、コピーではまったく別のフォームを構築し、式を更新できます。 次の例は、前の例から同じ匿名レコードを受け取り、新しい匿名のレコードに展開すること。

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

名前付きのレコードのインスタンスからの匿名のレコードを作成することもします。

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

参照と構造体の匿名のレコードとの間データをコピーすることもできます。

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a>匿名のレコードのプロパティ

匿名のレコードでは、さまざまな使用方法を完全に理解に不可欠な特性があります。

### <a name="anonymous-records-are-nominal"></a>匿名のレコードが標準

匿名のレコードが[標準型](https://en.wikipedia.org/wiki/Nominal_type_system)します。 という名前とは考えて[レコード](records.md)事前宣言を必要としない種類 (これは、公称も)。

匿名のレコードの 2 つの宣言は次の例を検討してください。

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x`と`y`値が異なる型であるし、は相互に互換性がありません。 等値性が解除され、同等ではありません。 これを示すためには、名前付きのレコードを同等検討してください。

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

型と同等のグループまたは比較に関連しているときに、対応する名前付きのレコードと比較した場合、匿名のレコードに関する本質的に異なるものはないです。

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>匿名のレコードを使用して、構造的等値と比較

レコードの種類と同様に匿名のレコードは、構造的等値性と比較します。 これは、すべての構成要素の型をサポートして等値と比較のようなレコードの種類の場合は true のみ。 等値または比較をサポートするには、2 つの匿名のレコードは、同じ「形状」する必要があります。

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>匿名のレコードはシリアル化

名前付きのレコードを含む場合と同様、匿名のレコードをシリアル化することができます。 例を次に示しますを使用して[Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

匿名のレコードは、シリアル化または逆シリアル化型を事前にドメインを定義することがなく、ネットワーク経由で軽量のデータを送信するために便利です。

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>匿名のレコードとの相互運用C#匿名型

使用を必要とする .NET API を使用することは[C#匿名型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)します。 C#匿名型は匿名のレコードを使用して相互に簡単です。 次の例では、匿名のレコードを使用して呼び出す方法を示しています、 [LINQ](../../csharp/programming-guide/concepts/linq/index.md)オーバー ロードを匿名型を必要とします。

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

さまざまな .NET 全体で使用される匿名型を渡すことの使用を要求する他の Api があります。 匿名のレコードは、それらを操作するためのツールです。

## <a name="limitations"></a>制限事項

匿名のレコードでは、その使用方法にいくつかの制限があります。 設計、本質的なものが、他のユーザーは結果セットのサイズを変更します。

### <a name="limitations-with-pattern-matching"></a>パターン マッチングの制限事項

匿名のレコードは、名前付きのレコードとは異なり、パターン マッチングをサポートしていません。 次の 3 つの理由があります。

1. パターンは、すべてのフィールドの名前付きのレコードの種類とは異なり、匿名のレコードを考慮する必要があります。 匿名のレコードは構造型のサブタイプをサポートしていません: 標準型があるためにです。
2. ため (1) はありません、パターン一致式でその他のパターンを指定する機能をそれぞれ個別のパターンは匿名の異なるレコードの種類を示すようにします。
3. (3) のため、匿名のレコード パターンは「ドット」表記の使用よりも詳細になります。

オープン言語提案がある[コンテキストが限定でパターン マッチングを許可する](https://github.com/fsharp/fslang-suggestions/issues/713)します。

### <a name="limitations-with-mutability"></a>可変性の制約

現時点で匿名のレコードを定義することは`mutable`データ。 [言語の修正候補を開く](https://github.com/fsharp/fslang-suggestions/issues/732)変更可能なデータを許可します。

### <a name="limitations-with-struct-anonymous-records"></a>構造体の匿名のレコードの制限事項

匿名のレコードを構造体を宣言することはできません`IsByRefLike`または`IsReadOnly`します。 [言語の修正候補を開く](https://github.com/fsharp/fslang-suggestions/issues/712)の`IsByRefLike`と`IsReadOnly`匿名のレコード。
