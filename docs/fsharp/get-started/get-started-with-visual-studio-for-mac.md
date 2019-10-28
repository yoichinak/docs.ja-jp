---
title: Visual Studio for Mac で F＃ をはじめよう
description: を Visual Studio for Mac と共F#に使用する方法について説明します。
ms.date: 07/03/2018
ms.openlocfilehash: d3604178f93cf17d21f25b09084be7e7977378b5
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082979"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Visual Studio for Mac で F＃ をはじめよう

F＃ および Visual F＃ ツールは、Visual Studio for Mac IDE でサポートされています。 [Visual Studio for Mac がインストール](install-fsharp.md#install-f-with-visual-studio-for-mac) されていることを確認してください。

## <a name="creating-a-console-application"></a>コンソールアプリケーションの作成

コンソールアプリケーションは、Visual Studio for Mac の最も基本的なプロジェクトの1つです。  これを行う方法を次に示します。Visual Studio for Mac を開いて、次を実行します。


1. **[ファイル]** メニューの **[新しいソリューション]** をクリックします。

2. **[新しいプロジェクト]** ダイアログには、2 つの異なるコンソールアプリケーション用のテンプレートがあります。一つは .NET Framework をターゲットとするもので、**[その他]** -> **[.NET]** の下にあります。もう一つのテンプレートは **[.NET Core]** -> **[アプリ]** の下にあり、.NET Core を対象としています。どちらのテンプレートを選んでもこの記事の目的に合うはずです。

3. コンソール アプリケーションで、必要であれば C# を F# に変更します。**[次へ]** ボタンをクリックして先に進みます。


4. プロジェクトに名前を付け、アプリに必要なオプションを選択します。プレビュー ウィンドウには、選択したオプションに基づいて作成されるディレクトリ構造が表示されます。  

5. **[作成]** をクリックします。ソリューション エクスプローラーに F# プロジェクトが表示されます。

## <a name="writing-your-code"></a>コードを記述する

まずはコードを記述してみましょう。`Program.fs` ファイルが開いていることを確認し、その内容を次のものに置き換えます。

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

前のコードサンプルでは、`x` という名前の入力を受け取り、それを単独で乗算する関数 `square` が定義されています。F# は[型の推定](../language-reference/type-inference.md)を行うので、`x` の型を指定する必要はありません。F# コンパイラは乗算が有効な型を認識し、`square` が呼び出される方法に基づいて `x` に型を割り当てます。マウス ポインターを `square` に合わせると、次のように表示されます。


```console
val square: x:int -> int
```

これは、関数の型シグネチャと呼ばれるものです。「square は、x という名前の整数を受け取り、整数を生成する関数」と読むことができます。コンパイラがこの時点では `square` に `int` 型を与えていることに注意してください。これは乗算が*あらゆる*型に一般的なのではなく、ある閉じた型の集合に一般的であるためです。F# コンパイラはこの時点で `int` を選択しましたが、例えば `float` といった別の型で `square` を呼び出すと、型シグネチャを調整します。


別の関数 `main` は、`EntryPoint` 属性で修飾され、プログラムの実行をそこから開始することを F# コンパイラに指示するために定義されています。他の [C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従い、コマンド ライン引数をこの関数に渡し、整数値 (通常は `0`) を返す事ができます。


この関数の中で、`square` 関数を引数 `12` で呼び出します。次に F# コンパイラは `square` の型に `int -> int` (つまり `int` を受け取り `int` を生成する関数) を割り当てます。`printfn` 関数は、C スタイルのプログラミング言語に似たフォーマット文字列と、フォーマット文字列にあるパラメータに対応するパラメータを用いて結果と改行を出力する出力関数です。

## <a name="running-your-code"></a>コードを実行する

コードを実行して結果を確認するには、トップレベル メニューから **[実行]** をクリックし、**[デバッグなしで開始]** をクリックします。この場合、デバッグなしでプログラムが実行され、結果を確認できます。

Visual Studio for Mac からコンソール ウィンドウがポップアップされ、以下が出力されます。

```console
12 squared is 144!
```


おめでとうございます! Visual Studio for Mac で初めての F# プロジェクトを作成し、関数の呼び出し結果を出力する F# 関数を作成し、プロジェクトを実行して結果を確認しました。


## <a name="using-f-interactive"></a>F# インタラクティブを使用する

Visual Studio for Mac の Visual F# ツールの最も優れた機能の 1 つは、F# インタラクティブ ウィンドウです。この機能を使用すると、コードを呼び出して結果を確認するという事がインタラクティブに実行できるプロセスにコードを送信できます。

使用を開始するには、まずコードの中の `square` 関数をハイライト表示します。次に、トップ レベル メニューの **[編集]** をクリックします。次に **[選択項目を F# Interactive に送信する]** を選択します。これにより、F# Interactive ウィンドウでコードが実行されます。選択項目を右クリックし、**[選択項目を F# Interactive に送信する]** を選択することもできます。F# Interactive ウィンドウが次のように表示されます。

```console
>

val square : x:int -> int

>
```

前に `square` 関数をポイントしたときに見たのと同じ関数シグネチャが表示されています。`square`が F# Interactive プロセスで定義されるようになったため、さまざまな値を呼び出すことができるようになりました。

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

関数が実行され、結果が `it` という新しい名前にバインドされ、`it` の型と値が表示されます。各行は、`;;` で終了する必要があることに注意してください。これによって関数呼び出しが完了した事を F# Interactive が認識します。F# Interactive で新しい関数を定義することもできます。

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上記では新しい関数 `isOdd` が定義されています。これは `int` を受け取り、それが奇数かどうかを確認します。この関数に様々な入力を与えてどのような値を返すのかを確認する事ができます。また関数呼び出しの中で関数を呼び出すこともできます。

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

ここでは、F# Interactive でできることの一部を取り上げています。詳細については、[F# を使用した対話型プログラミング](../tutorials/fsharp-interactive/index.md)を参照してください。

## <a name="next-steps"></a>次のステップ

まだ確認していない場合は、F# 言語のコア機能の一部をカバーしている [F# のツアー](../tour.md)をご覧ください。F# の一部機能の概要を説明し、Visual Studio for Mac にコピーして実行できる十分なコード サンプルを提供します。[F# ガイド](../index.md)で紹介されている、優れた外部リソースもあります。

## <a name="see-also"></a>関連項目

- [Visual F#](../index.md)
- [F# のツアー](../tour.md)
- [F#言語リファレンス](../language-reference/index.md)
- [型の推論](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
