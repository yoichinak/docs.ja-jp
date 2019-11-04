---
title: Visual Studioで F# をはじめよう
description: Visual Studio で F# を使用する方法について説明します。
ms.date: 07/03/2018
ms.openlocfilehash: e573af67a1fc00b0a340f8c73ab1ee0ed2b97810
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082699"
---
# <a name="get-started-with-f-in-visual-studio"></a>Visual Studioで F# をはじめよう

F# および Visual F# ツールは、Visual Studio IDE でサポートされます。

作業を開始するにあたり、[F# で Visual Studio がインストール](install-fsharp.md#install-f-with-visual-studio) されていることを確認してください。

## <a name="creating-a-console-application"></a>コンソールアプリケーションの作成

Visual Studio の最も基本的なプロジェクトの 1 つは、コンソールアプリケーションです。  これを行う方法を次に示します。  Visual Studio を開いたら、次のようにします。

1. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. [プロジェクト] ダイアログで、新規で**テンプレート**、はず**Visual F#** します。  テンプレートを表示するにF#は、これを選択します。

3. **.Net Core コンソールアプリ**または**コンソールアプリ**のいずれかを選択します。

4. **OK** ボタンを選択して、F# プロジェクトを作成します。  ソリューション エクスプ ローラーに F# プロジェクトが表示されます。

## <a name="writing-your-code"></a>コードの記述

まず、コードをいくつか記述してみましょう。  `Program.fs`ファイルが開いていることを確認し、その内容を次の内容に置き換えます。

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

前のコードサンプルでは、`x`という名前の入力を受け取り、それを単独で乗算する関数`square`が定義されています。  F#は[型推定](../language-reference/type-inference.md) を行うため、`x`の型を指定する必要はありません。  F# コンパイラは乗算が有効な型を認識し、`square`の呼び出しに基づいて`x` に型を割り当てます。  マウスポインターを`square`に合わせると、次のように表示されます。

```fsharp
val square: x:int -> int
```

これは、関数の型シグネチャと呼ばれるものです。  次のように読み取ることができます。「Square は x という名前の整数を取り、整数を生成する関数」と読むことができます。  コンパイラは`square`に`int`型を設定していること注意してください。  選択、F# コンパイラ`int`このポイントが調整されます型シグネチャを呼び出す場合`square`入力の種類などを変える、`float`します。

別の関数`main`が定義されています。これは`EntryPoint`属性で装飾されていますが、プログラムの実行をそこから開始するように F# コンパイラーに指示しています。  これは、コマンドライン引数をこの関数に渡すことができる他の[C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従い、整数のコードが返され`0`ます (通常は)。

この関数は、引数`12`で `square`関数を呼び出します。  次に、F# コンパイラは、 `square`の型を`int -> int`（つまり、 `int`を受け取り`int`を生成する関数）に割り当てます。  `printfn`は C スタイルのプログラミング言語に似たフォーマット文字列と、フォーマット文字列で指定されたパラメータに対応するパラメータを用いる整形出力関数で、結果と改行を出力します。

## <a name="running-your-code"></a>コードの実行

**Ctrl**+**F5**キーを押してコードを実行し、結果を確認することができます。  これにより、デバッグなしでプログラムが実行され、結果を確認できるようになります。  または、Visual Studio で **[デバッグ]** トップレベルメニュー項目を選択し、 **[デバッグなしで開始]** をクリックします。

次のように、Visual Studio がポップアップ表示されたコンソールウィンドウに出力されます。

```console
12 squared is 144!
```

おめでとうございます!  Visual Studioで最初の F# プロジェクトを作成し、その関数の呼び出し結果を出力する F# 関数を作成し、プロジェクトを実行して結果を確認しました。

## <a name="next-steps"></a>次のステップ

まだインストールしていない場合は、F# 言語のコア機能の一部をカバーする[F# のツアー](../tour.md) をご覧ください。  F# の機能の一部の概要を示し、Visual Studio にコピーして実行できる十分なコード サンプルを提供します。  [F# ガイド](../index.md) で紹介されている、優れた外部リソースもあります。

## <a name="see-also"></a>関連項目

- [F# のツアー](../tour.md)
- [F#言語リファレンス](../language-reference/index.md)
- [型推論](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
