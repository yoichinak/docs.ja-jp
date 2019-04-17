---
title: Visual Studio 2017 での .NET Core Hello World アプリケーションの発行
description: 発行では、.NET Core アプリケーションを実行するために必要なファイルのセットを作成します。
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0322d44ca37ab8e7faa3188887069c2e04ec755b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110267"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>Visual Studio 2017 での .NET Core Hello World アプリケーションの発行

「[Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築](with-visual-studio.md)」または「[Visual Studio 2017 での .NET Core を使用した Visual Basic Hello World アプリケーションの構築](vb-with-visual-studio.md)」では、Hello World コンソール アプリケーションを構築しました。 「[Visual Studio 2017 での C# Hello World アプリケーションのデバッグ](debugging-with-visual-studio.md)」では、Visual Studio デバッガーを使ってアプリケーションをテストしました。 正しく動作することが確認できたので、他のユーザーが使用できるように発行することができます。 発行では、アプリケーションを実行するために必要なファイルのセットが作成されます。これらのファイルは、対象コンピューターにコピーすることで配置できます。

アプリケーションを発行および実行するには 

1. Visual Studio がアプリケーションのリリース バージョンをビルドしていることを確認します。 必要に応じて、ツール バーのビルド構成の設定を **[デバッグ]** から **[リリース]** に変更します。

   ![リリース ビルドが選択された Visual Studio のツールバー](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. **HelloWorld** プロジェクト (HelloWorld ソリューションではなく) を右クリックし、メニューから **[発行]** を選びます。 Visual Studio のメイン メニューの **[ビルド]** から **[HelloWorld を発行]** を選択することもできます。

   ![Visual Studio の [発行] コンテキスト メニュー](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Visual Studio の [発行] ウィンドウ](media/publishing-with-visual-studio/publish-settings-window.png)

1. コンソール ウィンドウが開きます。 たとえば、Windows タスク バーの **[検索するテキストをここに入力]** テキスト ボックスに「`Command Prompt`」 (または省略して「`cmd`」) と入力し、**コマンド プロンプト** デスクトップ アプリを選ぶか、コマンド プロンプトが検索結果で選択されている場合は Enter キーを押して、コンソール ウィンドウを開きます。

1. アプリケーションのプロジェクト ディレクトリの `bin\release\PublishOutput` サブディレクトリで、発行されたアプリケーションに移動します。 次の図に示すように、発行された出力には次の 4 つのファイルが含まれます。

      * *HelloWorld.deps.json*

         アプリケーションのランタイム依存関係ファイル。 アプリケーションの実行に必要な .NET Core コンポーネントとライブラリ (アプリケーションが含まれる動的リンク ライブラリを含む) を定義します。 詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。
 
      * *HelloWorld.dll*

         アプリケーションが含まれるファイル。 動的リンク ライブラリであり、コンソール ウィンドウに `dotnet HelloWorld.dll` コマンドを入力することで実行できます。 

      * *HelloWorld.pdb* (配置は省略可能)

         デバッグ シンボルが含まれるファイル。 このファイルはアプリケーションと一緒に配置する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。

      * *HelloWorld.runtimeconfig.json*

         アプリケーションのランタイム構成ファイル。 ビルドされたアプリケーションが実行時に基盤とする .NET Core のバージョンを識別します。 詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。  

   ![発行されたファイルが表示されているコンソール ウィンドウ](media/publishing-with-visual-studio/published-files-output.png)

発行プロセスでは、フレームワークに依存する配置が作成されます。これは、.NET Core がシステムにインストールされていれば、.NET Core によってサポートされる任意のプラットフォームで発行されたアプリケーションが動作する配置の種類です。 ユーザーはコンソール ウィンドウから `dotnet HelloWorld.dll` コマンドを発行することによって、アプリケーションを実行できます。

.NET Core アプリケーションの発行と展開の詳細については、「[.NET Core アプリケーション展開](../../core/deploying/index.md)」を参照してください。
