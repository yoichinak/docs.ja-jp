---
title: Visual Studio for MacでF＃を使い始める
description: を Visual Studio for Mac と共F#に使用する方法について説明します。
ms.date: 07/03/2018
ms.openlocfilehash: d3604178f93cf17d21f25b09084be7e7977378b5
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082979"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Visual Studio for MacでF＃を使い始める

F＃およびVisual F＃ツールは、Visual Studio for Mac IDEでサポートされています。 [Visual Studio for Mac がインストール](install-fsharp.md#install-f-with-visual-studio-for-mac)されていることを確認して下さい。

## <a name="creating-a-console-application"></a>コンソールアプリケーションの作成

Visual Studio for Mac の最も基本的なプロジェクトの1つは、コンソールアプリケーションです。  これを行う方法を次に示します。  Visual Studio for Mac が開いたら、次のようになります。

1. **[ファイル]** メニューの **[新しいソリューション]** をポイントします。

2. [新しいプロジェクト] ダイアログには、コンソールアプリケーションに2つの異なるテンプレートがあります。  .NET Framework をターゲットとする > .NET の下に1つあります。  その他のテンプレートは .net core > アプリの下にあり、.NET Core を対象としています。  どちらのテンプレートも、この記事の目的で機能します。

3. コンソール アプリを変更 (C#) F# に必要な場合。  **[次へ]** ボタンをクリックして先に進みます。  

4. プロジェクトに名前を付け、アプリに必要なオプションを選択します。  プレビューウィンドウには、選択したオプションに基づいて作成されるディレクトリ構造が表示されます。  

5. **[作成]** をクリックします。  ソリューション エクスプ ローラーで F# プロジェクトが表示されます。

## <a name="writing-your-code"></a>コードの記述

まず、コードをいくつか記述してみましょう。  `Program.fs`ファイルが開いていることを確認し、その内容を次の内容に置き換えます。

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

前のコードサンプルでは、と`square`いう名前`x`の入力を受け取り、それを単独で乗算する関数が定義されています。  でF#は[型の推定](../language-reference/type-inference.md)が使用さ`x`れるため、の型を指定する必要はありません。  コンパイラF#は、乗算が有効な型を認識し、が呼び出される方法`x` `square`に基づいて型をに割り当てます。  マウスポインター `square`を合わせると、次のように表示されます。

```console
val square: x:int -> int
```

これは、関数の型シグネチャとして知られています。  次のように読み取ることができます。"Square は、x という整数を受け取り、整数を生成する関数です。  コンパイラ`square`によって型が`int`設定されていることに注意してください。これは、乗算が*すべて*の型のジェネリックではなく、閉じられた型のセット全体でジェネリックであるためです。  選択、F# コンパイラ`int`このポイントが調整されます型シグネチャを呼び出す場合`square`入力の種類などを変える、`float`します。

別の関数`main`が定義されているで装飾するが、 `EntryPoint` F# コンパイラにそのプログラムの実行を指示する属性を開始する必要がありますがあります。  これは、コマンドライン引数をこの関数に渡すことができる他の[C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従い、整数のコードが返され`0`ます (通常は)。

この関数は、 `square` `12`引数を指定して関数を呼び出します。  コンパイラF#は、の`square`型をに`int -> int`割り当てます。これ`int`は、を受け取り、を生成`int`する関数です。  の呼び出し`printfn`は、書式指定文字列を使用する書式設定された印刷関数で、C スタイルのプログラミング言語に似ています。また、書式指定文字列で指定されたパラメーターに対応するパラメーターを使用して、結果と改行を出力します。

## <a name="running-your-code"></a>コードの実行

上部のメニューから **[実行]** をクリックし、 **[デバッグなしで開始]** をクリックして、コードを実行し、結果を確認できます。  これにより、デバッグなしでプログラムが実行され、結果を確認できるようになります。

コンソールウィンドウに次の出力が表示され、Visual Studio for Mac ポップアップされます。

```console
12 squared is 144!
```

おめでとうございます!  Mac 用の Visual Studio で初めての F# プロジェクトを作成、F# の関数は、この関数の呼び出しの結果を印刷を記述してプロジェクトを実行し、いくつかの結果を参照してください。

## <a name="using-f-interactive"></a>対話型F#の使用

F# 対話型ウィンドウは、最適な機能では、Visual F# の Visual Studio for Mac ツールの 1 つ。  このメソッドを使用すると、コードを呼び出して結果を対話形式で確認できるプロセスにコードを送信できます。

使用を開始するには、 `square`コードで定義されている関数を強調表示します。  次に、トップレベルメニューの **[編集]** をクリックします。  次に選択**選択範囲を F# Interactive に送信**します。  これには、F# 対話型ウィンドウで、コードが実行されます。  または、選択範囲を右クリックし、選択**選択範囲を F# Interactive に送信**します。  F#対話型ウィンドウが表示され、次のようなウィンドウが表示されます。

```console
>

val square : x:int -> int

>
```

これは、関数をポイントした`square`ときに前に見た関数の関数シグネチャと同じです。  `square`が F# Interactive プロセスで定義されている、ここではさまざまな値を呼び出すことができます。

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

これにより、関数が実行され、結果が`it`新しい名前にバインドされ、の`it`型と値が表示されます。  各行は、で`;;`終了する必要があることに注意してください。  これは、どのように F# Interactive を知っている、関数呼び出しが完了するとします。  対話型でF#新しい関数を定義することもできます。

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上のでは新しい関数`isOdd`が定義されています。これはを`int`受け取り、それが奇数かどうかを確認します。  この関数を呼び出すと、異なる入力で何が返されるかを確認できます。  関数呼び出しの中で関数を呼び出すことができます。

```console
> isOdd (square 15);;
val it : bool = true
```

[パイプ転送演算子](../language-reference/symbol-and-operator-reference/index.md)を使用して、値を次の2つの関数にパイプライン処理することもできます。

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

パイプ転送演算子などの詳細については、以降のチュートリアルで説明します。

ここでは、F# Interactive で何ができるかを大まかに取り上げているだけです。  詳細については、[F# を使用した対話型プログラミング](../tutorials/fsharp-interactive/index.md) を参照してください。

## <a name="next-steps"></a>次の手順

まだインストールしていない場合はチェック アウト、 [F# のツアー](../tour.md)、F# 言語のコア機能の一部が含まれています。  一部の F# の機能の概要が表示され Visual Studio for Mac にコピーして実行できる十分なコード サンプルを提供します。  使用できますが、いくつかの優れた外部リソースがあるの紹介、 [F# ガイド](../index.md)します。

## <a name="see-also"></a>関連項目

- [Visual F#](../index.md)
- [F# のツアー](../tour.md)
- [F#言語リファレンス](../language-reference/index.md)
- [型の推論](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
