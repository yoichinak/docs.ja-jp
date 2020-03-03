---
title: タプル
description: 名前のないF#が順序付けられた値 (場合によっては異なる型) をグループ化したタプルについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630238"
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

組の例としては、同じ型または異なる型のペア、3要素などがあります。 次のコードに例をいくつか示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>個別の値の取得

次のコードに示すように、パターンマッチングを使用すると、タプル要素の名前にアクセスして割り当てることができます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

また、binding を使用`match` `let`して、式の外側にあるパターン一致を使用してタプルを分解することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

または、組の一致を関数への入力としてパターン化できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

タプルの要素が1つだけ必要な場合は、不要な値に新しい名前を作成しないように、ワイルドカード文字 (アンダースコア) を使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

参照タプルから構造体タプルに要素をコピーすることも簡単です。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

関数`fst` と`snd` (参照タプルのみ) は、組の1番目と2番目の要素をそれぞれ返します。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

トリプルの3番目の要素を返す組み込み関数はありませんが、次のように簡単に記述できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

通常、個々のタプル要素にアクセスするには、パターンマッチングを使用することをお勧めします。

## <a name="using-tuples"></a>タプルの使用

タプルは、次の例に示すように、関数から複数の値を返す便利な方法を提供します。 この例では、整数除算を実行し、組の最初のメンバーとして演算の丸められた結果を返し、その剰余をペアの2番目のメンバーとして返します。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

通常の関数構文によって暗黙的に指定される関数の引数の暗黙のカリー化を回避する場合は、関数の引数としてタプルを使用することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

関数`let sum a b = a + b`を定義するための通常の構文を使用すると、次のコードに示すように、関数の最初の引数の部分的なアプリケーションである関数を定義できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

パラメーターとしてタプルを使用すると、カリー化が無効になります。 詳細については、「[関数](./functions/index.md)」の「引数の部分的な適用」を参照してください。

## <a name="names-of-tuple-types"></a>タプル型の名前

組である型の名前を記述する場合は、 `*`記号を使用して要素を区切ります。 `int`、、および`string`などので構成される組の場合、型は次のように書き込まれます。 `(10, 10.0, "ten")` `float`

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>組とC#の相互運用

C#7.0 では、言語にタプルが導入されました。  C# のタプルは構造体と F# の構造体のタプルに同じです。  とC#相互運用する必要がある場合は、構造体の組を使用する必要があります。

これは簡単に行うことができます。  たとえば、C# クラスに組を渡すし、これは、タプルでも、その結果を消費する必要があるとします。

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

F#コードでは、パラメーターとして構造体のタプルを渡し、その結果を構造体のタプルとして使用できます。

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>参照タプルと構造体組の間の変換

参照タプルと構造体タプルはまったく異なる基になる表現を持つため、暗黙的に変換することはできません。  つまり、次のようなコードはコンパイルされません。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

1つのタプルに対してパターン一致をパターン化し、構成要素を使用してもう一方を構築する必要があります。  例:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>参照タプルのコンパイルされた形式

このセクションでは、コンパイル時の組の形式について説明します。  ここに記載されている情報は、.NET Framework 3.5 以下を対象としている場合を除き、読み取る必要はありません。

組は、複数のジェネリック型のいずれかのオブジェクトにコンパイル`System.Tuple`され、アリティでオーバーロードされます。また、型パラメーターの数も示されます。 タプル型は、C# または Visual Basic の場合など、別の言語からそれらを表示するとき、またはを F# の構成要素に対応していないツールを使用しているときに、このフォームに表示されます。 これら`Tuple`の型は .NET Framework 4 で導入されました。 コンパイラのバージョンを使用して .NET Framework の以前のバージョンをターゲットにする場合[System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) F# コア ライブラリのバージョン 2.0 から。 このライブラリの型は、.NET Framework の2.0、3.0、3.5 の各バージョンを対象とするアプリケーションにのみ使用されます。 型の転送を使用して、.NET Framework 2.0 と .NET Framework 4 F# コンポーネント間のバイナリの互換性を確保します。

### <a name="compiled-form-of-struct-tuples"></a>構造体のコンパイルされた形式のタプル

構造体のタプル (たとえば、 `struct (x, y)`)は、参照タプルとは根本的に異なります。  それらは<xref:System.ValueTuple>型にコンパイルされるか、アリティによってオーバーロードされるか、または型パラメーターの数になります。  これらは [C# 7.0 のタプル](../../csharp/tuples.md)および[Visual Basic 2017のタプル](../../visual-basic/programming-guide/language-features/data-types/tuples.md)と同等であり、双方向で相互運用できます。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
