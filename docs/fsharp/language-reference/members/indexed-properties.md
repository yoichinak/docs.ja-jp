---
title: インデックス付きプロパティ
description: インデックス付きプロパティについて説明しますF#、順序付けられたデータを配列に似たアクセスを許可します。
ms.date: 10/17/2018
ms.openlocfilehash: bc330641c451973ddefa0a34fe6e757a808f6cb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903826"
---
# <a name="indexed-properties"></a>インデックス付きプロパティ

順序付けられたデータを抽象化するクラスを定義するときに基になる実装を公開することがなく、そのデータにインデックス付きのアクセスを提供する便利なあることができます。 これは、`Index`メンバー。

## <a name="syntax"></a>構文

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Remarks

前の構文のフォームは、両方があるインデックス付きプロパティを定義する方法を示して、`get`と`set`メソッドが、`get`メソッドのみかが、`set`メソッドのみ。 取得のみと set のみに対して表示される構文に示す構文を組み合わせてまたを get と set の両方を持つプロパティを生成します。 この後者の形式を使用すると、get に異なるアクセシビリティ修飾子と属性を配置し、メソッドを設定できます。

名前を使用して`Item`コンパイラは、既定のインデックス付きプロパティとしてプロパティを扱います。 A*既定のインデックス付きプロパティ*オブジェクト インスタンスの配列に似た構文を使用してアクセスできるプロパティです。 たとえば場合、`o`構文は、このプロパティを定義する型のオブジェクトである`o.[index]`プロパティにアクセスするために使用します。

既定以外のインデックス付きプロパティにアクセスするための構文は、プロパティと、通常のメンバーと同様、かっこ内のインデックスの名前を提供します。 たとえば場合のプロパティ`o`が呼び出されます`Ordinal`、記述する`o.Ordinal(index)`へのアクセスします。

使用する形式に関係なく、インデックス付きプロパティの set メソッドのカリー化されたフォームを常に使用する必要があります。 カリー化関数については、次を参照してください。[関数](../functions/index.md)します。

## <a name="example"></a>例

次のコード例では、定義と使用の既定と既定以外のインデックス付きプロパティ get し、set メソッドを示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>出力

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>複数のインデックス値を含むインデックス付きプロパティ

インデックス付きプロパティには、1 つ以上のインデックス値を持つことができます。 その場合は、プロパティを使用する場合に、値はコンマで区切られます。 このようなプロパティの set メソッドには、キーを含むタプル 1 つ目は、2 番目の値を設定するは 2 つのカリー化された引数が必要です。

次のコードでは、複数のインデックス値を含むインデックス付きプロパティの使用を示します。

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a>関連項目

- [メンバー](index.md)
