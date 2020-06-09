---
title: Visual Studio Code で .NET Standard クラス ライブラリを作成する
description: Visual Studio Code を使用して .NET Standard クラス ライブラリを作成する方法について説明します。
ms.date: 05/29/2020
ms.openlocfilehash: 5720ac374d50ef27a07d463e57af1bd95a352d83
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446953"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a>チュートリアル: Visual Studio Code で .NET Standard ライブラリを作成する

"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。 .NET Standard 2.0 をターゲットとするクラス ライブラリでは、お使いのライブラリを、そのバージョンの .NET Standard をサポートする任意の .NET 実装によって呼び出すことができます。 ご自分のクラス ライブラリを完了させたら、それを NuGet パッケージとして配布するか、あるいは 1 つ以上のアプリケーションにコンポーネントとしてバンドルして含めるかどうかを決定します。

> [!NOTE]
> .NET Standard のバージョンとそれらがサポートするプラットフォームの一覧は、「[.NET Standard](../../standard/net-standard.md)」を参照してください。

このチュートリアルでは、1 つの文字列処理メソッドを含む簡単なユーティリティ ライブラリを作成します。 それを[拡張メソッド](../../csharp/programming-guide/classes-and-structs/extension-methods.md)として実装し、<xref:System.String> クラスのメンバーと同じように呼び出すことができるようにします。

## <a name="prerequisites"></a>必須コンポーネント

1. [C# 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)がインストールされている [Visual Studio Code](https://code.visualstudio.com/)。 Visual Studio Code に拡張機能をインストールする方法については、[VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) を参照してください。
2. [.Net Core 3.1 SDK 以降](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>ソリューションを作成する

まず、クラス ライブラリ プロジェクトを配置する空のソリューションを作成します。 ソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。 さらに関連するプロジェクトを同じソリューションに追加します。

1. Visual Studio Code を開きます。

1. メイン メニューから **[ファイル]**  >  **[フォルダーを開く]** / **[開く...]** の順に選択し、*ClassLibraryProjects* フォルダーを作成して、 **[フォルダーの選択]** / **[開く]** の順にクリックします。

1. メイン メニューで **[表示]**  >  **[ターミナル]** の順に選択して、Visual Studio Code で**ターミナル**を開きます。

   コマンド プロンプトで *ClassLibraryProjects* フォルダーが表示され、**ターミナル**が開きます。

1. **ターミナル**で、次のコマンドを入力します。

   ```dotnetcli
   dotnet new sln
   ```

   ターミナルには次の例のような出力があります。

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>クラス ライブラリ プロジェクトを作成する

"StringLibrary" という名前の新しい .NET Standard クラス ライブラリ プロジェクトをソリューションに追加します。

1. 次のコマンドをターミナルで実行して、ライブラリ プロジェクトを作成します。

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   ターミナルには次の例のような出力があります。

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. 次のコマンドを実行して、ライブラリ プロジェクトをソリューションに追加します。

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   ターミナルには次の例のような出力があります。

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. ライブラリが正しいバージョンの .NET Standard をターゲットにしていることを確認します。 **エクスプローラー**で、*StringLibrary/StringLibrary .csproj* を開きます。

   `TargetFramework` 要素に、プロジェクトが .NET Standard 2.0 をターゲットとしていることが示されます。

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. *Class1.cs* を開き、このコードを次のものと置き換えます。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   クラス ライブラリ `UtilityLibraries.StringLibrary` には、`StartsWithUpper` という名前のメソッドが含まれています。 このメソッドによって、現在の文字列のインスタンスが大文字で始まるかどうかを示す <xref:System.Boolean> 値が返されます。 Unicode 規格では、大文字と小文字が区別されます。 <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> メソッドは文字が大文字の場合に `true` を返します。

1. ファイルを保存します。

1. 次のコマンドを実行してソリューションをビルドし、エラーなしでプロジェクトがコンパイルされることを確認します。

   ```dotnetcli
   dotnet build
   ```

   ターミナルには次の例のような出力があります。

   ```
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a>ソリューションにコンソール アプリを追加する

このクラス ライブラリを使用するコンソール アプリケーションを追加します。 アプリによって、ユーザーに文字列の入力が求められ、文字列が大文字で始まるかどうかが報告されます。

1. 次のコマンドをターミナルで実行して、コンソール アプリ プロジェクトを作成します。

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   ターミナルには次の例のような出力があります。

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. 次のコマンドを実行して、ソリューションにコンソール アプリ プロジェクトを追加します。

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   ターミナルには次の例のような出力があります。

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. 最初は、新しいコンソール アプリ プロジェクトにクラス ライブラリへのアクセス権はありません。 クラス ライブラリでメソッドを呼び出せるようにするには、次のコマンドを実行して、クラス ライブラリ プロジェクトへのプロジェクト参照を作成します。

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   ターミナルには次の例のような出力があります。

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. *ShowCase/Program.cs* を開き、すべてのコードを次のコードに置き換えます。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   このコードでは、`row` 変数を使って、コンソール ウィンドウに書き込まれるデータの行数のカウントを維持します。 これが 25 以上になると、コードによってコンソール ウィンドウがクリアされ、ユーザーにメッセージが表示されます。

   プログラムは、ユーザーに文字列の入力を要求し、 文字列が大文字で始まるかどうかを示します。 ユーザーが文字列を入力せずに Enter キーを押すと、アプリケーションが終了し、コンソール ウィンドウが閉じます。

1. 変更内容を保存します。

1. プログラムを実行します。

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. 文字列を入力して <kbd>Enter</kbd> キーを押してプログラムを実行し、<kbd>Enter</kbd> キーを押して終了します。

   ターミナルには次の例のような出力があります。

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a>その他の技術情報

* [.NET Core CLI を使用したライブラリの開発](libraries.md)

## <a name="next-steps"></a>次の手順

このチュートリアルでは、ソリューションを作成し、ライブラリ プロジェクトを追加し、ライブラリを使用するコンソール アプリ プロジェクトを追加しました。 次のチュートリアルでは、ソリューションに単体テスト プロジェクトを追加します。

> [!div class="nextstepaction"]
> [Visual Studio Code での .NET Core を使用した .NET Standard ライブラリのテスト](testing-library-with-visual-studio-code.md)
