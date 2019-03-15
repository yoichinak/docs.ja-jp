---
title: Visual Studio Code での F# の概要します。
description: Visual Studio Code および ionide の概要のプラグインのスイートで F# を使用する方法について説明します。
ms.date: 12/23/2018
ms.openlocfilehash: 3e526d33a8b52e3c1241ed861d5ceb37eac10451
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846572"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio Code での F# の概要します。

書き込めるF#で[Visual Studio Code](https://code.visualstudio.com)で、 [Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)クロス プラットフォームの軽量な統合開発環境 (IDE) ですばらしい体験を IntelliSense および基本的なコードを取得するにはリファクタリング。 参照してください[Ionide.io](http://ionide.io)プラグインの詳細を表示します。

作業を開始できることを確認します。 [F# および ionide の概要プラグインが正しくインストールされている](install-fsharp.md#install-f-with-visual-studio-code)します。

> [!NOTE]
> Ionide の概要では、.NET Framework を生成します。F#プロジェクト、dotnet core ではなく、クロス プラットフォームの互換性の問題があることができます。 実行している場合**Linux**または**OSX**、開始する簡単な方法は使用する、[コマンド ライン ツール](https://docs.microsoft.com/en-us/dotnet/fsharp/get-started/get-started-command-line)します。

## <a name="creating-your-first-project-with-ionide"></a>Ionide の概要と、最初のプロジェクトを作成します。

新しい F# プロジェクトを作成するには、新しいフォルダー (することができます、どのような名前) に Visual Studio Code を開きます。

次に、コマンド パレットを開いて (**ビュー > コマンド パレット**) と入力します。

```
> F# new project
```

これで電源がオン、[偽造](https://github.com/fsharp-editing/Forge)プロジェクト。

> [!NOTE]
> テンプレート オプションが表示されない場合は、コマンド パレットで、次のコマンドを実行してテンプレートを更新してください:`>F#: Refresh Project Templates`します。

選択"F#:新しいプロジェクト を押して**Enter**します。 プロジェクト テンプレートを選択するためには、次の手順に移動します。

選択、`classlib`テンプレートとヒット**Enter**します。

次でプロジェクトを作成するディレクトリを選択します。 空のまま、現在のディレクトリを使用します。

最後に、最後の手順で、プロジェクトの名前を付けます。 F#使用して[パスカル ケース](http://c2.com/cgi/wiki?PascalCase)プロジェクト名にします。 この記事では`ClassLibraryDemo`名として。 プロジェクトの名前を入力したら後のヒット**Enter**します。

前の手順を実行する場合に次のように表示される、左側にある Visual Studio コード ワークスペースを取得する必要があります。

1. F#プロジェクト自体の下に、`ClassLibraryDemo`フォルダー。
2. 使用してパッケージを追加するための適切なディレクトリ構造[ `Paket`](https://fsprojects.github.io/Paket/)します。
3. クロス プラットフォーム ビルド スクリプトを[ `FAKE`](https://fsharp.github.io/FAKE/)します。
4. `paket.exe`実行可能ファイルをパッケージのフェッチし、の依存関係を解決することができます。
5. A`.gitignore`ファイルを Git ベースのソース管理にこのプロジェクトを追加する場合。

## <a name="writing-some-code"></a>コードの作成

開く、 *ClassLibraryDemo*フォルダー。  次のファイルが表示されます。

1. `ClassLibraryDemo.fs`で定義されているクラスを使用して F# 実装ファイルです。
2. `ClassLibraryDemo.fsproj`、F# プロジェクト ファイルをこのプロジェクトをビルドするために使用します。
3. `Script.fsx`、ソース ファイルを読み込む F# スクリプト ファイル。
4. `paket.references`、パケット ファイルをプロジェクトの依存関係を指定します。

開いている`Script.fsx`の末尾に次のコードを追加します。

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

この関数は、単語の形式に変換します[Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)します。 次の手順では、F# Interactive (FSI) を使用して評価です。

(11 行である必要があります) 関数全体を強調表示します。 強調表示され後の保持、 **Alt**キーとヒット **」と入力**します。 以下に、ポップアップ ウィンドウがわかり、このようなものが表示する必要があります。

![Ionide の概要で F# Interactive の出力の例](media/getting-started-vscode/vscode-fsi.png)

これは、次の 3 つを行いました。

1. FSI プロセスを開始します。
2. 強調表示したコードは、FSI プロセス上で送信します。
3. FSI プロセス経由で送信するコードを評価します。

経由で送信するため、[関数](../language-reference/functions/index.md)FSI でその関数を呼び出すようになりましたことができます。 対話型のウィンドウで、次のように入力します。

```fsharp
toPigLatin "banana";;
```

次の結果が表示されます。

```fsharp
val it : string = "ananabay"
```

ここで、最初の文字としての母音を試してみましょう。 次のように入力します。

```fsharp
toPigLatin "apple";;
```

次の結果が表示されます。

```fsharp
val it : string = "appleyay"
```

関数は、想定どおりに動作するが表示されます。 これで、先ほど Visual Studio Code で初めての F# 関数を記述し、FSI を使用して評価すること。

> [!NOTE]
> FSI の明細行がで終了しましたように気付き、`;;`します。 これは、FSI では、複数の行を入力できるためです。 `;;`により FSI 確認コードが完了すると、最後にします。

## <a name="explaining-the-code"></a>コードの説明

コードが実際に何のことを確認していない場合は、次に、順を追って示します。

ご覧のとおり、`toPigLatin`関数は、単語の入力として受け取り、その単語の Pig Latin 表現に変換します。 このルールは次のとおりです。

単語の最初の文字が母音で始まる場合は、単語の末尾に"yay"を追加します。 、母音で開始しない場合は、その最初の文字を単語の末尾に移動し、を「なります」に追加します。

FSI では、次お気付きかもしれません。

```fsharp
val toPigLatin : word:string -> string
```

示すこの`toPigLatin`で受け取る関数には、`string`入力として (と呼ばれる`word`)、戻って別`string`。 呼ばれます、[関数の型シグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/)、基本的な F# コードを理解する鍵は、F# です。 また、この場合、Visual Studio Code で関数ポインターを合わせます。

関数の本文で、2 つの異なる部分がわかります。

1. 呼ばれる、内部関数`isVowel`、特定の文字を決定する (`c`) を使用して指定されたパターンのいずれかと一致する場合にチェックして、母音は、[パターン マッチング](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)かどうかは、最初の文字は、母音と場合、最初の文字ベースの構造は、入力文字列からの戻り値をチェックする式、母音であるか。

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

フローの`toPigLatin`なります。

入力の単語の最初の文字の母音であることを確認します。 場合は、"yay"という単語の末尾にアタッチします。 それ以外の場合、その最初の文字を単語の末尾に移動し、それを「なります」に追加します。

1 つの最後にこれに関する注意: その他の多くの言語とは異なり、関数から返される明示的な命令はありません。 これは、ためF#が式に基づいて、関数の本体の最後の式は、戻り値。 `if..then..else`自体、式の本体では、`then`ブロックまたはの本文、`else`ブロックが入力値によって返されます。

## <a name="moving-your-script-code-into-the-implementation-file"></a>スクリプト コードを実装ファイルに移動

この記事では、前のセクションには、F# コードの記述の一般的な最初の手順が示されています。 最初の関数の記述と、FSI 使用して対話的に実行します。 これは、REPL 駆動型開発と呼ばれます、 [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 「読み取り評価印刷ループ」を意味します。 機能を試して動作ものがある場合する優れた方法です。

REPL 駆動型開発の次の手順では、作業コード F# 実装ファイルに移動します。 これは、実行可能なアセンブリの F# コンパイラによってコンパイルできます。

まず、開きます`ClassLibraryDemo.fs`します。  いくつかのコードが既にに存在することがわかります。 前方に移動し、クラス定義を削除しますがのままにすることを確認、 [ `namespace` ](../language-reference/namespaces.md)上部にある宣言します。

次に、作成、新しい[ `module` ](../language-reference/modules.md)と呼ばれる`PigLatin`をコピーし、`toPigLatin`ように関数。

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

次に、開く、`Script.fsx`ファイルを再び、および全体を削除`toPigLatin`ファイルに次の 2 つの行を保持することを確認しますが、機能します。

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```
テキストの両方の行を選択して、FSI でこれらの行を実行するには、Alt + Enter キーを押します。 FSI のプロセスに Pig Latin ライブラリのコンテンツを読み込むこれらと`open`、`ClassLibraryDemo`名前空間の機能にアクセスできるようにします。

次に、FSI ウィンドウで、使用して、関数を呼び出して、`PigLatin`前に定義したモジュール。

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

正常に完了 取得する前に、同じ結果が、F# 実装ファイルから読み込まれるようになりました。 ここでの主な違いは、F# ソース ファイルが FSI 内だけでなく、どこにでも実行できるアセンブリにコンパイルされます。

## <a name="summary"></a>まとめ

この記事では、次の学習できました。

1. Ionide の概要を使用して Visual Studio Code を設定する方法。
2. Ionide の概要で初めての F# プロジェクトを作成する方法。
3. F# スクリプトを使用して、ionide の概要で初めての F# 関数を記述し、FSI で実行する方法。
4. スクリプトを移行する方法を使用して、F# ソース コード、FSI からそのコードを呼び出します。

コードより F# Visual Studio Code および ionide の概要を使用して書き込むが組み込まれました。

## <a name="troubleshooting"></a>トラブルシューティング

次に遭遇する可能性のある特定の問題のトラブルシューティングを行うことがいくつかの方法を示します。

1. Ionide の概要の編集機能をコードを取得するには、F# ファイルはディスク、および Visual Studio Code ワークスペースで開いているフォルダー内に保存する必要があります。
2. 場合は、システムを変更または開いている Visual Studio のコードと共に ionide の概要の前提条件をインストールしたら、Visual Studio Code を再起動します。
3. 使用できることを確認、F#コンパイラとF#完全修飾パスを使用せずにコマンドラインから対話型です。 」と入力して行うことができます`fsc`、F# コンパイラのコマンドラインで、`fsi`または`fsharpi`の Visual F# ツールの Windows、Mac または Linux での Mono でそれぞれします。
4. プロジェクトのディレクトリで無効な文字があれば、ionide の概要が動作しない可能性があります。  これに該当する場合、プロジェクト ディレクトリの名前を変更します。
5. Ionide コマンドのいずれも作業している場合、 [Visual Studio Code の keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)を誤って上書きしているかどうかを参照してください。
6. Ionide の概要は、コンピューターに分割すると、上記のいずれが問題を修正、削除してみてください、`ionide-fsharp`コンピューターにディレクトリ プラグイン スイートを再インストールします。

Ionide の概要とは、構築および F# コミュニティのメンバーによって管理されるオープン ソース プロジェクトです。 問題を報告し、気軽に投稿にしてください、 [Ionide VSCode:FSharp GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)します。

レポートに問題がある場合に従ってください[問題を報告するときに使用するログを取得するための指示](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)します。

Ionide の概要開発者および F# コミュニティからさらにヘルプを求めることも、 [Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project)します。

## <a name="next-steps"></a>次の手順

F# と言語の機能の詳細については、チェック アウト[F# のツアー](../tour.md)します。
