---
title: 配列
description: 作成し、F# プログラミング言語で配列を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 4a81a0994479ecd92b8556c4901fea23c3c0507b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772711"
---
# <a name="arrays"></a>配列

> [!NOTE]
> API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

配列は、0 から始まる一連のデータ要素の、固定サイズの変更可能なコレクションで、その型はすべて同じです。

## <a name="creating-arrays"></a>配列の作成

配列は複数の方法で作成できます。 間の連続する値を一覧表示して、小さな配列を作成することができます`[|`と`|]`次の例に示すように、セミコロンで区切られたとします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

各要素を別々の行に配置することもでき、その場合は、セミコロンの区切り記号を省略できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

配列の要素の型は、使用されるリテラルから推論され、すべて同じである必要があります。 次のコードは、1.0 が浮動小数点数で、2 と 3 は整数であるため、エラーになります。

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

シーケンス式を使用して配列を作成することもできます。 1 から 10 までの整数の 2 乗の配列を作成する例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

すべての要素が 0 に初期化される配列を作成するには、`Array.zeroCreate` を使用します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a>要素へのアクセス

ドット演算子を使用して配列要素にアクセスすることができます (`.`) と角かっこ (`[`と`]`)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

配列のインデックスは、0 から始まります。

また、スライス表記を使用して配列の要素にアクセスすることもできます。この方法では、配列のサブ範囲を指定できます。 スライス表記の例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

スライス表記を使用するときは、配列の新しいコピーが作成されます。

## <a name="array-types-and-modules"></a>配列の型とモジュール

F# の配列の型はすべて、.NET Framework 型の <xref:System.Array?displayProperty=nameWithType> です。 したがって、F# の配列では、<xref:System.Array?displayProperty=nameWithType> で使用できるすべての機能がサポートされます。

ライブラリ モジュール[ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) 1 次元配列の操作をサポートしています。 `Array2D`、`Array3D`、`Array4D` の各モジュールには、それぞれ、2 次元、3 次元、4 次元の配列の操作をサポートする関数があります。 4 より大きいランクの配列は、<xref:System.Array?displayProperty=nameWithType> を使用して作成できます。

### <a name="simple-functions"></a>単純な関数

[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) 要素を取得します。 [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) 配列の長さを示します。 [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) 要素を指定した値に設定します。 これらの関数の使い方を次のコード例に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

出力は次のとおりです。

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>配列を作成する関数

既存の配列を必要とせずに配列を作成できる関数がいくつかあります。 [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) すべての要素を含まない新しい配列を作成します。 [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) 指定したサイズの配列を作成し、すべての要素を指定された値に設定します。 [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) ディメンションと、要素を生成する関数を指定して、配列を作成します。 [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) すべての要素が配列の型の値 0 に初期化される配列を作成します。 これらの関数の例を次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

出力は次のとおりです。

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) 既存の配列からコピーした要素を含む新しい配列を作成します。 コピーは簡易コピーです。つまり、要素の型が参照型である場合は、参照だけがコピーされ、基になっているオブジェクトはコピーされません。 これを次のコード例に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

このコードによる出力は、次のようになります。

```
[|Test1; Test2; |]
[|; Test2; |]
```

`Test1` という文字列は、最初の配列にのみ表示されます。これは、`firstArray` の参照が、新しい要素を作成する操作によって上書きされるものの、空の文字列への元の参照は影響を受けず、`secondArray` にまだ存在しているためです。 `Test2` という文字列は、両方の配列で表示されます。これは、`Insert` 型に対する <xref:System.Text.StringBuilder?displayProperty=nameWithType> 操作は基になっている <xref:System.Text.StringBuilder?displayProperty=nameWithType> オブジェクトに影響を与え、このオブジェクトは両方の配列で参照されているためです。

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) 配列のサブ範囲から新しい配列を生成します。 サブ範囲は、開始インデックスと長さで指定します。 `Array.sub` を使用したコードの例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

出力では、サブ配列が要素 5 から開始し、10 個の要素を含むことが示されています。

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) 既存の 2 つの配列を組み合わせることで、新しい配列を作成します。

次のコード例**Array.append**します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

このコードによる出力は、次のようになります。

