---
title: Visual Studio Code で F# をはじめる
description: Visual Studio Code および ionide の概要のプラグインのスイートで F# を使用する方法について説明します。
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082984"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio Code で F# をはじめる

[Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) を使用して [Visual Studio Code](https://code.visualstudio.com)で F# を記述すると、IntelliSense と基本的なコードリファクタリングを使用して、優れたクロスプラットフォームで軽量の統合開発環境 (IDE) エクスペリエンスを実現できます。 プラグインの詳細については、 [Ionide.io](http://ionide.io) を参照してください。

作業を開始できることを確認します。 [F# および ionide の概要プラグインが正しくインストールされている](install-fsharp.md#install-f-with-visual-studio-code)します。

> [!NOTE]
> Ionide は dotnet coreではなく、クロスプラットフォームでの互換性の問題が発生する可能性がある .NET Framework プロジェクトを生成します。 **Linux** または **OSX** を実行している場合は、[コマンドラインツール](get-started-command-line.md)を使用することをお勧めします。

## <a name="creating-your-first-project-with-ionide"></a>Ionide で最初のプロジェクトを生成する

新しい F# プロジェクトを作成するには、新しいフォルダーで Visual Studio Code を開きます(任意の名前をつけることができます)。

次に、コマンドパレット (**View > コマンドパレット**) を開き、次のように入力します。

```console
> F# new project
```

これは [FORGE](https://github.com/fsharp-editing/Forge) プロジェクトによって提供されます。

> [!NOTE]
> テンプレートオプションが表示されない場合は、コマンドパレットで次のコマンドを実行して`>F#: Refresh Project Templates`テンプレートを更新してみてください。

F#:**Enter キー**を押して、新しいプロジェクトを作成します。 これにより、次の手順に進みます。これは、プロジェクトテンプレートを選択するためのものです。

テンプレートを選択し、 **Enter キー**を押します。 `classlib`

次に、プロジェクトを作成するディレクトリを選択します。 空白のままにすると、現在のディレクトリを使用します。

最後の手順でプロジェクトに名前を指定します。 F#プロジェクト名として[Pascal](http://c2.com/cgi/wiki?PascalCase)形式を使用します。 この記事で`ClassLibraryDemo`は、を名前として使用します。 プロジェクトに使用する名前を入力したら、 **Enter キー**を押します。

これらの手順に従えば、左側に Visual Studio Code ワークスペースが表示され、次のように表示されます。

1. `ClassLibraryDemo`フォルダーの下にある F# プロジェクトそのもの。
2. [`Paket`](https://fsprojects.github.io/Paket/) を介してパッケージを追加するための正しいディレクトリ構造。
3. [`FAKE`](https://fsharp.github.io/FAKE/) を使用したクロスプラットフォームのビルドスクリプト。
4. パッケージをフェッチし、依存関係を解決できる実行可能ファイル。`paket.exe`
5. このプロジェクトを Git ベースのソース管理に追加する場合は、`.gitignore`ファイル。

## <a name="writing-some-code"></a>コードの記述

*Classlibrarydemo*フォルダーを開きます。  次のファイルが表示されます。

1. `ClassLibraryDemo.fs`、クラスが定義された F# 実装ファイル。
2. `ClassLibraryDemo.fsproj`、このプロジェクトをビルドするために使用される F# プロジェクトファイル。
3. `Script.fsx`、ソース ファイルを読み込む F# スクリプトファイル。
4. `paket.references`、プロジェクトの依存関係を指定する Packet ファイル。

`Script.fsx`を開き、最後に次のコードを追加します。

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

この関数は、単語を [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin) 形式に変換します。 次の手順では、F# インタラクティブ(FSI) を使用して評価します。

関数全体をハイライト表示します (11 行の長さである必要があります)。 ハイライト表示されたら、 **Alt** キーを押しながら **Enter** キーを押します。 下にウィンドウがポップアップ表示され、次のように表示されます。

![Ionide の概要での F# Interactive の出力例](./media/getting-started-vscode/vscode-fsi.png)

これは次の 3 つのことを行いました。

1. FSI.EXE プロセスを開始しました。
2. FSI.EXE プロセスでハイライト表示したコードが送信されました。
3. FSI.EXE プロセスは、送信したコードを評価しました。

送信したのは[関数](../language-reference/functions/index.md)だったので、fsi.exe! を使用してその関数を呼び出すことができるようになりました。 対話型ウィンドウで、次のように入力します。

```fsharp
toPigLatin "banana";;
```

次の結果が表示されます。

```fsharp
val it : string = "ananabay"
```

では、母音を最初の文字として試してみましょう。 次のように入力します。

```fsharp
toPigLatin "apple";;
```

次の結果が表示されます。

```fsharp
val it : string = "appleyay"
```

関数が期待どおりに動作しているようです。 Visual Studio Code で最初の F# 関数を作成し、FSI で評価しました。

> [!NOTE]
> ご存知かもしれませんが、FSI の行は`;;`で終了します。 これは、FSI で複数の行を入力できるためです。 最後`;;`は、コードが終了したことを FSI に知らせます。

## <a name="explaining-the-code"></a>コードの説明

実際にコードが何をしているかわからない場合は、次のステップで説明します。

ご覧のように、`toPigLatin`は単語を入力として受け取り、その単語を Pig 表現に変換する関数です。 この規則は次のとおりです。

単語の最初の文字が母音で始まる場合は、単語の末尾に "yay" を追加します。 母音で始まらない場合は、その最初の文字を単語の末尾に移動し、それに "ay" を追加します。

FSI で以下の行があることに気づいたと思います。

```fsharp
val toPigLatin : word:string -> string
```

これは、`toPigLatin`が`string`を入力として受け取り (`word`と呼ぶ) 、別の`string`を返す関数であることを示します。 これは[関数の型シグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/) と呼ばれ、F# の基本的な部分でコードを理解する鍵となるものです。 Visual Studio Code で関数名をクリックした場合もこれが表示されることに気づくと思います。

関数の本体には、次の 2 つの異なる部分があります。

1. 指定した文字 ( `isVowel`) が、指定されたパターン`c`のいずれかと一致するかどうかをチェックすることによって、特定の文字 () が母音であるかどうかを判断する内部[関数。](../language-reference/pattern-matching.md)

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. 最初の文字が母音であるかどうかを確認し、最初の文字が母音であるかどうかに基づいて、入力文字から戻り値を構築する[式。`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

したがって、 `toPigLatin`のフローは次の通りです。

入力単語の最初の文字が母音であるかどうかを確認します。 の場合は、単語の末尾に "yay" を付加します。 それ以外の場合は、最初の文字を単語の末尾に移動し、それに "ay" を追加します。

この点については最後に説明します。他の多くの言語とは異なり、関数から戻る明示的な命令はありません。 これは、 F# が式ベースであり、関数本体の最後の式が戻り値であるためです。 `if..then..else`はそれ自体が式であるため、`then`ブロックの本体または`else`ブロックの本体の値が返されます。

## <a name="moving-your-script-code-into-the-implementation-file"></a>スクリプトコードを実装ファイルへ移動する

この記事では、前のセクションには、F# コードの記述の一般的な最初の手順が示されています。 最初の関数の記述と、FSI 使用して対話的に実行します。 これは REPL ドリブン開発と呼ばれます。 [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)は "Read Evaluate-Print Loop" を表します。 機能を使用するには、機能を試してみることをお勧めします。

REPL 駆動型開発の次に、作業コードを F# 実装ファイルに移動します。 その後、F# コンパイラによって実行可能なアセンブリにコンパイルする事ができます。

まず、`ClassLibraryDemo.fs`を開きます。  いくつかのコードが既にあることがわかるでしょう。 先に進み、クラス定義を削除しますが、[`namespace`](../language-reference/namespaces.md) 宣言は上部に残しておいてください。

次に、`PigLatin`という新しい[`module`](../language-reference/modules.md) を作成し、`toPigLatin`関数を次のようにコピーします。

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

そして、`Script.fsx`ファイルをもう一度開き、`toPigLatin`関数全体を削除します。ただし、ファイルには次の 2 行を必ず残してください。

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

両方のテキスト行を選択し、Alt + Enter キーを押して、FSI でこれらの行を実行します。 これにより、Pig Latin ライブラリの内容が FSI プロセスに読み込まれ、`ClassLibraryDemo`名前空間を`open`することでその機能にアクセスできるようになります。

次に、[FSI] ウィンドウで前に定義した`PigLatin`モジュールの関数を呼び出します。

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

正常に完了 取得する前に、同じ結果が、F# 実装ファイルから読み込まれるようになりました。 ここでの主な違いは、F# ソース ファイルが FSI 内だけでなく、どこにでも実行できるアセンブリにコンパイルされます。

## <a name="summary"></a>まとめ

この記事では、次のことを学習しました。

1. Ionide を使用して Visual Studio Code を設定する方法
2. Ionide で初めての F# プロジェクトを作成する方法
3. Ionide で初めての F# 関数を記述し、FSI で実行する方法
4. スクリプトから F# ソースコードへ移行し、FSI からそのコードを呼び出す方法

これで、Visual Studio Code と Ionide を使用してより多くの F# コードを作成できるようになりました。

## <a name="troubleshooting"></a>トラブルシューティング

発生する可能性のある特定の問題をトラブルシューティングする方法を次に示します。

1. Ionide の概要の編集機能をコードを取得するには、F# ファイルはディスク、および Visual Studio Code ワークスペースで開いているフォルダー内に保存する必要があります。
2. システムに変更を加えた場合、または Visual Studio Code を開いた状態で Ionide の前提条件をインストールした場合は、Visual Studio Code を再起動します。
3. 完全修飾パスなしでコマンドラインから F# コンパイラと F# 対話式を使用できることを確認します。 これを行うには、F# コンパイラのコマンドラインに`fsc`を入力し、Windows の Visual F# ツールの`fsi`または`fsharpi`をそれぞれ入力し、Mac/Linux 上のモノラルを入力します。
4. プロジェクトディレクトリに無効な文字が含まれていると、Ionide が機能しない可能性があります。  この場合は、プロジェクトディレクトリの名前を変更します。
5. Ionide コマンドがいずれも動作しない場合、 [Visual Studio Code キーバインド](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) を調べて、誤って上書きされていないかどうかを確認します。
6. Ionide がコンピューター上で破損していて、上記のいずれも問題を解決しな場合、コンピューター上の`ionide-fsharp`ディレクトリを削除し、プラグインスイートを再インストールしてみてください。

Ionide の概要とは、構築および F# コミュニティのメンバーによって管理されるオープン ソース プロジェクトです。 問題を報告して、 [Ionide-vscode に投稿してください。Fsharp.core GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)。

何か問題が発生した場合は、[問題発生時のログ取得手順](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting) に従って下さい。

[Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project) で、Ionide 開発者および F# コミュニティからさらに助けを得ることができます。

## <a name="next-steps"></a>次のステップ

F# と言語機能の詳細について学ぶには、[F# のツアー](../tour.md) を参照してください。
