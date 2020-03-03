---
title: パターン マッチ
description: でF#パターンを使用して、データを論理構造と比較したり、データを構成要素に分解したり、データから情報を抽出したりする方法について説明します。
ms.date: 10/27/2019
ms.openlocfilehash: 1acb795cbe5581898ae5e1439098f906a8a16b93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041010"
---
# <a name="pattern-matching"></a>パターン マッチ

パターンは、入力データの変換規則です。 データを論理構造と比較したり、データを構成要素に分解したり、さまざまな方法でデータから情報を抽出したりするために、F# 言語全体で使用されます。

## <a name="remarks"></a>Remarks

パターンは、`match` 式などの多くの言語構成要素で使用されます。 `let` 束縛、ラムダ式、および `try...with` 式に関連付けられている例外ハンドラーで関数の引数を処理する場合に使用されます。 詳細については、「 [Match 式](match-expressions.md)、 [let 束縛](./functions/let-bindings.md)、[ラムダ式: `fun` キーワード](./functions/lambda-expressions-the-fun-keyword.md)」、および「[例外: `try...with` 式](./exception-handling/the-try-with-expression.md)」を参照してください。

たとえば、`match` 式では、*パターン*はパイプ記号の後になります。

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

各パターンは、なんらかの方法で入力を変換する際の規則として機能します。 `match` 式では、各パターンが順に調べられ、入力データにパターンとの互換性があるかどうかが確認されます。 一致が見つかった場合は、結果の式が実行されます。 一致が見つからなかった場合は、次のパターン規則がテストされます。 *条件*部分が[一致式](match-expressions.md)で説明されている場合は、省略可能です。

サポートされているパターンを次の表に示します。 実行時に、表に示されている順序で次の各パターンに対して入力がテストされます。パターンは、コードに示されているとおりに先頭から末尾へ、各行のパターンの左から右へ、再帰的に適用されます。

