---
title: Visual Studio での F# の概要します。
description: Visual Studio で F# を使用する方法について説明します。
ms.date: 07/03/2018
ms.openlocfilehash: 020e5d32b3aa5d5a2195c19d70d8fe684fbd56ef
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331911"
---
# <a name="get-started-with-f-in-visual-studio"></a>Visual Studio での F# の概要します。

F# および Visual F# ツールは、Visual Studio IDE でサポートされます。

作業を開始できることを確認します。 [Visual Studio をインストール F#](install-fsharp.md#install-f-with-visual-studio)します。

## <a name="creating-a-console-application"></a>コンソール アプリケーションを作成します。

Visual Studio で最も基本的なプロジェクトの 1 つは、コンソール アプリケーションです。  これを行う方法を次に示します。  Visual Studio が開くです。

1. **ファイル**メニューで、**新規**を選び、**プロジェクト**します。

2. [プロジェクト] ダイアログで、新規で**テンプレート**、はず**Visual F#** します。  選択すると、表示、F#テンプレート。

3. いずれかを選択 **.NET Core コンソール アプリ**または**コンソール アプリ**します。

3. 選択、**わかりました**F# プロジェクトを作成するボタン。  ソリューション エクスプ ローラーで F# プロジェクトが表示されます。

## <a name="writing-your-code"></a>コードの記述

最初にいくつかのコードを記述することで開始しましょう。  必ず、`Program.fs`ファイルを開くとを次の内容を置き換えます。

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

上記のコード サンプルは、関数で`square`という名前の入力を受け取るが定義されている`x`単独で乗算します。  F#使用[型の推定](../language-reference/type-inference.md)の型`x`を指定する必要はありません。  F#コンパイラを選択し、乗算が有効な場合は、型を認識する型が割り当てられます`x`方法に基づいて`square`が呼び出されます。  ポインターを合わせる場合`square`次を参照する必要があります。

```
val square: x:int -> int
```

これは、関数の型のシグネチャと呼ばれるものです。  次のように読み取ることができます。"正方形をという名前の整数を受け取る関数は、x と整数が生成されます"。  コンパイラが付けた注`square`、`int`型今のところ、これは、乗算の間でジェネリックがないためには*すべて*型の場合ではなくジェネリック型の間では、します。  選択、F# コンパイラ`int`このポイントが調整されます型シグネチャを呼び出す場合`square`入力の種類などを変える、`float`します。

別の関数`main`が定義されているで装飾するが、 `EntryPoint` F# コンパイラにそのプログラムの実行を指示する属性を開始する必要がありますがあります。  その他の場合と同じ規則に従って[C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)コマンドライン引数は、この関数に渡すことができます、整数コードが返されます (通常`0`)。

このために呼び出される関数では、`square`関数の引数を持つ`12`します。  F#コンパイラの型が割り当てられます`square`する`int -> int`(を受け取る関数は、`int`を生成し、 `int`)。  呼び出し`printfn`を C スタイル プログラミング言語で、書式指定文字列で指定されている対応するパラメーターのような形式の文字列を使用して書式設定された印刷機能は、結果と、新しい行を出力します。

## <a name="running-your-code"></a>コードの実行

コードを実行してキーを押して、結果を参照してください**Ctrl**+**F5**します。  これにより、デバッグを行わずにプログラムを実行し、結果を確認することができます。  または、選択することができます、**デバッグ**トップレベル メニューの Visual Studio 内の項目し、選択**デバッグなしで開始**します。

次の Visual Studio のポップアップをコンソール ウィンドウに出力が表示されます。

```
12 squared is 144!
```

おめでとうございます!  Visual Studio での初めての F# プロジェクトの作成、F# の関数は、この関数の呼び出しの結果を印刷を記述してプロジェクトを実行し、いくつかの結果を参照してください。

## <a name="next-steps"></a>次の手順

まだインストールしていない場合はチェック アウト、 [F# のツアー](../tour.md)、F# 言語のコア機能の一部が含まれています。  一部の F# の機能の概要が表示され Visual Studio にコピーして実行できる十分なコード サンプルを提供します。  使用できますが、いくつかの優れた外部リソースがあるの紹介、 [F# ガイド](../index.md)します。

## <a name="see-also"></a>関連項目

- [ツアーF#](../tour.md)
- [F#言語リファレンス](../language-reference/index.md)
- [型の推論](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
