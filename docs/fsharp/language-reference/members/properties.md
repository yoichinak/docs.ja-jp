---
title: プロパティ
description: オブジェクトに関連付けられている値を表すメンバーである F# プロパティ、について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: bf605ee1135bd3b3561bde9a8ae66353497931b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666366"
---
# <a name="properties"></a>プロパティ

*プロパティ*オブジェクトに関連付けられている値を表すメンバーします。

## <a name="syntax"></a>構文

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>Remarks

プロパティは、"が、"オブジェクト指向プログラミング、オブジェクト インスタンスにして、または型の静的プロパティに関連付けられているデータを表すリレーションシップ。

プロパティに、(バッキング ストアとも呼ばれます) の基になる値を明示的に指定するかどうか、またはのバッキング ストアを自動的に生成するコンパイラを許可したいかどうかに応じて、2 つの方法でプロパティを宣言できます。 通常、プロパティが値または変数の単純なラッパーにすぎませんプロパティに、自明でない実装がある場合より明確な方法、および自動の方法を使用する必要があります。 プロパティを明示的に宣言するには、使用、`member`キーワード。 この宣言型構文を指定する構文の後に、`get`と`set`もという名前のメソッド*アクセサー*します。 読み取り/書き込み、書き込み専用、読み取り専用プロパティでは、さまざまな形式で「構文」セクションに示すように、明示的な構文が使用されます。 読み取り専用のプロパティを定義するのみ、`get`メソッドです。 書き込み専用のプロパティの定義のみ、`set`メソッド。 プロパティは、両方を持つ場合は注意`get`と`set`アクセサー、別の構文を使用する属性とは、次のコードのように、アクセサーごとに異なるアクセシビリティ修飾子を指定します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

読み取り/書き込みプロパティは、両方があるため、`get`と`set`メソッドの順序`get`と`set`元に戻すことができます。 構文を指定する代わりに、`get`のみの構文と`set`結合構文を使用する代わりにのみです。 これを行う簡単にコメント アウト個人`get`または`set`メソッドでは、これは行う必要がある可能性があります。 結合の構文を使用するには、この方法は、次のコードに表示されます。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

プライベート値のプロパティのデータと呼びます保留が*バッキング ストア*します。 コンパイラでバッキング ストアを自動的に作成するには、キーワードを使用して`member val`、自己の識別子を省略し、プロパティを初期化する式を指定します。 プロパティを変更可能である場合は、含める`with get, set`します。 たとえば、次のクラス型には、自動的に実装された 2 つのプロパティが含まれています。 `Property1` 読み取り専用であり、プライマリ コンス トラクターに渡される引数に初期化されますと`Property2`は空の文字列に初期化され設定可能なプロパティです。

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

自動実装プロパティにと同じように他のメンバー定義の前に含める必要があるために、型の初期化の一環`let`バインドと`do`型定義内のバインディング。 初期化時に、プロパティがアクセスされるたびにしないと、自動的に実装されたプロパティを初期化する式がのみ評価されることに注意してください。 この動作では、明示的に実装されたプロパティの動作とは対照的です。 この実質的に意味はこれらのプロパティを初期化するコードは、クラスのコンス トラクターに追加されます。 この違いを示しています。 次のコードを検討してください。

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**出力**

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

AutoProperty の値変更されていないことと、繰り返し呼び出したときに、ExplicitProperty 変更のたびに呼び出されますが、上記のコードの出力を示しています。 これを示します、自動的に実装されたプロパティの式では、毎回は評価されませんは明示的なプロパティの getter メソッドです。

>[!WARNING]
>Entity Framework などのいくつかのライブラリがあります (`System.Data.Entity`) 自動的に実装されたプロパティの初期化とうまく連携する基本クラス コンス トラクターでカスタム操作を実行します。 その場合、明示的なプロパティを使用してみてください。

プロパティは、クラス、構造体、判別共用体、レコード、インターフェイス、および拡張機能の型のメンバーであることができ、オブジェクトの式で定義することもできます。

属性は、プロパティに適用できます。 プロパティに属性を適用するには、プロパティの前に別の行に属性を記述します。 詳細については、「[属性](../attributes.md)」を参照してください。

既定では、プロパティはパブリックです。 アクセシビリティ修飾子は、プロパティにも適用できます。 アクセシビリティ修飾子を適用する場合は追加、プロパティの名前の直前に両方に適用するものです、`get`と`set`メソッドです追加する前に、`get`と`set`異なるアクセシビリティがある場合、キーワード。各アクセサーが必要です。 *アクセシビリティ修飾子*、次のいずれかを指定できます: `public`、 `private`、`internal`します。 詳細については、「[Access Control](../access-control.md)」(アクセス制御) を参照してください。

プロパティの実装は、プロパティがアクセスされるたびに実行されます。

## <a name="static-and-instance-properties"></a>静的およびインスタンスのプロパティ

プロパティは、静的またはインスタンスのプロパティ。 静的なプロパティは、インスタンスを指定しないで呼び出すことができ、個々 のオブジェクトではなく、種類に関連付けられた値に使用されます。 静的プロパティは、自己識別子を省略します。 自己識別子は、インスタンスのプロパティに必要です。

次の静的プロパティの定義は静的フィールドがあるシナリオに基づいて`myStaticValue`プロパティのバッキング ストアは。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

プロパティもできる配列に似た、呼び出された場合*インデックス付きプロパティ*します。 詳細については、次を参照してください。[インデックス付きプロパティ](indexed-properties.md)します。

## <a name="type-annotation-for-properties"></a>プロパティの型の注釈

多くの場合、コンパイラは、バッキング ストアの種類のプロパティの型を推論するのに十分な情報が、型の注釈を追加することで、型を明示的に設定することができます。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Set アクセサーのプロパティを使用します。

提供するプロパティを設定する`set`アクセサーを使用して、`<-`演算子。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

出力は**20**します。

## <a name="abstract-properties"></a>抽象プロパティ

プロパティは、抽象にすることができます。 メソッドと同様`abstract`プロパティに関連付けられた仮想ディスパッチがあることを意味します。 抽象プロパティは、同じクラスの定義のないは、本当に抽象することができます。 このようなプロパティを含むクラスは、抽象クラスではそのためです。 代わりに、抽象はだけことを意味は仮想関数、プロパティをその場合は、定義が同じクラス内にある必要があります。 抽象プロパティをプライベートにすることはできませんし、1 つのアクセサーが抽象の場合は、他の必要がありますも抽象にすることに注意してください。 抽象クラスの詳細については、次を参照してください。[抽象クラス](../abstract-classes.md)します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>関連項目

- [メンバー](index.md)
- [メソッド](methods.md)
