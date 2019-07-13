---
title: 表示内容
description: についてF#、同じ型の要素の順序付けされた不変の系列を一覧表示します。
ms.date: 05/16/2016
ms.openlocfilehash: cc4e292280cca0dca37f69cf5a46ec2822d08d5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904125"
---
# <a name="lists"></a>表示内容

> [!NOTE]
> この記事の API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

F# のリストは、順序が指定されており変更できない一連の同じ型の要素です。 リストに対する基本操作を実行するには、内の関数を使用して、 [List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)します。

## <a name="creating-and-initializing-lists"></a>リストの作成と初期化

リストを定義するには、次のコード行に示すように、セミコロンで区切って明示的にリストした要素を角かっこで囲みます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

要素間に改行を挿入することもできます。その場合はセミコロンの区切り記号を省略できます。 要素の初期化式が長い場合、各要素にコメントを含める場合は、改行の構文を使用するとコードが読みやすくなります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

通常、リストの要素はすべて同じ型である必要があります。 例外として、要素が基本型として指定されているリストには、派生型の要素を含めることができます。 したがって次に示す例は、`Button` と `CheckBox` の両方が `Control` から派生しているため、受け入れられます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

また、次のコードで示すように、整数を範囲演算子 (`..`) で区切って示した範囲を使用して、リストの要素を定義することもできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

空のリストは、間に何も含まない 1 組の角かっこで示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

