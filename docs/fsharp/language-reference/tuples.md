---
title: タプル
description: については、F#タプル、名前のないが、順序付けされた値のさまざまな種類のグループ化します。
ms.date: 05/16/2016
ms.openlocfilehash: 950451ad1672e0c9fc609773f1bc32fc13636ddb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645113"
---
# <a name="tuples"></a>タプル

*タプル*は、名前はないが順序付けられた値のさまざまな種類のグループです。  タプルは参照型か構造体のどちらかです。

## <a name="syntax"></a>構文

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Remarks

各*要素*前の構文では有効な F# 式を指定できます。

## <a name="examples"></a>使用例

ペア、3 要素、および同じまたは別の型のタプルの例が含まれます。 いくつかの例は、次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>個々 の値を取得します。

使えばパターン マッチングにアクセスしたり、タプルの要素の名前を割り当てる次のコードに示すようにできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

外部のパターン マッチングを使用してタプルを分解することもできます、`match`式を使用して`let`バインド。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

パターンを作成できますまたは関数への入力として組の一致します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

タプルの 1 つだけの要素が必要な場合、必要のない値の新しい名前を作成しないようにする、ワイルドカード文字 (アンダー スコア) を使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

構造体タプルに参照組から要素のコピーも簡単です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

関数は、`fst`と`snd`(組のみを参照)、最初し、2 番目、タプルの要素のそれぞれします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

3 つの要素の 3 番目の要素を返す組み込み関数はありませんが、次のように簡単に書き込む 1 つ。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

一般に、パターン マッチングを使用して、タプルの個々 の要素にアクセスすることをお勧めします。

## <a name="using-tuples"></a>タプルを使用してください。

タプルは、次の例に示すように、関数から複数の値を返す便利な方法を提供します。 この例では、整数除算を実行し、結果を丸め、タプルのペアの最初のメンバーとして操作と、ペアの 2 番目のメンバーとして残りの部分を返します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

暗黙的なカリー化関数の引数は、通常の関数の構文で指定されるを回避する場合、組も関数の引数として使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

関数を定義するには、通常の構文`let sum a b = a + b`次のコードに示すように、関数の最初の引数の部分的なアプリケーションである関数を定義することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

パラメーターとして組を使用するには、カリー化が無効にします。 詳細については、「部分的な引数アプリケーション」を参照してください[関数](functions/index.md)します。

## <a name="names-of-tuple-types"></a>タプル型の名前

使用する組である型の名前を記述するときに、`*`要素を区切る記号。 構成される組の`int`、 `float`、および`string`など`(10, 10.0, "ten")`種類は次のように書き込まれます。

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>C# のタプルとの相互運用

C# 7.0 では、言語に組が導入されました。  C# のタプルは構造体と F# の構造体のタプルに同じです。  C# を使用した相互運用する必要がある場合は、構造体のタプルを使用する必要があります。

これは、簡単に実行できます。  たとえば、C# クラスに組を渡すし、これは、タプルでも、その結果を消費する必要があるとします。

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

F#コード、パラメーターとして構造体の組を渡すし、構造体タプルとして結果を消費することができます。

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>参照の組と構造体のタプル間の変換

参照の組と構造体のタプルは、完全に別の基になる表現であるため、暗黙的に変換可能ではありません。  これは、次のコードはコンパイルされません。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

パターンを作成する必要があります 1 つのタプルが一致し、他の構成要素を構築します。  例:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>参照の組のコンパイル済みの形式

このセクションでは、している、コンパイル時に、タプルの形式が説明します。  ここにある情報は、.NET Framework 3.5 を対象としている場合を除き、読み取りに必要なまたは下限はありません。

タプルは、すべての名前付き、いくつかのジェネリック型のいずれかのオブジェクトにコンパイル`System.Tuple`アリティ、または型パラメーターの数をオーバー ロードされます。 タプル型は、C# または Visual Basic の場合など、別の言語からそれらを表示するとき、またはを F# の構成要素に対応していないツールを使用しているときに、このフォームに表示されます。 `Tuple`型が .NET Framework 4 で導入されました。 コンパイラのバージョンを使用して .NET Framework の以前のバージョンをターゲットにする場合[System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) F# コア ライブラリのバージョン 2.0 から。 このライブラリ内の型は、2.0、3.0、および .NET Framework 3.5 のバージョンを対象とするアプリケーションに対してのみ使用されます。 型の転送を使用して、.NET Framework 2.0 と .NET Framework 4 F# コンポーネント間のバイナリの互換性を確保します。

### <a name="compiled-form-of-struct-tuples"></a>構造体のタプルのコンパイル済みの形式

構造体のタプル (たとえば、 `struct (x, y)`)は、参照タプルとは根本的に異なります。  それらは<xref:System.ValueTuple>型にコンパイルされるか、アリティによってオーバーロードされるか、または型パラメーターの数になります。  これらは [C# 7.0 のタプル](../../csharp/tuples.md)および[Visual Basic 2017のタプル](../../visual-basic/programming-guide/language-features/data-types/tuples.md)と同等であり、双方向で相互運用できます。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