```
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) 新しい配列に含める配列の要素を選択します。 次のコードで `Array.choose` の例を示します。 配列の要素の型は、オプションの型で返される値の型と一致している必要はありません。 この例では、要素の型は `int` ですが、オプションは多項式関数 `elem*elem - 1` の結果であり、浮動小数点数です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

このコードによる出力は、次のようになります。

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) 既存の配列の配列の各要素に対して指定された関数を実行し、関数によって生成された要素を収集、新しい配列に結合します。 次のコードで `Array.collect` の例を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

このコードによる出力は、次のようになります。

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) 配列のシーケンスを受け取り、1 つの配列に結合します。 次のコードで `Array.concat` の例を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

このコードによる出力は、次のようになります。

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) ブール条件関数を受け取り、条件が true の入力配列の要素のみを含む新しい配列を生成します。 次のコードで `Array.filter` の例を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

このコードによる出力は、次のようになります。

```
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) 既存の配列の順序を反転して、新しい配列を生成します。 次のコードで `Array.rev` の例を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]

このコードによる出力は、次のようになります。

```
"Hello world!"
```

パイプライン演算子を使用して配列を変換する配列モジュール内の関数を簡単に組み合わせることができます (`|>`)、次の例に示すようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

出力は次のようになります。

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>多次元配列

多次元配列を作成できますが、多次元配列リテラルを記述するための構文はありません。 演算子を使用して[ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236)配列要素のシーケンスのシーケンスから配列を作成します。 シーケンスには、配列リテラルまたはリスト リテラルを使用できます。 たとえば、次のコードでは 2 次元の配列が作成されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

関数を使用することもできます。 [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b)関数は、3 と 4 つの次元の配列を使用して、2 次元の配列を初期化するためにします。 これらの関数は、要素の作成に使用する関数を受け取ります。 関数を指定する代わりに、初期値に設定された要素を含む 2 次元配列を作成するには、使用、 [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804)が可能な関数を配列に最大 4 つのディメンションです。 次のコード例では、まず、目的の要素を含む複数の配列から成る 1 つの配列を作成し、次に、`Array2D.init` を使用して目的の 2 次元配列を生成する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

配列インデックスとスライス構文は、4 ランクまでの配列に使用できます。 複数の次元でインデックスを指定するときに次のコード例に示すように、インデックスを分離するのにでコンマを使用します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]

2 次元配列の型は `<type>[,]` として書き出され (`int[,]`、`double[,]` など)、3 次元配列の型は `<type>[,,]` として書き出されます。このように、次元が高くなるにつれ、書き出される型が変わります。

1 次元配列で使用できる関数のサブセットのうち、多次元配列でも使用できるのは一部だけです。 詳細については、次を参照してください。 [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d)、 [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d)、 [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d)、および[ `Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d)します。

### <a name="array-slicing-and-multidimensional-arrays"></a>配列スライスと多次元配列

2 次元配列 (マトリックス) では、範囲を指定して、ワイルドカードを使用して、サブ行列を抽出できます (`*`) 全体の行または列を指定する文字。

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

F# 3.1 では、多次元配列を同じまたは低い次元のサブ配列に多次元配列を分解することができます。 たとえば、単一の行または列を指定して、行列からベクターを取得できます。

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

このスライス構文は、要素アクセス演算子およびオーバーロードされた `GetSlice` メソッドを実装する型に使用できます。 たとえば、次のコードは、F# 2D 配列をラップし、配列のインデックスのサポートを提供する項目プロパティを実装し、3 つのバージョンの `GetSlice` を実装するマトリックス型を作成します。 マトリックス型のテンプレートとしてこのコードの使用が可能であれば、このセクションで説明するすべてのスライスの操作を使用できます。

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a>配列に対するブール条件

関数は、 [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9)と[ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e)それぞれ 1 つまたは 2 つの配列の要素をテストします。 これらの関数は、テスト用の関数を受け取り、要素 (または `true` の場合は要素のペア) のうち、条件を満たす要素がある場合は `Array.exists2` を返します。

次のコードは、`Array.exists` と `Array.exists2` の使用方法を示しています。 これらの例では、ただ 1 つの引数 (この場合は関数引数) を適用することで、新しい関数を作成しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

このコードによる出力は、次のようになります。

```
true
false
false
true
```

同様に、関数は、 [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4)のすべての要素がブール条件を満たすかどうかを判断する配列をテストします。 バリエーション[ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9)同じ長さの 2 つの配列の要素を含むブール関数を使用して同じ動作です。 これらの関数の使い方を次のコード例に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

これらの例の出力は次のようになります。

```
false
true
true
false
```

### <a name="searching-arrays"></a>配列の検索

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) ブール関数を受け取り、関数が返す対象の最初の要素を返します`true`、発生させるか、<xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType>条件を満たす要素が存在しない場合。 [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) ように、 `Array.find`、要素自体ではなく、要素のインデックスを返す点が異なります。

次のコードでは、`Array.find` と `Array.findIndex` を使用して、完全平方かつ完全立方である値を探しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

出力は次のとおりです。

```
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) ように、`Array.find`点を除き、その結果、オプション型でありを返します、`None`要素が存在しない場合。 一致する要素が配列内にあるかどうかわからない場合は、`Array.tryFind` ではなく、`Array.find` を使用してください。 同様に、 [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a)などは[ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)が点を除いて、オプションの種類は戻り値の値。 要素が見つからない場合、オプションは `None` です。

