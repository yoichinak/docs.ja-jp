---
title: インターフェイス
description: 他のF#クラスが実装する関連メンバーのセットをインターフェイスが指定する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 8f054a668ad0fbc2453a45883e8052471280eca3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627650"
---
# <a name="interfaces"></a>インターフェイス

*インターフェイス*は、他のクラスが実装する関連メンバーのセットを指定します。

## <a name="syntax"></a>構文

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Remarks

インターフェイス宣言は、メンバーが実装されていないことを除いて、クラス宣言に似ています。 代わりに、キーワード`abstract`によって示されているように、すべてのメンバーが抽象型になります。 抽象メソッドにメソッド本体を指定することはできません。 ただし、 `default`キーワードと共にメンバーの別の定義をメソッドとして含めることで、既定の実装を提供することもできます。 これは、他の .NET 言語で基底クラスの仮想メソッドを作成することと同じです。 このような仮想メソッドは、インターフェイスを実装するクラスでオーバーライドできます。

インターフェイスの既定のアクセシビリティは`public`です。

各メソッドのパラメーターに通常の F# 構文を使用して名前を付けることができます必要に応じて。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

上`ISprintable`の例`Print`では、メソッドには、という名前`format`の`string`型の1つのパラメーターがあります。

インターフェイスを実装するには、オブジェクト式を使用する方法とクラス型を使用する方法の2つの方法があります。 どちらの場合も、クラス型またはオブジェクト式は、インターフェイスの抽象メソッドにメソッド本体を提供します。 実装は、インターフェイスを実装する各型に固有です。 したがって、異なる型のインターフェイスメソッドは相互に異なる場合があります。

簡易構文`interface`を`end`使用する場合、定義の開始と終了をマークするキーワードとは省略可能です。 これらのキーワードを使用しない場合、コンパイラは、使用するコンストラクトを分析することで、型がクラスであるかインターフェイスであるかを推論しようとします。 メンバーを定義する場合、または他のクラス構文を使用する場合、型はクラスとして解釈されます。

.NET のコーディングスタイルでは、すべてのインターフェイスを大文字`I`で開始します。

## <a name="implementing-interfaces-by-using-class-types"></a>クラス型を使用したインターフェイスの実装

次のコードに示すように、 `interface`キーワード、インターフェイスの名前、 `with`およびキーワードを使用して、クラス型に1つ以上のインターフェイスを実装することができます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

インターフェイスの実装は継承されるため、派生クラスはそれらを再実装する必要はありません。

## <a name="calling-interface-methods"></a>インターフェイスメソッドの呼び出し

インターフェイスメソッドを呼び出すことができるのは、インターフェイスを実装する型のオブジェクトではなく、インターフェイスのみです。 そのため、これらのメソッドを呼び出すに`:>` `upcast`は、演算子または演算子を使用して、インターフェイス型にアップキャストすることが必要になる場合があります。

型`SomeClass`のオブジェクトがある場合にインターフェイスメソッドを呼び出すには、次のコードに示すように、オブジェクトをインターフェイス型にアップキャストする必要があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

別の方法として、次の例のように、キャストしてインターフェイスメソッドを呼び出すオブジェクトに対してメソッドを宣言する方法があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>オブジェクト式を使用したインターフェイスの実装

オブジェクト式は、インターフェイスを実装するための簡単な方法を提供します。 これらは、名前付きの型を作成する必要がなく、インターフェイスメソッドをサポートするオブジェクトを必要とする場合に、追加のメソッドを使用しない場合に便利です。 オブジェクト式を次のコードに示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>インターフェイスの継承

インターフェイスは、1つまたは複数の基本インターフェイスから継承できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [オブジェクト式](object-expressions.md)
- [クラス](classes.md)
