---
title: インターフェイス
description: 学習方法F#インターフェイスは、他のクラスを実装する関連するメンバーのセットを指定します。
ms.date: 05/16/2016
ms.openlocfilehash: 5b57769af6c05b83b3a112635033abf4efaca772
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645369"
---
# <a name="interfaces"></a>インターフェイス

*インターフェイス*他のクラスを実装する関連するメンバーのセットを指定します。

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

インターフェイスの宣言ではメンバーが実装されていないがクラス宣言に似ています。 代わりに、すべてのメンバーが抽象クラスで、キーワードで示されている`abstract`します。 抽象メソッドでは、メソッド本体は提供されません。 ただしもと共にメソッドとして、メンバーの個々 の定義を含めることで、既定の実装を提供できます、`default`キーワード。 これは、他の .NET 言語の基本クラスでの仮想メソッドの作成と同じです。 このような仮想メソッドは、インターフェイスを実装するクラスでオーバーライドできます。

インターフェイスの既定のアクセシビリティが`public`します。

各メソッドのパラメーターに通常の F# 構文を使用して名前を付けることができます必要に応じて。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

上記の`ISprintable`例では、`Print`メソッドには、型の 1 つのパラメーター`string`名前`format`します。

インターフェイスを実装する 2 つの方法: オブジェクトの式を使用して、クラスの型を使用します。 どちらの場合は、クラス型またはオブジェクトの式は、インターフェイスの抽象メソッドのメソッド本体を提供します。 実装では、各インターフェイスを実装する型に固有です。 そのため、さまざまな種類のインターフェイス メソッドは、互いに異なる可能性があります。

キーワード`interface`と`end`、軽量構文を使用すると、開始と、定義の最後をマークするは省略可能です。 これらのキーワードを使用しない場合、コンパイラは、使用する構成要素を分析することでは、クラスまたはインターフェイスに、型かどうかを推測しようとします。 メンバーを定義または他のクラスの構文を使用する場合は、型がクラスとして解釈されます。

.NET のコーディング スタイルは、大文字のすべてのインターフェイスを開始する`I`します。

## <a name="implementing-interfaces-by-using-class-types"></a>クラス型を使用してインターフェイスを実装します。

使用して、クラス型の 1 つまたは複数のインターフェイスを実装することができます、`interface`キーワードをインターフェイスの名前と`with`キーワード、インターフェイス メンバーの定義後に次のコードに示すようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

インターフェイスの実装が継承されるので、派生クラスは、それらを再実装する必要はありません。

## <a name="calling-interface-methods"></a>インターフェイス メソッドの呼び出し

インターフェイス メソッドは、インターフェイスを実装する型のオブジェクトではなく、インターフェイスを介してのみ呼び出すことができます。 したがってを使用して、インターフェイス型にキャストする必要があります、`:>`演算子または`upcast`これらのメソッドを呼び出すために演算子。

型のオブジェクトがある場合は、インターフェイス メソッドを呼び出す`SomeClass`、次のコードに示すようにアップ キャスト オブジェクトをインターフェイス型で、必要があります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

代替では、そのキャスト、オブジェクトのメソッドを宣言することですし、次の例のように、インターフェイス メソッドを呼び出します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>オブジェクト式を使用してインターフェイスを実装します。

オブジェクトの式は、インターフェイスを実装する簡単な手段です。 これらは、名前付きの型を作成する必要はありませんし、追加メソッドを指定せず、インターフェイス メソッドをサポートするオブジェクト、たいときに便利です。 オブジェクト式は、次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>インターフェイスの継承

インターフェイスは、1 つまたは複数の基底インターフェイスから継承できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [オブジェクト式](object-expressions.md)
- [クラス](classes.md)