`Array.tryFind` を使用したコードの例を次に示します。 このコードでは、前に示したコードを利用しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

出力は次のとおりです。

```
Found an element: 1
Found an element: 729
```

使用[ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e)を見つけることだけでなく、要素を変換する必要がある場合。 この関数の結果は、変換した要素をオプションの値として返した最初の要素になります。該当する要素が見つからない場合は、`None` を返します。

`Array.tryPick` の使用方法を次のコードに示します。 この例では、ラムダ式の代わりに、複数のローカル ヘルパー関数を定義することでコードを簡単にしています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

出力は次のとおりです。

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a>配列に対する計算の実行

[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e)関数は、配列の各要素の平均を返します。 この関数を使用できるのは、整数による正確な除算がサポートされている要素型だけです。そのため、浮動小数点型では使用できますが、整数型では使用できません。 [ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54)関数は、各要素に対して関数の呼び出しの結果の平均を返します。 整数型の配列の場合は、`Array.averageBy` を使用し、この関数で各要素を浮動小数点型に変換して計算することもできます。

使用[ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b)または[ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd)要素の型がサポートされている場合、最大値または最小の要素を取得します。 同様に、 [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045)と[ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f)が最初に実行する、比較をサポートする型に変換するなどの関数を許可します。

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) 、配列の要素を追加し、 [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b)各要素に対して関数を呼び出すし、結果をまとめて追加します。

戻り値を格納することがなく、配列内の各要素に対して関数を実行、 [ `Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516)します。 同じ長さの 2 つの配列に関連する関数、 [ `Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc)します。 関数の結果の配列を保持することも必要がある場合を使用して、 [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45)または[ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c)、一度に 2 つの配列で動作します。

バリエーション[ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486)と[ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405)計算に関与する要素のインデックスを許可する以外にも同様です[ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4)[ `Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0)します。

関数は、 [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09)、 [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c)、 [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d)、 [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9)、 [`Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)、および[ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad)配列のすべての要素に関連するアルゴリズムを実行します。 同様に、バリエーション[ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79)と[ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) 2 つの配列に対して計算を実行します。

これらの関数の計算を実行するために同じ名前の関数に対応して、 [List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)します。 使用例については、次を参照してください。[一覧](lists.md)します。

### <a name="modifying-arrays"></a>配列の変更

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) 要素を指定した値に設定します。 [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) 指定された値に配列の要素の範囲を設定します。 `Array.fill` のコード例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

出力は次のとおりです。

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

使用することができます[ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667)に 1 つのサブセクションを別の配列にコピーします。

### <a name="converting-to-and-from-other-types"></a>他の型との相互変換

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) リストから配列を作成します。 [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) シーケンスから配列を作成します。 [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4)配列型から他のこれらのコレクション型に変換します。

### <a name="sorting-arrays"></a>配列の並べ替え

使用[ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312)を汎用的な比較関数を使用して配列を並べ替えます。 使用[ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) 、値を生成する関数を指定すると呼ばれる、*キー*を汎用的な比較関数を使用して、キーで並べ替えるには、します。 使用[ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95)カスタム比較関数を提供したい場合。 `Array.sort`、`Array.sortBy`、および `Array.sortWith` は、いずれも、並べ替えた配列を新しい配列として返します。 バリエーション[ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0)、 [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)、および[ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b)新しいものを返す代わりに、既存の配列を変更します。

### <a name="arrays-and-tuples"></a>配列とタプル

関数は、 [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187)と[ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48)配列、またはその逆のタプルをタプルのペアの配列に変換します。 [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677)は 3 つの要素の組または組の 3 つの配列で動作することを除いてに似ています。

## <a name="parallel-computations-on-arrays"></a>配列に対する並列計算

モジュール[ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09)配列に対する並列計算を実行するための関数が含まれています。 このモジュールは、Version 4 より前の .NET Framework を対象とするアプリケーションでは使用できません。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
