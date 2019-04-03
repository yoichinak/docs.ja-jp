---
title: モジュール
description: F# のモジュールの値、型、および F# のプログラム内の関数値などの F# コードでのグループ化の方法について説明します。
ms.date: 04/24/2017
ms.openlocfilehash: 9e5bef4ffe3301a69bbe32483625652d988f8a35
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611114"
---
# <a name="modules"></a>モジュール

F# 言語のコンテキストで、*モジュール*値、型、および F# のプログラム内の関数値などの F# コードでのグループです。 モジュールのコードをグループ化すると、関連するコードをまとめることができ、プログラム内で名前の競合を回避するのに役立ちます

## <a name="syntax"></a>構文

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a>Remarks

F# のモジュールは、型、値、関数の値のコードなどの F# コード構造のグループ化`do`バインドします。 静的メンバーのみを持つ共通言語ランタイム (CLR) クラスとして実装されます。 モジュールでファイル全体が含まれているかどうかによって、モジュール宣言の 2 種類があります。 最上位レベルのモジュールの宣言とローカル モジュール宣言します。 最上位レベルのモジュールの宣言には、モジュールには中にファイル全体が含まれます。 最上位レベルのモジュールの宣言は、ファイル内の最初の宣言としてのみ表示できます。

省略可能な最上位レベルのモジュール宣言の構文で*名前空間の修飾*は、モジュールを含む入れ子になった名前空間の名前のシーケンスです。 修飾名前空間は、事前に宣言する必要はありません。

最上位レベルのモジュール内の宣言にインデントを設定する必要はありません。 ローカル モジュールのすべての宣言にインデントを設定します。 モジュールのローカル宣言では、モジュール宣言の下にインデント、宣言は、モジュールの一部です。

すべてのローカル モジュールを含む、ファイルの内容全体を拡張子を付けずにファイルと同じ名前を持つ、暗黙的に作成された最上位モジュールの一部となるコード ファイルが最上位レベルのモジュールの宣言または名前空間の宣言で始まっていない場合最初の文字を大文字に変換します。 たとえば、次のファイルがあるとします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

このファイルは、この方法で記述されている場合、コンパイルは。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

をファイルに複数のモジュールがある場合は、モジュールごとにローカル モジュールの宣言を使用する必要があります。 外側の名前空間が宣言されている場合、これらのモジュールは、外側の名前空間の一部になります。 外側の名前空間が宣言されていない場合、モジュールは、暗黙的に作成された最上位レベルのモジュールの一部になります。 次のコード例では、複数のモジュールを含むコード ファイルを示します。 コンパイラが暗黙的にという名前の最上位レベルのモジュールを作成します`Multiplemodules`、および`MyModule1`と`MyModule2`その最上位レベルのモジュール内で入れ子になっています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

プロジェクトで、または 1 つのコンパイルで複数のファイルがある場合、またはライブラリを構築している場合は、名前空間の宣言またはファイルの上部にあるモジュールの宣言を含める必要があります。 のみ、F# コンパイラは暗黙的にモジュール名を決定し、プロジェクトやコンパイルのコマンド ラインに 1 つのみのファイルは、アプリケーションを作成するときにします。

*アクセシビリティ修飾子*、次のいずれかを指定できます: `public`、 `private`、`internal`します。 詳細については、「[Access Control](access-control.md)」(アクセス制御) を参照してください。 既定値はパブリックです。

## <a name="referencing-code-in-modules"></a>モジュール内のコードを参照します。

関数、型、および値を別のモジュールから参照する場合は、修飾名を使用いずれかまたはモジュールを開く必要があります。 修飾名を使用する場合は、名前空間、モジュール、および対象となるプログラム要素の識別子を指定する必要があります。 次のようにドット (.) で修飾パスの各部分を分離します。

`Namespace1.Namespace2.ModuleName.Identifier`

モジュールまたは 1 つ以上のコードを簡略化する名前空間を開くことができます。 開く名前空間とモジュールの詳細については、[インポート宣言。`open`キーワード](import-declarations-the-open-keyword.md)を参照してください。

次のコード例では、ファイルの末尾までのすべてのコードを含む最上位レベルのモジュールを示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

同じプロジェクト内の別のファイルからこのコードを使用するには、修飾名を使用するか、または開く、モジュール、関数を使用する前に次の例に示すように。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>入れ子になったモジュール

モジュールは、入れ子にすることができます。 内部のモジュールは、外側のモジュール宣言のない新しいモジュール、内側のモジュールがいることを示すに関してインデントする必要があります。 たとえば、次の 2 つの例を比較します。 モジュール`Z`次のコードの内部のモジュールです。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

モジュールが、`Z`モジュールに兄弟`Y`次のコード。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
モジュール`Z`モジュール内の他の宣言に関してはインデントされませんので、次のコードでは、兄弟のモジュールも`Y`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
最後に、外側のモジュールは、宣言されておらず、別のモジュール宣言によってすぐにその後に場合、新しいモジュール宣言は、内部のモジュールと見なされますが、コンパイラ警告が表示するかどうか、2 番目のモジュールの定義より遠くはインデントされません、まずは。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
警告を回避するには、内部のモジュールをインデントします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
ファイルの 1 つの外部モジュール内のすべてのコードがし、内部のモジュールが必要な場合は、外側のモジュールには、等号が必要としないと、インデントを設定するのには、外側のモジュールである任意の内部モジュールを宣言を含む、宣言することはありません。 内部のモジュール宣言内で宣言は、インデントを設定する必要は。 次のコードでは、このケースを示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>再帰的なモジュール

F#4.1 には、再帰的に相互に含まれているすべてのコードでは、モジュールの概念が導入されています。  使用してこれには`module rec`します。  使用`module rec`されない型とモジュール間の相互参照コードを記述することでいくつかの問題を軽減することができます。  この例を次に示します。

```fsharp
module rec RecursiveModule =
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

なお、例外`DontSqueezeTheBananaException`とクラス`Banana`両方には、互いを参照してください。  モジュールではさらに、`BananaHelpers`とクラス`Banana`も互いに参照してください。  これは、削除した場合、F# で表現できませんが、`rec`からキーワード、`RecursiveModule`モジュール。

この機能はでも[名前空間](namespaces.md)F# 4.1 とします。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [名前空間](namespaces.md)
- [F#RFC FS-1009 - ファイル内でより大きな範囲経由で相互に参照型とモジュールを許可します。](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)