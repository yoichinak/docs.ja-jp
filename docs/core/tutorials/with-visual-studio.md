---
title: Visual Studio で .NET Core を使用してコンソール アプリケーションを作成する
description: Visual Studio を使用して、C# または Visual Basic で.NET Core コンソール アプリケーションを作成する方法について説明します。
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 9c3456cd8c940e53e8a70c1d3a7c3b09de77c21d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201584"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a>チュートリアル: Visual Studio 2019 で .NET Core コンソール アプリケーションを作成する

このチュートリアルでは、Visual Studio 2019 で .NET Core コンソール アプリケーションを作成して実行する方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

- **.NET Core クロスプラットフォーム開発**ワークロードがインストールされている [Visual Studio 2019 バージョン 16.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 このワークロードを選択すると、.NET Core 3.1 SDK が自動的にインストールされます。

  詳細については、記事「[.NET Core SDK をインストールする](../install/sdk.md?pivots=os-windows)」の「[Visual Studio を使用してインストールする](../install/sdk.md?pivots=os-windows#install-with-visual-studio)」のセクションを参照してください。

## <a name="create-the-app"></a>アプリを作成する

<!-- markdownlint-disable MD025 -->

1. Visual Studio 2019 を開きます。

1. "HelloWorld" という名前の新しい .NET Core コンソール アプリ プロジェクトを作成します。

   1. スタート ページで、 **[新しいプロジェクトの作成]** を選択します。

      ![Visual Studio のスタート ページで [新しいプロジェクトの作成] ボタンが選択されている](./media/with-visual-studio/start-window.png)

   1. **[新しいプロジェクトの作成]** ページで、検索ボックスに「**コンソール**」と入力します。 次に、言語の一覧から **[C#]** または **[Visual Basic]** を選択してから、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。 **[コンソール アプリ (.NET Core)]** テンプレートを選択し、 **[次へ]** を選択します。

      ![フィルターが選択された状態の [新しいプロジェクトの作成] ウィンドウ](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > .NET Core テンプレートが表示されない場合は、必要なワークロードが不足している可能性があります。 **[お探しの情報が見つかりませんでしたか?]** メッセージで、 **[さらにツールと機能をインストールする]** リンクを選択します。 Visual Studio インストーラーが開きます。 **.NET Core クロスプラットフォーム開発**ワークロードがインストールされていることを確認してください。

   1. **[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**HelloWorld**」と入力します。 次に、 **[作成]** を選択します。

      ![プロジェクト名、場所、およびソリューション名のフィールドを使用して新しいプロジェクト ウィンドウを構成します](./media/with-visual-studio/configure-new-project.png)

   .NET Core のコンソール アプリケーション テンプレートで、`Program` というクラスが、<xref:System.String> 配列を引数として必要とする単一のメソッド `Main` とともに定義されます。 `Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。 アプリケーションが起動されるときに提供されるコマンドライン引数はすべて *args* 配列にあります。

   使用する言語が表示されていない場合は、ページの上部にある言語セレクターを変更します。

   ```csharp
   using System;

   namespace HelloWorld
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   このテンプレートでは、シンプルな "Hello World" アプリケーションを作成します。 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> メソッドを呼び出し、"Hello World!" を コンソール ウィンドウに表示します。

## <a name="run-the-app"></a>アプリを実行する

1. プログラムを実行するには、ツール バーで **[HelloWorld]** を選択するか、**F5** キーを押します。

   ![HelloWorld の実行ボタンが選択された Visual Studio ツールバー](./media/with-visual-studio/run-program.png)

   コンソール ウィンドウが開き、"Hello World!" というテキストが 画面に出力され、Visual Studio のデバッグ情報が表示されます。

   ![Hello World Press any key to continue と表示されているコンソール ウィンドウ](./media/with-visual-studio/hello-world-console.png)

1. 任意のキーを押して、コンソール ウィンドウを閉じます。

## <a name="enhance-the-app"></a>アプリを拡張する

アプリケーションを拡張し、ユーザーに名前の入力を求め、日付と時刻と共にそれを表示するようにします。 次の手順では、アプリを変更してから再度実行します。

1. `Main` メソッド (現在は `Console.WriteLine` を呼び出す行のみ) の内容を以下のコードに置き換えます。

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="Snippet1":::

   このコードは、"What is your name?" と コンソール ウィンドウに表示して、ユーザーが文字列を入力して Enter キーを押すまで待機します。 これはこの文字列を `name` という変数に格納します。 さらに現在の現地時刻を含む <xref:System.DateTime.Now?displayProperty=nameWithType> プロパティの値を取得して、それを `date` という変数に代入します (Visual Basic では `currentDate`)。 最後に、これらの値がコンソール ウィンドウに表示されます。

   `\n` (Visual Basic では `vbCrLf`) は、改行文字を表します。

   文字列の前にドル記号 (`$`) を付けると、変数名などの式を文字列で中かっこで囲むことができます。 式の値が、式の代わりに文字列に挿入されます。 この構文は、[補間された文字列](../../csharp/language-reference/tokens/interpolated.md)と呼ばれます。

1. プログラムを実行するには、ツール バーで **[HelloWorld]** を選択するか、**F5** キーを押します。

1. プロンプトに対し、名前を入力し、**Enter** キーを押します。

   ![プログラムの出力が変更されたコンソール ウィンドウ](./media/with-visual-studio/hello-world-update.png)

1. 任意のキーを押して、コンソール ウィンドウを閉じます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、.NET Core アプリケーションを作成しました。 次のチュートリアルでは、アプリをデバッグします。

> [!div class="nextstepaction"]
> [Visual Studio で .NET Core コンソール アプリケーションをデバッグする](debugging-with-visual-studio.md)
