---
title: コマンド ライン ツールの F# の概要します。
description: 任意のオペレーティング システム (Windows、macOs または Linux) で .NET Core CLI を使用した F# で簡単なマルチ プロジェクト ソリューションを構築する方法について説明します。
ms.date: 03/26/2018
ms.openlocfilehash: bc9b223fcf133ffe8b19d5284dcbd3c14a426235
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938698"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>.NET Core CLI を使用した F# の概要します。

この記事では、どのできますを開始する F# .NET Core CLI を使用したオペレーティング システム (Windows、macOS、または Linux) でについて説明します。 コンソール アプリケーションによって呼び出されるクラス ライブラリを使用したマルチ プロジェクト ソリューションを構築する経由になります。

## <a name="prerequisites"></a>必須コンポーネント

を開始するには、、の最新バージョンをインストールする必要があります[.NET Core SDK](https://www.microsoft.com/net/download/)します。

この記事では、方法を知っているコマンドラインを使用して、任意のテキスト エディターを前提としています。 それを既に使用しない場合[Visual Studio Code](get-started-vscode.md) F# 用のテキスト エディターとして便利なオプションです。

## <a name="build-a-simple-multi-project-solution"></a>単純なマルチ プロジェクト ソリューションをビルドします。

コマンド プロンプト/ターミナルを開きを使用して、[新しい dotnet](../../core/tools/dotnet-new.md)という新しいソリューション ファイルを作成するコマンド`FSNetCore`:

```console
dotnet new sln -o FSNetCore
```

前のコマンドを実行した後は、次のディレクトリ構造が生成されます。

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>クラス ライブラリを作成します。

ディレクトリに移動*FSNetCore*します。

使用して、`dotnet new`コマンド、クラス ライブラリ プロジェクトを作成、 **src**ライブラリという名前のフォルダー。

```console
dotnet new classlib -lang F# -o src/Library
```

前のコマンドを実行した後は、次のディレクトリ構造が生成されます。

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

内容を置き換える`Library.fs`を次のコード。

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

ライブラリ プロジェクトに Newtonsoft.Json NuGet パッケージを追加します。

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

追加、`Library`プロジェクトを`FSNetCore`ソリューションを使用して、 [dotnet sln 追加](../../core/tools/dotnet-sln.md)コマンド。

```console
dotnet sln add src/Library/Library.fsproj
```

実行`dotnet build`プロジェクトをビルドします。 作成するときに、未解決の依存関係が復元されます。

### <a name="write-a-console-application-that-consumes-the-class-library"></a>クラス ライブラリを使用するコンソール アプリケーションを作成します。

使用して、`dotnet new`コマンド、コンソール アプリケーションを作成、 **src**アプリという名前のフォルダー。

```console
dotnet new console -lang F# -o src/App
```

前のコマンドを実行した後は、次のディレクトリ構造が生成されます。

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

内容を置き換える、`Program.fs`を次のコード ファイル。

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

参照を追加、`Library`プロジェクトを使用して[dotnet 参照の追加](../../core/tools/dotnet-add-reference.md)します。

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

追加、`App`プロジェクトを`FSNetCore`ソリューションを使用して、`dotnet sln add`コマンド。

```console
dotnet sln add src/App/App.fsproj
```

NuGet の依存関係を復元`dotnet restore`実行`dotnet build`プロジェクトをビルドします。

ディレクトリに、`src/App`コンソール プロジェクトとプロジェクトを渡すことを実行`Hello World`引数として。

```console
cd src/App
dotnet run Hello World
```

次の結果が表示されます。

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>次の手順

次に、チェック アウト、 [F# のツアー](../tour.md)を F# のさまざまな機能の詳細を参照してください。
