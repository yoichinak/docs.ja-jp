---
title: Visual Studio での F# の概要します。
description: Visual Studio で F# を使用する方法について説明します。
ms.date: 07/03/2018
ms.openlocfilehash: e573af67a1fc00b0a340f8c73ab1ee0ed2b97810
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082699"
---
# <a name="get-started-with-f-in-visual-studio"></a>Visual Studio での F# の概要します。

F# および Visual F# ツールは、Visual Studio IDE でサポートされます。

作業を開始できることを確認します。 [Visual Studio をインストール F#](install-fsharp.md#install-f-with-visual-studio)します。

## <a name="creating-a-console-application"></a>コンソールアプリケーションの作成

Visual Studio の最も基本的なプロジェクトの1つは、コンソールアプリケーションです。  これを行う方法を次に示します。  Visual Studio が開いたら、次のようにします。

1. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. [プロジェクト] ダイアログで、新規で**テンプレート**、はず**Visual F#** します。  テンプレートを表示するにF#は、これを選択します。

3. **.Net Core コンソールアプリ**または**コンソールアプリ**のいずれかを選択します。

4. 選択、**わかりました**F# プロジェクトを作成するボタン。  ソリューション エクスプ ローラーで F# プロジェクトが表示されます。

## <a name="writing-your-code"></a>コードの記述

まず、コードをいくつか記述してみましょう。  `Program.fs`ファイルが開いていることを確認し、その内容を次の内容に置き換えます。

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

前のコードサンプルでは、と`square`いう名前`x`の入力を受け取り、それを単独で乗算する関数が定義されています。  でF#は[型の推定](../language-reference/type-inference.md)が使用さ`x`れるため、の型を指定する必要はありません。  コンパイラF#は、乗算が有効な型を認識し、が呼び出される方法`x` `square`に基づいて型をに割り当てます。  マウスポインター `square`を合わせると、次のように表示されます。

```fsharp
val square: x:int -> int
```

これは、関数の型シグネチャとして知られています。  次のように読み取ることができます。"Square は、x という整数を受け取り、整数を生成する関数です。  コンパイラ`square`によって型が`int`設定されていることに注意してください。これは、乗算が*すべて*の型のジェネリックではなく、閉じられた型のセット全体でジェネリックであるためです。  選択、F# コンパイラ`int`このポイントが調整されます型シグネチャを呼び出す場合`square`入力の種類などを変える、`float`します。

別の関数`main`が定義されているで装飾するが、 `EntryPoint` F# コンパイラにそのプログラムの実行を指示する属性を開始する必要がありますがあります。  これは、コマンドライン引数をこの関数に渡すことができる他の[C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従い、整数のコードが返され`0`ます (通常は)。

この関数は、 `square` `12`引数を指定して関数を呼び出します。  コンパイラF#は、の`square`型をに`int -> int`割り当てます。これ`int`は、を受け取り、を生成`int`する関数です。  の呼び出し`printfn`は、書式指定文字列を使用する書式設定された印刷関数で、C スタイルのプログラミング言語に似ています。また、書式指定文字列で指定されたパラメーターに対応するパラメーターを使用して、結果と改行を出力します。

## <a name="running-your-code"></a>コードの実行

**Ctrl**+**F5**キーを押してコードを実行し、結果を確認することができます。  これにより、デバッグなしでプログラムが実行され、結果を確認できるようになります。  または、Visual Studio で **[デバッグ]** トップレベルメニュー項目を選択し、 **[デバッグなしで開始]** をクリックします。

次のように、Visual Studio がポップアップ表示されたコンソールウィンドウに出力されます。

```console
12 squared is 144!
```

おめでとうございます!  Visual Studio での初めての F# プロジェクトの作成、F# の関数は、この関数の呼び出しの結果を印刷を記述してプロジェクトを実行し、いくつかの結果を参照してください。

## <a name="next-steps"></a>次の手順

まだインストールしていない場合はチェック アウト、 [F# のツアー](../tour.md)、F# 言語のコア機能の一部が含まれています。  一部の F# の機能の概要が表示され Visual Studio にコピーして実行できる十分なコード サンプルを提供します。  使用できますが、いくつかの優れた外部リソースがあるの紹介、 [F# ガイド](../index.md)します。

## <a name="see-also"></a>関連項目

- [F# のツアー](../tour.md)
- [F#言語リファレンス](../language-reference/index.md)
- [型の推論](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
