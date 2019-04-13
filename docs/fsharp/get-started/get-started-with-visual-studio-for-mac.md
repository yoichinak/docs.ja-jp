---
title: Mac 用 Visual Studio での F# の概要します。
description: 使用する方法について説明しますF#で Visual Studio for mac。
ms.date: 07/03/2018
ms.openlocfilehash: a6997f139d7e6c5fdf77878442db0b0b75b3d727
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331872"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Mac 用 Visual Studio での F# の概要します。

F# および Visual F# ツールは、for Mac IDE、Visual Studio でサポートされます。 いる[Visual Studio for Mac がインストールされている](install-fsharp.md#install-f-with-visual-studio-for-mac)します。

## <a name="creating-a-console-application"></a>コンソール アプリケーションを作成します。

Visual Studio for Mac で最も基本的なプロジェクトの 1 つは、コンソール アプリケーションです。  これを行う方法を次に示します。  Visual Studio for Mac が起動したら。

1. **ファイル**メニューで、**新しいソリューション**します。

2. 新しいプロジェクト ダイアログ ボックスで、コンソール アプリケーションの 2 つの異なるテンプレートがあります。  その他の 1 つである .NET、.NET Framework を対象にする-> です。  他のテンプレートは、.NET Core では .NET Core を対象とするアプリ]-> [です。  この記事では、テンプレートのいずれかが動作する必要があります。

3. コンソール アプリを変更 (C#) F# に必要な場合。  選択、**次**前方に移動するボタン。  

4. プロジェクトの名前を入力し、アプリで必要なオプションを選択します。  選択したオプションに基づいて作成されるディレクトリ構造を表示する画面の端にあるプレビュー ウィンドウの通知。  

5. **[作成]** をクリックします。  ソリューション エクスプ ローラーで F# プロジェクトが表示されます。

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

コードを実行し をクリックして結果を表示することができます**実行**トップ レベル メニューからし**デバッグなしで開始**します。  これは、デバッグを行わず、プログラムを実行し、結果を確認することができます。

次の Visual Studio for Mac のポップアップをコンソール ウィンドウに出力が表示されます。

```
12 squared is 144!
```

おめでとうございます!  Mac 用の Visual Studio で初めての F# プロジェクトを作成、F# の関数は、この関数の呼び出しの結果を印刷を記述してプロジェクトを実行し、いくつかの結果を参照してください。

## <a name="using-f-interactive"></a>使用してF#対話型

F# 対話型ウィンドウは、最適な機能では、Visual F# の Visual Studio for Mac ツールの 1 つ。  経由で、そのコードを呼び出すし、対話形式で結果を参照してください、プロセスにコードを送信することができます。

これを使用するには、強調表示、`square`コードで定義された関数。  次に、をクリックして**編集**トップ レベル メニューから。  次に選択**選択範囲を F# Interactive に送信**します。  これには、F# 対話型ウィンドウで、コードが実行されます。  または、選択範囲を右クリックし、選択**選択範囲を F# Interactive に送信**します。  表示する必要があります、F#対話型ウィンドウは次のように表示されます。

```
>

val square : x:int -> int

>
```

同じ関数のシグネチャが表示されます、`square`関数で、関数の上にカーソルを配置するときに表示します。  `square`が F# Interactive プロセスで定義されている、ここではさまざまな値を呼び出すことができます。

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

関数を実行します。 これには、新しい名前に、結果をバインド`it`、種類と値の表示と`it`します。  各行を終了する必要がありますに注意してください。`;;`します。  これは、どのように F# Interactive を知っている、関数呼び出しが完了するとします。  新しい関数を定義することもできますF#Interactive:。

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上の定義を新しい関数の場合、 `isOdd`、受け取り、`int`と奇数かどうかを確認します。  異なる入力で返される内容を表示するには、この関数を呼び出すことができます。  関数呼び出し内の関数を呼び出すことができます。

```
> isOdd (square 15);;
val it : bool = true
```

使用することも、 [- 前方パイプ演算子](../language-reference/symbol-and-operator-reference/index.md)に 2 つの関数に値を渡すパイプラインします。

```
> 15 |> square |> isOdd;;
val it : bool = true
```

以降のチュートリアルでは、順方向のパイプ演算子などがについて説明します。

ここでは、F# Interactive で何ができるかを大まかに取り上げているだけです。  詳細については、[F# を使用した対話型プログラミング](../tutorials/fsharp-interactive/index.md) を参照してください。

## <a name="next-steps"></a>次の手順

まだインストールしていない場合はチェック アウト、 [F# のツアー](../tour.md)、F# 言語のコア機能の一部が含まれています。  一部の F# の機能の概要が表示され Visual Studio for Mac にコピーして実行できる十分なコード サンプルを提供します。  使用できますが、いくつかの優れた外部リソースがあるの紹介、 [F# ガイド](../index.md)します。

## <a name="see-also"></a>関連項目

- [Visual F#](../index.md)
- [ツアーF#](../tour.md)
- [F#言語リファレンス](../language-reference/index.md)
- [型の推論](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
