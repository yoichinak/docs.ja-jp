---
title: 名前空間
description: 学習方法、F#名前空間では、プログラム要素のグループに名前を追加することによって関連する機能の領域にコードを整理できます。
ms.date: 12/08/2018
ms.openlocfilehash: b315d654dad0d36e3584564ad027c68fb3c94cce
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645265"
---
# <a name="namespaces"></a>名前空間

名前空間では、関連する機能の領域にへのグループに名前を追加できるコードを編成できます。F#プログラム要素です。 名前空間は、通常の最上位の要素でF#ファイル。

## <a name="syntax"></a>構文

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>Remarks

名前空間にコードを配置する場合は、ファイル内の最初の宣言は名前空間を宣言する必要があります。 ファイル全体の内容は、名前空間の一部となる、ファイルにさらにその他の名前空間宣言が存在しない指定します。 場合は、[次へ] の名前空間宣言までのすべてのコードは最初の名前空間内にあると見なさします。

値および関数、名前空間を含める直接ことはできません。 代わりに、モジュールでは、値および関数を含める必要があるし、モジュールの名前空間に含まれます。 名前空間は、モジュールの種類を含めることができます。

名前空間の上、XML ドキュメント コメントを宣言できますが、無視されます。 コンパイラ ディレクティブは、名前空間の上にも宣言できます。

名前空間は明示的に宣言する名前空間キーワード、または暗黙的にモジュールを宣言するときに。 名前空間を明示的に宣言するには、名前空間キーワードの後に名前空間の名前を使用します。 次の例では、名前空間を宣言するコード ファイル`Widgets`型とその名前空間に含まれるモジュールを使用します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

ファイルの内容全体が 1 つのモジュールである場合は、宣言することも名前空間に暗黙的を使用して、`module`キーワードとモジュールの完全修飾名で新しい名前空間名を指定します。 次の例では、名前空間を宣言するコード ファイル`Widgets`とモジュール`WidgetsModule`関数が含まれています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

次のコードは上記のコードと同じですが、モジュールがローカル モジュールの宣言。 その場合は、名前空間は、独自の行に表示する必要があります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

1 つ以上のモジュールが 1 つまたは複数の名前空間で同じファイルで必要に応じて、ローカル モジュール宣言を使用する必要があります。 モジュールのローカル宣言を使用する場合は、モジュール宣言で修飾名前空間を使用できません。 次のコードでは、名前空間の宣言と 2 つのモジュールのローカル宣言を持つファイルを示します。 この場合、モジュールが、名前空間で直接に含まれるファイルと同じ名前を持つ、暗黙的に作成されたモジュールはありません。 などのファイルで、コードの他の`do`モジュール メンバーを修飾する必要があるため、内部のモジュールではなく、名前空間には、バインド、`widgetFunction`モジュール名を使用しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

この例の出力は次のとおりです。

```fsharp
Module1 10 20
Module2 5 6
```

詳細については、次を参照してください。[モジュール](modules.md)します。

## <a name="nested-namespaces"></a>入れ子になった名前空間

入れ子になった名前空間を作成するときに、完全修飾する必要があります。 それ以外の場合、新しい最上位レベルの名前空間を作成します。 インデントは、名前空間の宣言では無視されます。

次の例では、入れ子になった名前空間を宣言する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>ファイルとアセンブリの名前空間

名前空間は、1 つのプロジェクトやコンパイルで複数のファイルにまたがることができます。 用語*名前空間のフラグメント*1 つのファイルに含まれている名前空間の一部について説明します。 名前空間は、複数のアセンブリをまたがることもできます。 たとえば、`System`名前空間に多数のアセンブリにまたがり、多数の入れ子になった名前空間が含まれていますが、全体の .NET Framework が含まれています。

## <a name="global-namespace"></a>グローバル Namespace

定義済みの名前空間を使用する`global`に最上位レベルの .NET 名前空間に名前を格納します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

使用することできますもグローバル他の名前空間と名前が競合を解決するのには、たとえば最上位レベルの .NET 名前空間を参照します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>再帰的な名前空間

名前空間は、再帰的に相互に含まれているすべてのコードを許可するには、再帰的なとしても宣言できます。  使用してこれには`namespace rec`します。 使用`namespace rec`されない型とモジュール間の相互参照コードを記述することでいくつかの問題を軽減することができます。 この例を次に示します。

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

なお、例外`DontSqueezeTheBananaException`とクラス`Banana`両方には、互いを参照してください。  モジュールではさらに、`BananaHelpers`とクラス`Banana`も互いに参照してください。 表現することがあるF#を削除した場合、`rec`からキーワード、`MutualReferences`名前空間。

この機能は使用できる最上位[モジュール](modules.md)します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [モジュール](modules.md)
- [F#RFC FS-1009 - ファイル内でより大きな範囲経由で相互に参照型とモジュールを許可します。](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