|名|説明|例|
|----|-----------|-------|
|定数パターン|数値、文字、リテラル文字列、列挙定数、または定義済みのリテラル識別子|`1.0`, `"test"`, `30`, `Color.Red`|
|識別子パターン|判別共用体のケース値、例外ラベル、またはアクティブ パターンのケース|`Some(x)`<br /><br />`Failure(msg)`|
|変数パターン|*identifier*|`a`|
|`as` パターン|*識別子*としての*パターン*|`(a, b) as tuple1`|
|OR パターン|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|AND パターン|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Cons パターン|*識別子*::*リスト-識別子*|`h :: t`|
|リスト パターン|[ *pattern_1*;...;*pattern_n* ]|`[ a; b; c ]`|
|配列パターン|[&#124; *pattern_1*;..;*pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|かっこで囲まれたパターン|(*パターン*)|`( a )`|
|タプル パターン|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|レコード パターン|{ *identifier1* = *pattern_1*;...;*identifier_n* = *pattern_n* }|`{ Name = name; }`|
|ワイルドカード パターン|_|`_`|
|型の注釈が指定されたパターン|*pattern* :*型*|`a : int`|
|型テスト パターン|:? *型*[as*識別子*]|`:? System.DateTime as dt`|
|null パターン|null|`null`|

## <a name="constant-patterns"></a>定数パターン

定数パターンは、数値、文字、リテラル文字列、列挙定数 (列挙型名が含まれる) です。 定数パターンのみが含まれる `match` 式は、他の言語の case ステートメントと比較できます。 入力がリテラル値と比較され、値が等しい場合にはパターンが一致します。 リテラルの型に、入力の型との互換性があることが必要です。

リテラル パターンの使用例を次に示します。変数パターンと OR パターンも使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

リテラル パターンにはこの他に、列挙定数に基づくパターンもあります。 列挙定数を使用するときは、列挙型名を指定する必要があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>識別子パターン

パターンが有効な識別子になる文字列の場合は、識別子の形式でパターンの照合方法が決まります。 識別子が 2 文字以上で、大文字で始まる場合は、コンパイラが識別子パターンとの照合を試みます。 このパターンの識別子は、Literal 属性が指定された値、判別共用体のケース、例外識別子、またはアクティブ パターンのケースです。 一致する識別子が見つからない場合は、照合が失敗し、次のパターン規則の変数パターンが入力と比較されます。

判別共用体パターンは、単純な名前付きケースであるか、値またはタプル (複数の値を含む) を含むかのいずれかです。 値が存在する場合は、値の識別子を指定する必要があります。 タプルの場合は、タプルの各要素の識別子、または 1 つ以上の名前付きの共用体フィールドのフィールド名の識別子、を持つタプル パターンを指定する必要があります。 例については、このセクションのコード例を参照してください。

`option` 型は、`Some` と `None` の 2 つのケースを持つ判別共用体です。 一方のケース (`Some`) には値が含まれますが、もう一方のケース (`None`) は単なる名前付きケースです。 したがって、`Some` には、`Some` ケースに関連付けられた値の変数が必要ですが、`None` は単体で使用する必要があります。 次のコードでは、`var1` 変数に、`Some` ケースとの照合で取得された値が指定されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

次の例では、`PersonName` 判別共用体に、名前に使用できる形式を表す文字列および文字が混在しています。 判別共用体のケースは `FirstOnly`、`LastOnly`、および `FirstLast` です。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

名前付きフィールドがある判別共用体の場合、名前付きフィールドの値を抽出するために等号 (=) を使用します。 たとえば、次のような宣言を持つ判別共用体について検討します。

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

次のようにパターン一致式の中で名前付きフィールドを使用できます。

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

前の例では、名前付きフィールドの使用は省略可能であり、したがって、`Circle(r)` と `Circle(radius = r)` は同じ結果になります。

複数のフィールドを指定する場合は、区切り記号としてセミコロン (;) を使用します。

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

アクティブ パターンを使用すると、より複雑なカスタム パターン マッチを定義できます。 アクティブパターンの詳細については、「[アクティブパターン](active-patterns.md)」を参照してください。

識別子が例外であるケースは、例外ハンドラーのコンテキストのパターン マッチで使用されます。 例外処理でのパターンマッチングの詳細については、「[例外: `try...with` 式](./exception-handling/the-try-with-expression.md)」を参照してください。

## <a name="variable-patterns"></a>変数パターン

変数パターンでは、照合される値が変数名に割り当てられ、その変数名を、`->` 記号の右側の実行式で使用できるようになります。 変数パターン単体はどの入力にも一致しますが、多くの場合、変数パターンはその他のパターン内で使用されます。このため、タプルや配列などのより複雑な構造体を変数に分解することが可能になります。

タプル パターン内で変数パターンを使用する例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>as パターン

`as` パターンは、`as` 句が追加されたパターンです。 `as` 句は、照合する値を `match` 式の実行式で使用できる名前に束縛します。または、このパターンが `let` 束縛で使用される場合は、名前が束縛としてローカル スコープに追加されます。

`as` パターンの使用例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>OR パターン

OR パターンは、入力データが複数のパターンと一致する場合に、同じコードを結果として実行するときに使用します。 OR パターンの両側の型に互換性があることが必要です。

OR パターンの使用例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>AND パターン

AND パターンでは、入力が 2 つのパターンと一致する必要があります。 AND パターンの両側の型に互換性があることが必要です。

次の例は、このトピックで後述する「[組パターン](https://msdn.microsoft.com/library/#tuple)」で示した `detectZeroTuple` に似ていますが、ここでは `var1` と `var2` の両方を and パターンを使用して値として取得します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Cons パターン

欠点パターンは、リストを最初の要素、*先頭*、および残りの要素 (*末尾*) を含むリストに分解するために使用されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>リスト パターン

リスト パターンでは、リストをいくつかの要素に分解できます。 リスト パターン自体は、特定の数の要素を含むリストとだけ一致します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>配列パターン

配列パターンはリスト パターンに似ており、特定の長さの配列を分解するために使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>かっこで囲まれたパターン

かっこでパターンを囲んで、目的の結合規則を得ることができます。 次の例では、かっこを使用して、AND パターンと Cons パターンの間の結合規則を制御します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>タプル パターン

タプル パターンはタプル形式の入力と一致します。このパターンでは、タプル内の位置ごとにパターン マッチ変数を使用して、タプルを構成要素に分解できます。

タプル パターンの使用例を次に示します。リテラル パターン、変数パターン、およびワイルドカード パターンも使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>レコード パターン

レコード パターンは、レコードを分解してフィールドの値を抽出するために使用されます。 パターンがレコードのすべてのフィールドを参照する必要はありません。省略されたフィールドは照合に使用されないため、抽出されません。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>ワイルドカード パターン

ワイルドカード パターンは、アンダースコア (`_`) 文字で表され、変数パターンと同様にどの入力にも一致しますが、入力が変数に割り当てられるのではなく、破棄される点が異なります。 多くの場合、ワイルドカード パターンは、その他のパターン内で `->` 記号の右側の式で不要な値のプレースホルダーとして使用されます。 また、一致しなかった入力に対応するために、パターン リストの最後にワイルドカード パターンが使用されることもよくあります。 ワイルドカード パターンは、このトピックの多くのコード例で示されています。 一例として、上記のコードを参照してください。

## <a name="patterns-that-have-type-annotations"></a>型の注釈が付けられたパターン

パターンには型の注釈を付けることができます。 このコメントはその他の型の注釈と同様に動作し、その他の型の注釈と同様に推論を導きます。 パターンの型の注釈はかっこで囲む必要があります。 型の注釈が付けられたパターンを次のコードに示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>型テスト パターン

型テスト パターンは、入力を型と照合するために使用されます。 入力型がパターンで指定された型と一致する場合、またはその型の派生型である場合は、一致と見なされます。

型テスト パターンの使用例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

識別子が特定の派生型であるかどうかを確認するだけの場合は、次の例に示すように、パターンの `as identifier` 部分は必要ありません。

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a>null パターン

null パターンは null 値と一致します。null 値は、null 値を許可する型を使用しているときに示される可能性があります。 Null パターンは、.NET Framework コードと相互運用する場合によく使用されます。 たとえば、.NET API の戻り値が `match` 式への入力である場合が考えられます。 プログラム フローは、戻り値が null であるかどうかと、戻り値のその他の特性に基づいて制御できます。 null パターンを使用すると、null 値が残りのプログラムに反映されるのを防ぐことができます。

null パターンと変数パターンの使用例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>関連項目

- [match 式](match-expressions.md)
- [アクティブ パターン](active-patterns.md)
- [F# 言語リファレンス](index.md)
