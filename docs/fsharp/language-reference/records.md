---
title: レコード
description: 学習方法F#レコードはオプションでメンバーの名前付きの値の単純な集計を表します。
ms.date: 05/16/2016
ms.openlocfilehash: a499755383654ddaf76af12776ee93f27834b7b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795422"
---
# <a name="records"></a>レコード

レコードは、名前付きの値の単純な集合を表しており、オプションでメンバーを含みます。  以降でF#4.1、構造体または参照型になることができますか。  これが、既定では参照型です。

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

前の構文で*typename*レコードの種類の名前を指定*label1*と*label2*と呼ばれる値の名前は*ラベル*、*type1*と*type2*これらの値の種類を示します。 *メンバー リスト*省略可能な型のメンバーの一覧を示します。  使用することができます、`[<Struct>]`参照型であるレコードではなく、構造体のレコードを作成する属性。

いくつかの例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

各ラベルは、個別の行には、セミコロンを省略できます。

値を設定するには式と呼ばれるで*式を記録*します。 コンパイラでは、(ラベルが十分に区別されるその他のレコードの種類の場合) を使用するラベルから型を推測します。 中かっこ ({}) は、レコードの式を囲みます。 次のコードはラベルが付いた 3 つの浮動要素を持つレコードを初期化するレコード式`x`、`y`と`z`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

同じラベルも別の型がある場合は、短縮形を使用しないでください。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

最後に宣言された型のラベルの以前に宣言された型よりも優先で、前の例では、`mypoint3D`推論されます`Point3D`します。 次のコードのように、レコードの種類を明示的に指定することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

クラス型と同様、レコードの種類のメソッドを定義することができます。

## <a name="creating-records-by-using-record-expressions"></a>レコード式を使用してレコードを作成します。

レコードはレコードで定義されているラベルを使用して初期化できます。 これを行う式として参照されます、*記録式*します。 レコード式を囲むし、区切り記号としてセミコロンを使用するには、中かっこを使用します。

次の例では、レコードを作成する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

レコード式には、型定義では、最後のフィールドの後のセミコロンは、1 つの行ですべてのフィールドがあるかどうかに関係なく、省略可能です。

レコードを作成するときに各フィールドの値を指定する必要があります。 任意のフィールドの初期化式では、他のフィールドの値を参照することはできません。

次のコードの種類で`myRecord2`フィールドの名前から推測されます。 必要に応じて、型名を明示的に指定できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

レコード構築の別の形式は、既存のレコードをコピーし、フィールドの値の一部を変更したりするときに役に立ちます。 次のコード行を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

レコード式のこのフォームと呼ばれる、*コピーして更新するレコード式*。

レコードは既定では変更できません。ただし、コピーと更新の式を使用して簡単に変更されたレコードを作成することができます。 変更可能なフィールドを明示的に指定できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

レコードのフィールドでは、DefaultValue 属性を使用しないでください。 既定値に初期化されるフィールドを持つレコードの既定のインスタンスの定義、およびコピーを使用して、既定値と異なる任意のフィールドを設定する式をレコードを更新にことをお勧めします。

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

## <a name="creating-mutually-recursive-records"></a>相互に再帰的なレコードを作成します。

レコードを作成するときにいずれかの時点に後で定義するには別の型に依存する可能性があります。 これは、再帰的に相互にレコードの種類を定義する場合を除き、コンパイル エラーです。

相互に再帰的なレコードを定義するのには、`and`キーワード。 これにより 2 つまたは複数のレコードの種類をまとめてリンクできます。

たとえば、次のコードの定義、`Person`と`Address`相互に再帰の種類。

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
    PostCode: string }
```

せず、前の例を定義した場合、`and`キーワード、その後はコンパイルされません。 `and`キーワードが相互に再帰的な定義に必要です。

## <a name="pattern-matching-with-records"></a>レコードを使用したパターン マッチ

レコードは、パターン マッチングで使用できます。 一部のフィールドを明示的に指定し、一致が発生したときに割り当てられる他のフィールドの変数を指定できます。 これを次のコード例に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

このコードの出力は次のとおりです。

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>レコードとクラス間の違い

レコード フィールドは、プロパティとして自動的に公開されているし、それらが作成時に使用され、レコードのコピーで、クラスとは異なります。 レコードの作成は、クラスの構築からも異なります。 レコードの種類では、コンス トラクターを定義できません。 代わりに、このトピックで説明した構築の構文が適用されます。 クラスは、コンス トラクターのパラメーター、フィールド、およびプロパティ間の直接の関係のあるありません。

共用体と構造体の型と同様には、レコードは、構造的等値セマンティクスを持ちます。 クラスの参照がある等値セマンティクスです。 次のコード例はこの処理方法を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

このコードの出力は次のとおりです。

```
The records are equal.
```

クラスと同じコードを記述する場合、2 つのクラスのオブジェクトが等しくならない 2 つの値は、ヒープ上の 2 つのオブジェクトを表しますであり、アドレスだけが比較 (クラス型のオーバーライドしない限り、`System.Object.Equals`メソッド)。

レコードの等価性を参照する必要がある場合、属性を追加`[<ReferenceEquality>]`レコード上。

## <a name="see-also"></a>関連項目

- [F# の型](fsharp-types.md)
- [クラス](classes.md)
- [F# 言語リファレンス](index.md)
- [参照の等価性](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [パターン一致](pattern-matching.md)