シーケンス式を使用してリストを作成することもできます。 参照してください[シーケンス式](sequences.md#sequence-expressions)詳細についてはします。 たとえば、次のコードでは 1 から 10 までの整数の 2 乗のリストが作成されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>リストの操作に使用する演算子

リストに要素を付加するには、`::` (cons) 演算子を使用します。 `list1` が `[2; 3; 4]` の場合、次のコードでは `list2` が `[100; 2; 3; 4]` として作成されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

互換性のある型を含むリストを連結するには、次のコードに示すように `@` 演算子を使用します。 `list1` が `[2; 3; 4]` であり、`list2` が `[100; 2; 3; 4]` の場合、このコードでは `list3` が `[2; 3; 4; 100; 2; 3; 4]` として作成されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

リストに対する操作を実行するための関数では使用、 [List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)します。

F# のリストは変更できないため、変更操作を行うと、既存のリストが変更されるのではなく、新しいリストが生成されます。

リストF#、つまり要素へのアクセスは O とリストの先頭のみにアクセスする操作は o (1)、シングル リンク リストとして実装されます (*n*)。

## <a name="properties"></a>プロパティ

リスト型では次のプロパティがサポートされています。

|プロパティ|型|説明|
|--------|----|-----------|
|[ヘッド](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|1 番目の要素。|
|[空](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|該当する型の空のリストを返す静的プロパティ。|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|リストに要素がない場合は `true` です。|
|[Item](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|指定したインデックスの要素 (起点を 0 とする)。|
|[長さ](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|要素の数。|
|[末尾](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|1 番目の要素を除いたリスト。|

これらのプロパティを使用したいくつかの例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>リストの使用

リストを使用してプログラミングを行うと、少量のコードで複雑な操作を実行できます。 このセクションでは、関数型プログラミングにおいて重要なリストに対する一般的な操作について説明します。

### <a name="recursion-with-lists"></a>リストを使用した再帰

リストは、再帰的なプログラミング技法に非常に適しています。 リストのすべての要素に対して実行する必要がある操作があるとします。 この操作を再帰的に実行するには、リストの先頭に対して処理を行った後にリストの後部 (元のリストの最初の要素を除いた要素で構成される、元のリストより小さいリスト) を次の再帰レベルに戻します。

このような再帰関数を記述するには、パターン マッチで cons 演算子 (`::`) を使用します。これによって、リストの先頭を末尾から分離できます。

パターン マッチを使用して、リストに対する操作を実行する再帰関数を実装する方法を次のコード例に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

このコードは小さいリストでは問題なく動作しますが、リストが大きくなると、スタックがオーバーフローする可能性があります。 次に示すコードは、再帰関数の処理では標準的な技法であるアキュムレータ引数を使用して、このコードを改善したものです。 アキュムレータ引数を使用すると、関数の後部が再帰的になり、スタック領域を節約できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

関数 `RemoveAllMultiples` は、2 つのリストを受け取る再帰関数です。 1 番目のリストは、倍数を削除する数値が格納されたリストで、2 番目のリストは、数値を削除する元のリストです。 次の例のコードでは、この再帰関数を使用してリストから素数以外をすべて削除します。その結果、素数のリストが残ります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

出力は次のとおりです。

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>モジュール関数

[List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)リストの要素にアクセスする機能を提供します。 先頭の要素には、最も迅速かつ簡単にアクセスできます。 プロパティを使用して[ヘッド](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)またはモジュール関数[List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2)します。 リストの末尾を使用してアクセスすることができます、[末尾](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)プロパティまたは[List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601)関数。 インデックスを使用して要素を検索するには使用、 [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1)関数。 `List.nth` はリストを走査します。 そのため、これは O (*n*)。 コードで `List.nth` を頻繁に使用する場合は、リストの代わりに配列を使用すると、効果的である可能性があります。 配列での要素のアクセスは O(1) です。

### <a name="boolean-operations-on-lists"></a>リストに対するブール演算

[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107)関数が一覧にすべての要素があるかどうかを判断します。

[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)関数に適用されるブール値の一覧を返します要素にテスト`true`任意の要素は、テストを満たしている場合。 [List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e)と似ていますが、一連の 2 つのリスト内の要素のペアで動作します。

`List.exists` を使用したコードの例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

出力は次のとおりです。

```
For list [0; 1; 2; 3], contains zero is true
```

次の例は、`List.exists2` の使い方を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

出力は次のとおりです。

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

使用することができます[List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7)一覧のすべての要素が条件を満たすかどうかをテストするかどうか。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

出力は次のとおりです。

```
true
false
```

同様に、 [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) 2 つのリスト内の対応する位置のすべての要素が要素の各ペアを含むブール式を満たすかどうかを決定します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

出力は次のとおりです。

```
true
false
```

### <a name="sort-operations-on-lists"></a>リストに対する並べ替え操作

[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d)、 [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)、および[List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7)関数は、リストを並べ替えます。 並べ替え関数は、これら 3 つの関数のどれを使用するかを判断します。 `List.sort` は、既定の一般的な比較を使用します。 一般的な比較は、汎用の比較関数に基づくグローバル演算子を使用して、値を比較します。 この比較は、単純な数値型、タプル、レコード、判別共用体、リスト、配列、および `System.IComparable` を実装する任意の型など、広範な要素型で効率的に動作します。 `System.IComparable` を実装する型の場合は、汎用的な比較で `System.IComparable.CompareTo()` 関数が使用されます。 また、汎用的な比較は文字列にも使用できますが、カルチャに依存しない並べ替え順序が使用されます。 関数型のようなサポートされない型には、汎用的な比較を使用できません。 また、既定の汎用的な比較は、小さい構造の型の場合に最高のパフォーマンスを示します。比較と並べ替えが頻繁に必要な大きい構造の型の場合は、`System.IComparable` を実装し、`System.IComparable.CompareTo()` メソッドを効率的に実装することを考慮してください。

`List.sortBy` 関数は、並べ替え基準として使用される値を返す関数を受け取り、`List.sortWith` 関数は、比較関数を引数として受け取ります。 これら 2 つの関数は、比較をサポートしない型を使用するとき、またはカルチャを認識する文字列の場合のように複雑な比較セマンティクスを必要とする比較の場合に役立ちます。

次の例は、`List.sort` の使い方を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

出力は次のとおりです。

```
[-2; 1; 4; 5; 8]
```

次の例は、`List.sortBy` の使い方を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

出力は次のとおりです。

```
[1; -2; 4; 5; 8]
```

次の例は、`List.sortWith` の使い方を示しています。 この例では、カスタムの比較関数 `compareWidgets` を使用して、まず、カスタム型の 1 つのフィールドを比較し、最初のフィールドの値が同じである場合は、さらに別のフィールドを比較しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

出力は次のとおりです。

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>リストに対する検索操作

リストに対するさまざまな検索操作がサポートされています。 最も簡単な[List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06)、特定の条件に一致する最初の要素を検索することができます。

次のコード例では、`List.find` を使用して、5 で割り切れる最初の数をリストから検索する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

The result is 5.

呼び出す場合は、要素は、最初に変換する必要があります、 [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)オプションを返します関数を受け取るが、値の最初のオプションを検索、`Some(x)`します。 `List.pick` は要素を返す代わりに、結果 `x` を返します。 一致する要素が見つからない場合、`List.pick` は `System.Collections.Generic.KeyNotFoundException` をスローします。 `List.pick` の使用方法を次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

出力は次のとおりです。

```
"b"
```

検索操作の別のグループ[List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d)関連関数は、オプションの値を返します。 `List.tryFind` 関数は、条件を満たす要素がリストにある場合は、その最初の要素を返します。条件を満たす要素がない場合は、オプション値 `None` を返します。 バリエーション[List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec)が見つかった場合、要素自体ではなく、要素のインデックスを返します。 これらの関数を次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

出力は次のとおりです。

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>リストに対する算術演算

Sum や average などの一般的な算術演算に組み込まれている、 [List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)します。 使用する[List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9)、リストの要素の型をサポートする必要があります、`+`演算子と 0 個の値。 すべての組み込み数値型はこの条件を満たしています。 使用する[List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1)要素の型は、除算、剰余は整数型は除外されますが、浮動小数点型では、なしをサポートする必要があります。 [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d)と[List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403)関数をパラメーターとして関数を実行して、この関数の結果は、合計または平均値の計算に使用されます。

次のコードは、`List.sum`、 `List.sumBy`、および `List.average` の使用方法を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

出力は `1.000000`になります。

`List.averageBy` の使用方法を次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

出力は `5.5`になります。

### <a name="lists-and-tuples"></a>リストとタプル

タプルを含むリストは、zip 関数および unzip 関数で操作できます。 これらの関数は、単一値の 2 つのリストを結合してタプルのリストを 1 つ生成したり、タプルの 1 つのリストを分割して単一の値のリストを 2 つ生成したりします。 最も単純な[List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c)関数が 1 つの要素の 2 つのリストを受け取り、タプルのペアの 1 つのリストを生成します。 別のバージョン、 [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b)1 つの要素の 3 つのリストを受け取り、3 つの要素の組の 1 つのリストを生成します。 次のコード例は、`List.zip` の使用方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

出力は次のとおりです。

```
[(1, -1); (2, -2); (3; -3)]
```

次のコード例は、`List.zip3` の使用方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

出力は次のとおりです。

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

対応するバージョンを解凍[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)と[List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)組のリストを受け取り、最初のリストがそれぞれの組の最初のすべての要素が含まれている、タプルの一覧を返すと、2 番目のリストには、各タプルの 2 番目の要素が含まれています。

次のコード例は、の使用を示します[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

出力は次のとおりです。

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

次のコード例は、の使用を示します[List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

出力は次のとおりです。

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>リスト要素に対する操作

F# は、リストの要素に対するさまざまな操作をサポートしています。 最も単純な[List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f)を使用すると、一覧のすべての要素に対して関数を呼び出します。 種類があります[List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40)、2 つのリストの要素に対して演算を実行できます[List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60)などは`List.iter`として各要素のインデックスが渡されることを除き、各要素に対して呼び出される関数の引数と[List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c)の機能の組み合わせである`List.iter2`と`List.iteri`します。 次のコード例にこれらの関数を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

出力は次のとおりです。

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

リストの要素を変換するもう 1 つの頻繁に使用される関数は[List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)を使用すると、一覧の各要素に関数を適用して、新しいリストにすべての結果を格納します。 [List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57)と[List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8)は複数のリストを受け取るバリエーションです。 使用することもできます[List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14)と[List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49)場合、要素だけでなく、関数は各要素のインデックスに渡される必要があります。 `List.mapi2` と `List.mapi` の唯一の違いは、`List.mapi2` では 2 つのリストが使用される点です。 次の例を示しています[List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

出力は次のとおりです。

```
[2; 3; 4]
```

`List.map2` を使用する例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

出力は次のとおりです。

```
[5; 7; 9]
```

`List.map3` を使用する例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

出力は次のとおりです。

```
[7; 10; 13]
```

`List.mapi` を使用する例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

出力は次のとおりです。

```
[1; 3; 5]
```

`List.mapi2` を使用する例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

出力は次のとおりです。

```
[0; 7; 18]
```

[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f)などは`List.map`, 点が、各要素はリストを生成および最終的な一覧にこれらすべてのリストが連結されます。 次のコードでは、リストの各要素が 3 つの値を生成します。 これらすべてが 1 つのリストに集約されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

出力は次のとおりです。

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

使用することも[List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248)、ブール条件を受け取り、特定の条件を満たす要素のみで構成される新しいリストを生成します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

結果のリストは `[2; 4; 6]` です。

Map と filter を組み合わせた[List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d)変換し、同時に要素を選択することができます。 `List.choose` は、オプションを返す関数をリストの各要素に適用し、関数がオプション値 `Some` を返す要素の結果から成る新しいリストを返します。

次のコードでは、`List.choose` を使用して、最初の文字が大文字の単語を単語のリストから選択しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

出力は次のとおりです。

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>複数のリストに対する操作

複数のリストを結合できます。 2 つのリストに 1 つに参加するには、使用[List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426)します。 使用して複数の 2 つのリストを結合する[List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c)します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>フォールド操作とスキャン操作

リストの操作の中には、リストのすべての要素間の依存関係を伴うものがあります。 フォールド操作とスキャン操作は`List.iter`と`List.map`、各要素に対して関数を呼び出す場合、これらの操作と呼ばれる追加のパラメーターを提供する、*アキュムレータ*情報を保持します。計算。

リストに対して計算を実行するには、`List.fold` を使用します。

次のコード例は、の使用を示します[List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0)さまざまな操作を実行します。

リストが走査されます。アキュムレータ `acc`は、計算の進行に伴って渡される値です。 1 番目の引数はアキュムレータとリスト要素を受け取り、そのリスト要素に対する計算の中間結果を返します。 2 番目の引数はアキュムレータの初期値です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

関数名に数字が付いている関数は、複数のリストを操作するバージョンです。 たとえば、 [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) 2 つのリストに対して計算を実行します。

次の例は、`List.fold2` の使い方を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8)を異なる`List.fold`最終的な追加のパラメーターの値を返しますが、`List.scan`追加のパラメーター (最終値) に加え、中間値の一覧を返します。

これらの各関数が含まれていますリバース バリエーションの 1 つ、たとえば、 [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7)での順序でリストが走査して、引数の順序。 また、`List.fold`と`List.foldBack`のバリエーションがある[List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343)と[List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2)、同じ長さの 2 つのリストを受け取る。 各要素に対して実行される関数では、両方のリストの対応する要素を使用して操作を実行できます。 2 つのリストの要素の型が同じである必要はありません。たとえば、次の例では、一方のリストには銀行口座の取引金額が格納され、もう一方のリストには取引の種類 (預け入れまたは引き出し) が格納されています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

合計のような計算の場合は、結果が走査の順序に依存しないため、`List.fold` と `List.foldBack` のどちらを使用しても、同じ結果になります。 次の例では、`List.foldBack` を使用してリストの要素を追加します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

次の例では、銀行口座の例に戻ります。 今度は、利息を計算する新しい取引の種類が追加されています。 取引の順序によって期末残高が異なります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

関数は、 [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b)に似ています`List.fold`と`List.scan`ただし、別のアキュムレータを受け渡すのではなく`List.reduce`の代わりに、要素型の 2 つの引数を受け取る関数には1 つだけ、およびそれらの引数の 1 つは、計算の中間結果を格納することを意味、アキュムレータとして機能します。 `List.reduce` は、初めに最初の 2 つのリスト要素に対して演算を実行し、次にその演算の結果と次の要素を合わせて使用します。 独自の型を持つ別のアキュムレータがないため、`List.reduce` を `List.fold` の代わりに使用できるのは、アキュムレータと要素が同じ型を持つ場合だけです。 `List.reduce` を使用したコードの例を次に示します。 指定されたリストに要素がない場合、`List.reduce` は例外をスローします。

次のコードでは、ラムダ式の最初の呼び出しで引数 2 と 4 を受け取って 6 を返し、次の呼び出しで引数 6 と 10 を受け取るので、結果が 16 になります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>リストと他のコレクション型との変換

`List` モジュールには、シーケンスと配列との間で両方向の変換を行うための関数が用意されています。 シーケンスとの間に変換する[List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0)または[List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0)します。 または配列に変換する[List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547)または[List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032)します。

### <a name="additional-operations"></a>その他の操作

リストに対する追加の操作については、ライブラリのリファレンス トピックを参照してください。 [Collections.List モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d)します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
- [シーケンス](sequences.md)
- [配列](arrays.md)
- [オプション](options.md)
