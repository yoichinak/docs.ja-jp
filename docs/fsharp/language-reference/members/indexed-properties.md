---
title: インデックス付きプロパティ
description: のF#インデックス付きプロパティについて説明します。これにより、順序付けられたデータへの配列に似たアクセスが可能になります。
ms.date: 10/17/2018
ms.openlocfilehash: 379417e31b8e178d8c939e5b23dc144bfb17e562
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627560"
---
# <a name="indexed-properties"></a>インデックス付きプロパティ

順序付けされたデータを抽象化するクラスを定義する場合、基になる実装を公開せずに、そのデータへのインデックス付きアクセスを提供すると役立つことがあります。 これは、 `Item`メンバーによって行われます。

## <a name="syntax"></a>構文

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Remarks

前の構文の形式`get`では、メソッド`set`とメソッドの両方を持つインデックス付きプロパティを定義する方法`get` 、メソッドを持つもの、 `set`またはメソッドのみを持つインデックス付きプロパティを定義する方法を示します。 Get のみに表示される構文と、set のみに表示される構文の両方を組み合わせて、get と set の両方を持つプロパティを生成することもできます。 この2番目の形式では、get メソッドと set メソッドに異なるアクセシビリティ修飾子と属性を配置できます。

名前`Item`を使用すると、コンパイラはプロパティを既定のインデックス付きプロパティとして扱います。 *既定のインデックス付きプロパティ*は、オブジェクトインスタンスで配列に似た構文を使用してアクセスできるプロパティです。 たとえば、が、 `o`このプロパティを定義する型のオブジェクトである場合、構文`o.[index]`を使用してプロパティにアクセスします。

既定以外のインデックス付きプロパティにアクセスするための構文では、通常のメンバーと同じように、プロパティの名前とインデックスをかっこで囲んで指定します。 たとえば、の`o`プロパティが呼び出さ`Ordinal`れた場合は、それ`o.Ordinal(index)`にアクセスするためにを記述します。

使用するフォームに関係なく、インデックス付きプロパティの set メソッドには、常にカリー化された形式を使用する必要があります。 カリー化関数の詳細については、「[関数](../functions/index.md)」を参照してください。

## <a name="example"></a>例

次のコード例は、get メソッドと set メソッドを持つ既定のインデックス付きプロパティと既定以外のインデックス付きプロパティの定義と使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>出力

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>複数のインデックス値を持つインデックス付きプロパティ

インデックス付きプロパティには、複数のインデックス値を指定できます。 この場合、プロパティが使用されるときに、値はコンマで区切られます。 このようなプロパティの set メソッドには、2つのカリー化引数が必要です。最初の引数はキーを含むタプルで、2番目の引数は設定する値です。

次のコードは、複数のインデックス値を持つインデックス付きプロパティの使用方法を示しています。

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
