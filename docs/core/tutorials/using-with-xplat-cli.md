---
title: CLI を使用する .NET Core に関する概要
description: Windows、Linux、または macOS の .NET Core での、.NET Core コマンド ライン インターフェイス (CLI) の使用方法を段階的に説明するチュートリアル。
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: cf8c3ae070f4c77789dc55ba4d7888c7b15c8653
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736992"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要

このトピックでは、.NET Core CLI ツールを利用し、自分のコンピューターでプラットフォームに依存しないアプリを開発する方法について説明します。

.NET Core CLI ツールセットに慣れていない場合は、[.NET Core SDK の概要](../tools/index.md) に関するページを参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- [.NET Core SDK 2.1](https://dotnet.microsoft.com/download) 以降のバージョン。
- ユーザーが選んだテキスト エディターまたはコード エディター。

## <a name="hello-console-app"></a>Hello コンソール アプリ

GitHub の dotnet/samples レポジトリから、[サンプル コードを表示またはダウンロード](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)することができます。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。

コマンド プロンプトを開き、*Hello* という名前のフォルダーを作成します。 作成したフォルダーに移動して、次のように入力します。

```dotnetcli
dotnet new console
dotnet run
```

簡単に説明します。

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な依存関係を含む最新の *Hello.csproj* プロジェクト ファイルを作成します。 また、アプリケーションのエントリ ポイントを含む基本的なファイルである *Program.cs* も作成します。

   *Hello.csproj*:

   [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   プロジェクト ファイルでは、依存関係を復元し、プログラムをビルドするために必要なすべてのものを指定します。

   - `OutputType` タグは、実行可能ファイル (つまり、コンソール アプリケーション) をビルドすることを示します。
   - `TargetFramework` タグは、対象の .NET 実装を指定します。 高度なシナリオでは、複数の対象フレームワークを指定し、1 回の操作でそれらすべてにビルドすることができます。 このチュートリアルでは、.NET Core 2.1 の場合のビルドについてのみ説明します。

   *Program.cs*:

   [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]

   プログラムは `using System` で始まります。これは、"`System` 名前空間のすべてがこのファイルのスコープになる" こと意味します。 `System` 名前空間には、`Console` クラスが含まれています。

   次に、`Hello` という名前空間を定義します。 これを必要なものに変更できます。 `Program` という名前のクラスは、引数として文字列配列を使用する `Main` メソッドで、その名前空間内に定義されます。 この配列には、コンパイル済みプログラムの呼び出し時に渡される引数のリストが含まれます。 実際は、この配列は使用されません。プログラムはコンソールに "Hello World!" と 記述するだけです。 後に、この引数を利用するようにコードを変更します。

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` は [`dotnet restore`](../tools/dotnet-restore.md) を暗黙的に呼び出します。 `dotnet restore` は、[NuGet](https://www.nuget.org/) (.NET パッケージ マネージャー) を呼び出して依存関係ツリーを復元します。 NuGet は、*Hello.csproj* ファイルを分析し、ファイルに記載されている依存関係をダウンロードし (またはコンピューターのキャッシュから取得し)、サンプルをコンパイルして実行するために必要な *obj/project.assets.json* ファイルを記述します。

   > [!IMPORTANT]
   > .NET Core 1.x バージョンの SDK を使用している場合は、`dotnet new` の呼び出し後に `dotnet restore` を自分で呼び出す必要があります。

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) は、[`dotnet build`](../tools/dotnet-build.md) を呼び出してビルド ターゲットがビルドされていることを確認した後、`dotnet <assembly.dll>` を呼び出してターゲット アプリケーションを実行します。

    ```console
    $ dotnet run
    Hello World!
    ```

    [`dotnet build`](../tools/dotnet-build.md) を実行し、ビルド コンソール アプリケーションを実行しないでコードをコンパイルすることもできます。 これで、Windows で `dotnet bin\Debug\netcoreapp2.1\Hello.dll` を使用して (Windows 以外のシステムの場合は `/` を使用して) 実行できる DLL ファイルとしてアプリケーションがコンパイルされます。 アプリケーションには引数を指定することもできます。それについてはこのトピックの後半で説明します。

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    高度なシナリオでは、展開可能なプラットフォーム固有のファイルの自己完結型セットとしてアプリケーションをビルドし、.NET Core が必ずしもインストールされているとは限らないコンピューターに対して実行することができます。 詳細については、「[.NET Core アプリケーション展開](../deploying/index.md)」を参照してください。

### <a name="augmenting-the-program"></a>プログラムの拡張

プログラムを少し変更してみましょう。 フィボナッチ数は面白いです。アプリを実行した人に挨拶をする引数を使用するためにフィボナッチ数も追加しましょう。

1. *Program.cs* ファイルの内容を次のコードで置き換えます。

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. [`dotnet build`](../tools/dotnet-build.md) を実行し、変更内容をコンパイルします。

3. アプリにパラメーターを渡すプログラムを実行します。

   ```console
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

以上です。  自由に *Program.cs* を拡張できます。

## <a name="working-with-multiple-files"></a>複数のファイルの操作

単純な 1 回だけのプログラムには 1 つのファイルで十分ですが、より複雑なアプリをビルドする場合、プロジェクトに複数のソース ファイルを使用する可能性があります。
先のフィボナッチのサンプルから作成してみましょう。いくつかのフィボナッチ値をキャッシュしてから、再帰機能をいくつか追加します。

1. 次のコードを利用し、*FibonacciGenerator.cs* という名前の *Hello* ディレクトリ内に新しいファイルを追加します。

   [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. *Program.cs* ファイルの `Main` メソッドを変更し、次の例のように新しいクラスをインスタンス化し、そのメソッドを呼び出します。

   [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. [`dotnet build`](../tools/dotnet-build.md) を実行し、変更内容をコンパイルします。

4. [`dotnet run`](../tools/dotnet-run.md) を実行し、アプリを実行します。 プログラムの出力は次のようになります。

   ```console
   $ dotnet run
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

## <a name="publish-your-app"></a>アプリケーションの発行

アプリを配布する準備ができたら、[`dotnet publish`](../tools/dotnet-publish.md) コマンドを使って、_bin\\debug\\netcoreapp2.1\\publish\\_ に _publish_ フォルダーを生成します (Windows 以外のシステムの場合は `/` を使います)。 dotnet ランタイムが既にインストールされている他のプラットフォームには、_publish_ フォルダーの内容を配布できます。

[dotnet](../tools/dotnet.md) コマンドを使って、発行されたアプリを実行できます。

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a>まとめ

以上です。 これで、ここで学習した基本的な概念を利用し、自分だけのプログラムを作成できます。

## <a name="see-also"></a>関連項目

- [.NET Core CLI ツールを使用したプロジェクトの整理およびテスト](testing-with-cli.md)
- [CLI を使用して .NET Core アプリを公開する](../deploying/deploy-with-cli.md)
- [アプリの展開についてさらに学習する](../deploying/index.md)
