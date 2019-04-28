---
title: スライス (F#)
description: 既存のスライスを使用する方法について説明しますF#データ型と他のデータ型のスライスを定義する方法。
ms.date: 01/22/2019
ms.openlocfilehash: 1d8bb029ad18c8853ab58888959967ed279fb368
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925995"
---
# <a name="slices"></a>スライス

F#、スライスがデータ型のサブセットです。 データ型から、スライスを実行できるようにするには、データ型を定義する必要がありますか、`GetSlice`メソッドまたは、[拡張子を入力](type-extensions.md)にスコープされています。 この記事は、既存のファイルからのスライスを実行する方法を説明しますF#型と、独自に定義する方法。

スライスはのような[インデクサー](members/indexed-properties.md)が、基になるデータ構造体から単一の値を生成するのではなく複数の。

F#現在は、文字列、リスト、配列、および 2D 配列のスライスの組み込みサポート。

## <a name="basic-slicing-with-f-lists-and-arrays"></a>基本的なスライスF#リストと配列

スライスは最も一般的なデータ型はF#リストと配列。 次の例では、リストでそれを行う方法を示します。

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

リストのスライスと同じように、配列のスライスします。

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a>多次元配列のスライス

F#多次元配列をサポートしている、F#コア ライブラリです。 1 次元の配列と多次元配列のスライスにも役立ちます。 ただし、特定の行と列のスライスを実行できるように、追加のディメンションの概要は、構文がやや異なる定められています。

2D 配列のスライスには、次の例に示します。

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

F#コア ライブラリを一切定義しません`GetSlice`3D の配列。 定義する必要がありますまたは他の配列以上のディメンションをスライスする場合、`GetSlice`メンバー自分でします。

## <a name="defining-slices-for-other-data-structures"></a>その他のデータ構造にスライスを定義します。

F#コア ライブラリが限定的なセットの種類のスライスを定義します。 多くのデータ型のスライスを定義する場合は、これを行う型定義自体または型の拡張機能。

たとえば、ここではのスライスを定義する方法、<xref:System.ArraySegment%601>便利なデータ操作に許可するクラス。

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(?start, ?finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>必要がある場合は、ボックス化を回避するためにインライン化の使用

実際には構造体である型のスライスを定義している場合ことをお勧めする`inline`、`GetSlice`メンバー。 F#コンパイラによる最適化のスライスの結果としてヒープ割り当てを回避する、省略可能な引数。 これは非常に重要ですなどの構造をスライス<xref:System.Span%601>をヒープに割り当てることができません。

```fsharp
open System

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a>関連項目

- [インデックス付きプロパティ](members/indexed-properties.md)
