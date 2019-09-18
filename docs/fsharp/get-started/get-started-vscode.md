---
title: Visual Studio Code での F# の概要します。
description: Visual Studio Code および ionide の概要のプラグインのスイートで F# を使用する方法について説明します。
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082984"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio Code での F# の概要します。

[Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)をF#使用して[Visual Studio Code](https://code.visualstudio.com)に記述すると、IntelliSense と基本的なコードリファクタリングを使用して、優れたクロスプラットフォームで軽量の統合開発環境 (IDE) エクスペリエンスを実現できます。 プラグインの詳細については、 [Ionide.io](http://ionide.io)を参照してください。

作業を開始できることを確認します。 [F# および ionide の概要プラグインが正しくインストールされている](install-fsharp.md#install-f-with-visual-studio-code)します。

> [!NOTE]
> Ionide は、クロスF#プラットフォームの互換性の問題が発生する可能性がある dotnet core ではなく .NET Framework プロジェクトを生成します。 **Linux**または**OSX**でを実行している場合は、[コマンドラインツール](get-started-command-line.md)を使用することをお勧めします。

## <a name="creating-your-first-project-with-ionide"></a>Ionide を使用した最初のプロジェクトの作成

新しい F# プロジェクトを作成するには、新しいフォルダー (することができます、どのような名前) に Visual Studio Code を開きます。

次に、コマンドパレット (**View > コマンドパレット**) を開き、次のように入力します。

```console
> F# new project
```

これは、[偽造](https://github.com/fsharp-editing/Forge)されたプロジェクトを利用しています。

> [!NOTE]
> テンプレートオプションが表示されない場合は、コマンドパレットで次のコマンドを実行して`>F#: Refresh Project Templates`テンプレートを更新してみてください:。

F#:**Enter キー**を押して、新しいプロジェクトを作成します。 これにより、次の手順に進みます。これは、プロジェクトテンプレートを選択するためのものです。

テンプレートを選択し、 **Enter キー**を押します。 `classlib`

次に、プロジェクトを作成するディレクトリを選択します。 空白のままにすると、現在のディレクトリが使用されます。

最後の手順でプロジェクトに名前を指定します。 F#プロジェクト名として[Pascal](http://c2.com/cgi/wiki?PascalCase)形式を使用します。 この記事で`ClassLibraryDemo`は、を名前として使用します。 プロジェクトに使用する名前を入力したら、 **Enter キー**を押します。

前の手順に従った場合は、左側に Visual Studio Code ワークスペースが表示され、次のように表示されます。

1. フォルダー F#の`ClassLibraryDemo`下にあるプロジェクト自体。
2. を介し[`Paket`](https://fsprojects.github.io/Paket/)てパッケージを追加するための適切なディレクトリ構造。
3. を使用した[`FAKE`](https://fsharp.github.io/FAKE/)クロスプラットフォームのビルドスクリプト。
4. パッケージをフェッチし、依存関係を解決できる実行可能ファイル。`paket.exe`
5. この`.gitignore`プロジェクトを Git ベースのソース管理に追加する場合は、ファイル。

## <a name="writing-some-code"></a>コードの記述

*Classlibrarydemo*フォルダーを開きます。  次のファイルが表示されます。

1. `ClassLibraryDemo.fs`で定義されているクラスを使用して F# 実装ファイルです。
2. `ClassLibraryDemo.fsproj`、F# プロジェクト ファイルをこのプロジェクトをビルドするために使用します。
3. `Script.fsx`、ソース ファイルを読み込む F# スクリプト ファイル。
4. `paket.references`は、プロジェクトの依存関係を指定するパケットファイルです。

を`Script.fsx`開き、の末尾に次のコードを追加します。

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

この関数は、単語を[Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)の形式に変換します。 次の手順では、F# Interactive (FSI) を使用して評価です。

関数全体を強調表示します (11 行の長さである必要があります)。 強調表示されたら、 **Alt**キーを押しながら**Enter**キーを押します。 ウィンドウのポップアップが表示され、次のように表示されます。

![Ionide の概要で F# Interactive の出力の例](./media/getting-started-vscode/vscode-fsi.png)

これは次の3つの処理を行いました。

1. FSI.EXE プロセスを開始しました。
2. FSI.EXE プロセスで強調表示したコードが送信されました。
3. FSI.EXE プロセスは、送信したコードを評価しました。

送信したのは[関数](../language-reference/functions/index.md)だったので、fsi.exe! を使用してその関数を呼び出すことができるようになりました。 対話型ウィンドウで、次のように入力します。

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

関数が想定どおりに動作しているようです。 これで、先ほど Visual Studio Code で初めての F# 関数を記述し、FSI を使用して評価すること。

> [!NOTE]
> ご存知かもしれませんが、FSI.EXE の行は`;;`で終了します。 これは、FSI.EXE で複数の行を入力できるためです。 最後`;;`のは、コードが終了したことを fsi.exe に通知します。

## <a name="explaining-the-code"></a>コードの説明

実際にコードが何をしているかわからない場合は、次の手順を実行します。

ご覧のように、 `toPigLatin`は単語を入力として受け取り、その単語の Pig 表現に変換する関数です。 この規則は次のとおりです。

単語の最初の文字が母音で始まる場合は、単語の末尾に "yay" を追加します。 母音で始まらない場合は、その最初の文字を単語の末尾に移動し、それに "ay" を追加します。

FSI.EXE では、次のことにご気になるかもしれません。

```fsharp
val toPigLatin : word:string -> string
```

これは、 `toPigLatin` `string`を入力として受け取り (と呼び`word`ます)、別`string`のを返す関数であることを示します。 呼ばれます、[関数の型シグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/)、基本的な F# コードを理解する鍵は、F# です。 Visual Studio Code で関数をポイントすると、この点にも注意してください。

関数の本体には、次の2つの異なる部分があります。

1. 指定した文字 ( `isVowel`) が、指定されたパターン`c`のいずれかと一致するかどうかをチェックすることによって、特定の文字 () が母音であるかどうかを判断する内部[関数。](../language-reference/pattern-matching.md)

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. 最初の文字が母音であるかどうかを確認し、最初の文字が母音であるかどうかに基づいて、入力文字から戻り値を構築する[式。`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

そのため、 `toPigLatin`のフローは次のようになります。

入力単語の最初の文字が母音であるかどうかを確認します。 の場合は、単語の末尾に "yay" を付加します。 それ以外の場合は、最初の文字を単語の末尾に移動し、それに "ay" を追加します。

この点については最後に説明します。他の多くの言語とは異なり、関数から戻る明示的な命令はありません。 これは、 F#が式ベースであり、関数本体の最後の式が戻り値であるためです。 は`if..then..else`それ自体が式であるため、入力`then`値に応じてブロックの`else`本体またはブロックの本体が返されます。

## <a name="moving-your-script-code-into-the-implementation-file"></a>実装ファイルへのスクリプトコードの移動

この記事では、前のセクションには、F# コードの記述の一般的な最初の手順が示されています。 最初の関数の記述と、FSI 使用して対話的に実行します。 これは REPL ドリブン開発と呼ばれます。 [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)は "Read Evaluate-Print Loop" を表します。 機能を使用するには、機能を試してみることをお勧めします。

REPL 駆動型開発の次の手順では、作業コード F# 実装ファイルに移動します。 これは、実行可能なアセンブリの F# コンパイラによってコンパイルできます。

開始するには`ClassLibraryDemo.fs`、を開きます。  いくつかのコードが既に存在していることがわかります。 クラス定義を削除しますが、宣言は[`namespace`](../language-reference/namespaces.md)先頭に残しておいてください。

次に、という[`module`](../language-reference/modules.md) `PigLatin`新しいを作成し`toPigLatin` 、関数を次のようにコピーします。

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

次に、 `Script.fsx`ファイルをもう一度開き、関数全体`toPigLatin`を削除します。ただし、ファイルには次の2行を必ず残してください。

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

正常に完了 取得する前に、同じ結果が、F# 実装ファイルから読み込まれるようになりました。 ここでの主な違いは、F# ソース ファイルが FSI 内だけでなく、どこにでも実行できるアセンブリにコンパイルされます。

## <a name="summary"></a>まとめ

この記事では、次のことを学習しました。

1. Ionide を使用して Visual Studio Code を設定する方法について説明します。
2. Ionide の概要で初めての F# プロジェクトを作成する方法。
3. F# スクリプトを使用して、ionide の概要で初めての F# 関数を記述し、FSI で実行する方法。
4. スクリプトを移行する方法を使用して、F# ソース コード、FSI からそのコードを呼び出します。

コードより F# Visual Studio Code および ionide の概要を使用して書き込むが組み込まれました。

## <a name="troubleshooting"></a>トラブルシューティング

発生する可能性がある特定の問題をトラブルシューティングするには、次のいくつかの方法があります。

1. Ionide の概要の編集機能をコードを取得するには、F# ファイルはディスク、および Visual Studio Code ワークスペースで開いているフォルダー内に保存する必要があります。
2. システムに変更を加えた場合、または Visual Studio Code を開いた状態でインストールされた Ionide の前提条件を確認した場合は、Visual Studio Code を再起動します。
3. 完全修飾パスを使用せF#ずにF# 、コマンドラインからコンパイラおよび interactive を使用できることを確認します。 」と入力して行うことができます`fsc`、F# コンパイラのコマンドラインで、`fsi`または`fsharpi`の Visual F# ツールの Windows、Mac または Linux での Mono でそれぞれします。
4. プロジェクトディレクトリに無効な文字が含まれていると、Ionide が機能しない可能性があります。  この場合は、プロジェクトディレクトリの名前を変更します。
5. Ionide コマンドがいずれも動作していない場合は、 [Visual Studio Code キーバインド](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)を調べて、誤って上書きされていないかどうかを確認します。
6. Ionide がコンピューター上で破損していて、上記のいずれも問題を解決して`ionide-fsharp`いない場合は、コンピューター上のディレクトリを削除し、プラグインスイートを再インストールしてみてください。

Ionide の概要とは、構築および F# コミュニティのメンバーによって管理されるオープン ソース プロジェクトです。 問題を報告して、 [Ionide-vscode に投稿してください。Fsharp.core GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)。

報告する問題が発生した場合は、「ログを取得する」[の手順](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)に従って、問題を報告してください。

Ionide の概要開発者および F# コミュニティからさらにヘルプを求めることも、 [Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project)します。

## <a name="next-steps"></a>次の手順

F# と言語の機能の詳細については、[F# のツアー](../tour.md) を参照してください。
