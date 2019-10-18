---
title: Visual Studio Code での F# の概要
description: Visual Studio Code および ionide の概要のプラグインのスイートで F# を使用する方法について説明します。
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082984"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio Code で F# を使い始める

[Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)を使用して[Visual Studio Code](https://code.visualstudio.com)でF#を記述すると、IntelliSense と基本的なコードリファクタリングを使用して、優れたクロスプラットフォームで軽量の統合開発環境 (IDE) エクスペリエンスを実現できます。 プラグインの詳細については、 [Ionide.io](http://ionide.io)を参照してください。

まず、[F# および ionide の概要プラグインが正しくインストールされている](install-fsharp.md#install-f-with-visual-studio-code)ことを確認してください。

> [!NOTE]
> Ionide は、クロスプラットフォームの互換性の問題が発生する可能性がある dotnet core ではなく .NET Framework F#プロジェクトを生成します。 **Linux**または**OSX**でを実行している場合は、[コマンドラインツール](get-started-command-line.md)を使用することをお勧めします。

## <a name="creating-your-first-project-with-ionide"></a>Ionide を使用した最初のプロジェクトの作成

新しい F# プロジェクトを作成するには、新しいフォルダで Visual Studio コードを開きます (任意の名前を付けることができます)。

次に、コマンドパレット (**View > コマンドパレット**) を開き、次のように入力します。

```console
> F# new project
```

これは、[FORGE](https://github.com/fsharp-editing/Forge)プロジェクトから提供されています。

> [!NOTE]
> テンプレートオプションが表示されない場合は、コマンドパレットで次のコマンドを実行して`>F#: Refresh Project Templates`テンプレートを更新してみてください。

**Enter**を押して、「F＃：New Project」を選択します。これにより、次の手順に進みます。これは、プロジェクトテンプレートを選択するためのものです。

テンプレートを選択し、 **Enter キー**を押します。 `classlib`

次に、プロジェクトを作成するディレクトリを選択します。 空白のままにすると、カレントディレクトリが使用されます。

最後にプロジェクト名を指定します。 F#ではプロジェクト名として[Pascal](http://c2.com/cgi/wiki?PascalCase)形式を使用します。 この記事では、`ClassLibraryDemo`を名前として使用します。 プロジェクトに使用する名前を入力したら、 **Enter キー**を押します。

前の手順に従った場合は、左側に Visual Studio Code ワークスペースが表示され、次のように表示されます。

1. `ClassLibraryDemo`フォルダーの下にあるF#プロジェクト自体。
2. [`Paket`](https://fsprojects.github.io/Paket/)を介してパッケージを追加するための適切なディレクトリ構造。
3. [`FAKE`](https://fsharp.github.io/FAKE/)を使用したクロスプラットフォーム ビルド スクリプト。
4. パッケージを取得して依存関係を解決できる`paket.exe`実行可能ファイル。
5. このプロジェクトをGitベースのソース管理に追加する場合は、 `.gitignore`ファイル。

## <a name="writing-some-code"></a>コードの記述

*Classlibrarydemo*フォルダーを開きます。  次のファイルが表示されます。

1. `ClassLibraryDemo.fs`、クラスが定義されている F# 実装ファイル。
2. `ClassLibraryDemo.fsproj`、このプロジェクトのビルドに使用される F# プロジェクト ファイルです。
3. `Script.fsx`、ソース ファイルを読み込む F# スクリプト ファイル。
4. `paket.references`は、プロジェクトの依存関係を指定するパケットファイルです。

`Script.fsx`を開き、最後に次のコードを追加します。

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

この関数は、単語を[Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)の形式に変換します。 次の手順では、F# Interactive (FSI) を使用して評価します。

関数全体をハイライト表示します (長さは11 行である必要があります)。 ハイライト表示されたら、 **Alt**キーを押しながら**Enter**キーを押します。 ウィンドウのポップアップが表示され、次のように表示されます。

![Ionide の概要での F# Interactive の出力例](./media/getting-started-vscode/vscode-fsi.png)

これは次の3つのことを行いました。

1. FSI.EXE プロセスを開始しました。
2. FSI.EXE プロセスでハイライト表示したコードが送信されました。
3. FSI.EXE プロセスは、送信したコードを評価しました。

送信したのは[関数](../language-reference/functions/index.md)だったので、fsi.exe を使用してその関数を呼び出すことができます! 対話型ウィンドウで、次のように入力します。

```fsharp
toPigLatin "banana";;
```

次の結果が表示されます。

```fsharp
val it : string = "ananabay"
```

では、最初の文字として母音を試してみましょう。 次のように入力します。

```fsharp
toPigLatin "apple";;
```

次の結果が表示されます。

```fsharp
val it : string = "appleyay"
```

関数が想定どおりに動作しているようです。 おめでとうございます、あなたはちょうどVisual Studioコードであなたの最初のF#関数を書き、FSIでそれを評価しました!

> [!NOTE]
> ご存知かもしれませんが、FSI.EXE の行は`;;`で終了します。 これは、FSI.EXE で複数の行を入力できるためです。 最後`;;`のは、コードが終了したことを fsi.exe に通知します。

## <a name="explaining-the-code"></a>コードの説明

実際にコードが何をしているかわからない場合は、次の手順を実行します。

ご覧のように、 `toPigLatin`は単語を入力として受け取り、その単語の Pig 表現に変換する関数です。 この規則は次のとおりです。

単語の最初の文字が母音で始まる場合は、単語の末尾に "yay" を追加します。 母音で始まらない場合は、その最初の文字を単語の末尾に移動し、それに "ay" を追加します。

FSI.EXE では、次のことに気づいたかもしれません。

```fsharp
val toPigLatin : word:string -> string
```

これは、 `toPigLatin` `string`を入力として受け取り (と呼び`word`ます)、別`string`のを返す関数であることを示します。これは[関数の型シグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/)と呼ばれ、F# コードの基本的な部分を理解するための重要なF#の基本的部分です。 Visual Studio Code でカーソルを関数に合わせると、この点にも注意してください。

関数の本体には、次の2つの異なる部分があります。

1. 指定した文字(`isVowel`)が、指定されたパターンのいずれかと一致するかどうかをチェックすることによって、特定の文字 (`c`)が母音であるかどうかを判断する内部[関数。](../language-reference/pattern-matching.md)

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. 最初の文字が母音であるかどうかを確認し、最初の文字が母音であるかどうかに基づいて、入力文字から戻り値を構築する[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)式。

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

そのため、 `toPigLatin`のフローは次のようになります。

入力単語の最初の文字が母音であるかどうかを確認します。 そうである場合は、単語の末尾に "yay" を付加します。 それ以外の場合は、最初の文字を単語の末尾に移動し、それに "ay" を追加します。

この点については最後に説明します。他の多くの言語とは異なり、関数から戻る明示的な命令はありません。 これは、 F#が式ベースであり、関数本体の最後の式が戻り値であるためです。 `if..then..else`はそれ自体が式であるため、`then`ブロックの本体または`else`ブロックの本体の値が返されます。

## <a name="moving-your-script-code-into-the-implementation-file"></a>実装ファイルへのスクリプトコードの移動

この記事の前のセクションには、F# コードの記述の一般的な最初の手順を示しました。 最初に関数を記述して、FSI 使用して対話的に実行します。 これは REPL ドリブン開発と呼ばれます。 [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)は "Read Evaluate-Print Loop" を表します。 何かが機能するまで機能を試すのに最適な方法です。

REPL 駆動型開発の次の手順は、作業コードを F# 実装ファイルに移動することです。その後、F# コンパイラによって実行可能なアセンブリにコンパイルできます。

まず、`ClassLibraryDemo.fs`を開きます。  いくつかのコードが既に存在していることがわかります。先に進み、クラス定義を削除しますが、必ず[`namespace`](../language-reference/namespaces.md)宣言は先頭に残しておいてください。

次に、`PigLatin`という新しい[`module`](../language-reference/modules.md)を作成し、`toPigLatin`関数を次のようにコピーします。

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

そして、`Script.fsx`ファイルをもう一度開き、`toPigLatin`関数全体を削除します。ただし、ファイルには次の2行を必ず残してください。

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

両方のテキスト行を選択し、Alt + Enter キーを押して、FSI.EXE でこれらの行を実行します。 これらの操作により、Pig Latin ライブラリの内容が fsi.exe プロセスと`open` `ClassLibraryDemo`名前空間に読み込まれ、機能にアクセスできるようになります。

次に、[fsi.exe] ウィンドウで、前に定義`PigLatin`したモジュールを使用して関数を呼び出します。

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

成功！ 以前と同じ結果が得られますが、現在はF＃実装ファイルからロードされています。 ここでの主な違いは、F＃ソースファイルがFSIだけでなく、どこでも実行できるアセンブリにコンパイルされることです。

## <a name="summary"></a>まとめ

この記事では、次のことを学習しました。

1. Ionide を使用して Visual Studio Code を設定する方法について説明します。
2. Ionide を使用して初めての F# プロジェクトを作成する方法。
3. F# スクリプトを使用して、ionide で初めての F# 関数を記述し、FSI で実行する方法。
4. スクリプト コードを F# ソースに移行し、そのコードを FSI から呼び出す方法。

これで、Visual Studio コードと Ionide を使用して、より多くの F# コードを記述できるようになりました。

## <a name="troubleshooting"></a>トラブルシューティング

発生する可能性のある特定の問題をトラブルシューティングする方法を次にします。

1. Ionide のコード編集機能を取得するには、F# ファイルをディスクに保存し、Visual Studio コード ワークスペースで開いているフォルダ内に保存する必要があります
2. システムに変更を加えた場合、または Visual Studio コードを開いた Ionide の前提条件をインストールした場合は、Visual Studio Code を再起動します。
3. 完全修飾パスなしでコマンドラインから F# コンパイラと F# 対話式を使用できることを確認します。これを行うには、F# コンパイラのコマンドラインに`fsc`を入力し、Windows の Visual F# ツールの`fsi`または`fsharpi`をそれぞれ入力し、Mac/Linux 上のモノラルを入力します。
4. プロジェクトディレクトリに無効な文字が含まれていると、Ionide が機能しない可能性があります。この場合は、プロジェクトディレクトリの名前を変更します。
5. Ionide コマンドがいずれも動作していない場合は、 [Visual Studio Code キーバインド](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)を調べて、誤って上書きされていないかどうかを確認します。
6. Ionideがマシン上で壊れていて、上記のいずれも問題を解決していない場合は、コンピュータの`ionide-fsharp`ディレクトリを削除して、プラグインスイートを再インストールしてみてください。

Ionideは、F# コミュニティのメンバーによって構築され、維持されるオープンソースプロジェクトです。問題を報告し、[Ionide-vscode に投稿してください。Fsharp.core GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)。

報告する問題がある場合は、「[ログを取得する](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)」の手順に従って、問題を報告してください。

[Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project)チャネルの Ionide 開発者と F# コミュニティからさらなる支援を求めることもできます。

## <a name="next-steps"></a>次の手順

F# と言語の機能の詳細については、[F# のツアー](../tour.md) を参照してください。
