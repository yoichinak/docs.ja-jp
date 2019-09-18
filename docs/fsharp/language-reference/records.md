---
title: レコード
description: レコードがF#名前付きの値の単純な集計を表す方法について説明します。メンバーを使用することもできます。
ms.date: 06/09/2019
ms.openlocfilehash: 1ba002407b1ccbcbceed32df8636fb860e89e3b6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053940"
---
# <a name="records"></a>レコード

レコードは、名前付きの値の単純な集合を表しており、オプションでメンバーを含みます。 構造体と参照型のどちらでもかまいません。  既定では、これらは参照型です。

## <a name="syntax"></a>構文

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a>Remarks

前の構文では、 *typename*はレコード型の名前、 *label1*と*label2*は*ラベル*と*呼ばれる値*の名前、 *type1 と type1*はこれらの値の型です。 *メンバーリスト*は、型のメンバーの省略可能なリストです。  属性を使用し`[<Struct>]`て、参照型であるレコードではなく、構造体レコードを作成できます。

次に例をいくつか示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

各ラベルが個別の行にある場合、セミコロンは省略可能です。

*レコード式*と呼ばれる式に値を設定できます。 コンパイラは、使用されているラベルから型を推測します (ラベルが他のレコードの種類とは十分に異なる場合)。 中かっこ ({}) は、レコード式を囲みます。 次のコードは、 `x` `y`とと`z`いうラベルを持つ3つの float 要素を持つレコードを初期化するレコード式を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

同じラベルを持つ別の型が存在する可能性がある場合は、短縮形を使用しないでください。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

最後に宣言された型のラベルは、以前に宣言された型よりも`mypoint3D` `Point3D`優先されます。したがって、前の例では、はと推論されます。 レコードの種類は、次のコードのように明示的に指定できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

メソッドは、クラス型の場合と同様に、レコード型に対して定義できます。

## <a name="creating-records-by-using-record-expressions"></a>レコード式を使用したレコードの作成

レコードで定義されているラベルを使用して、レコードを初期化できます。 これを行う式は、*レコード式*と呼ばれます。 中かっこを使用してレコード式を囲み、セミコロンを区切り記号として使用します。

次の例では、レコードを作成する方法を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

レコード式の最後のフィールドの後のセミコロン、および型定義では、フィールドがすべて1行にあるかどうかにかかわらず、省略可能です。

レコードを作成するときは、各フィールドに値を指定する必要があります。 任意のフィールドについて、初期化式の他のフィールドの値を参照することはできません。

次のコードでは、の`myRecord2`型はフィールドの名前から推論されます。 必要に応じて、型名を明示的に指定できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

別の形式のレコードの構築は、既存のレコードをコピーする必要があり、フィールド値の一部を変更する必要がある場合に便利です。 次のコード行はこれを示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

この形式のレコード式は、レコードの*コピーと更新の式*と呼ばれます。

既定では、レコードは変更できません。ただし、コピーと更新の式を使用して、変更されたレコードを簡単に作成できます。 また、変更可能なフィールドを明示的に指定することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

レコードフィールドで DefaultValue 属性を使用しないでください。 より適切な方法は、既定値に初期化されるフィールドを持つレコードの既定のインスタンスを定義し、コピーと更新のレコード式を使用して、既定値とは異なるフィールドを設定することです。

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a>相互再帰的なレコードの作成

レコードを作成するときに、後で定義する別の型に依存するように設定することもできます。 レコードの種類が相互に再帰的に定義されている場合を除き、コンパイルエラーになります。

同時に再帰的なレコードを定義`and`するには、キーワードを使用します。 これにより、2つ以上のレコードの種類をリンクすることができます。

たとえば、次のコードでは、 `Person`と`Address`型が相互に再帰的に定義されています。

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string
    Occupant: Person }
```

`and`キーワードを使用せずに前の例を定義すると、コンパイルされません。 相互再帰的な定義にはキーワードが必要です。`and`

## <a name="pattern-matching-with-records"></a>レコードを使用したパターンマッチ

レコードは、パターンマッチングで使用できます。 一部のフィールドを明示的に指定し、一致が発生したときに割り当てられる他のフィールドの変数を指定できます。 これを次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

このコードの出力は次のようになります。

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>レコードとクラスの違い

レコードフィールドは、プロパティとして自動的に公開され、レコードの作成とコピーに使用されるという点でクラスとは異なります。 レコードの構築も、クラスの構築とは異なります。 レコード型では、コンストラクターを定義することはできません。 代わりに、このトピックで説明する構築構文が適用されます。 クラスには、コンストラクターのパラメーター、フィールド、およびプロパティの間に直接的な関係はありません。

Union 型や structure 型と同様に、レコードには構造的等価性のセマンティクスがあります。 クラスには参照等値セマンティクスがあります。 次のコード例はこの処理方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

このコードの出力は次のとおりです。

```
The records are equal.
```

クラスを使用して同じコードを記述した場合、2つのクラスオブジェクトは等しくなります。これは、2つの値がヒープ上の2つのオブジェクトを表し、 `System.Object.Equals`アドレスのみが比較されるためです (クラス型がメソッドをオーバーライドする場合を除きます)。

レコードの参照の等価性が必要な場合は`[<ReferenceEquality>]` 、レコードの上に属性を追加します。

## <a name="see-also"></a>関連項目

- [F# の型](fsharp-types.md)
- [クラス](classes.md)
- [F# 言語リファレンス](index.md)
- [参照-等値](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [パターン一致](pattern-matching.md)
