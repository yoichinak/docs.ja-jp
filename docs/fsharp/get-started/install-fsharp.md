---
title: インストールします。F#
description: お客様の環境に基づいて、F# をインストールする方法について説明します。
ms.date: 08/28/2018
ms.openlocfilehash: 792c61c0522cd4d0c68a64572f2892ce33f71ea6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331976"
---
# <a name="install-f"></a>F# をインストールします。\#

複数の方法で F# をインストールと、環境に応じてことができます。

## <a name="install-f-with-visual-studio"></a>Visual Studio を使用した F# のインストールします。

ダウンロードしている場合[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)最初に、これは最初にインストール、Visual Studio インストーラー。 インストーラーから、適切な SKU の Visual Studio をインストールします。 既にインストールされていること、クリックして**変更**します。

次のワークロードの一覧を確認します。 選択**ASP.NET および web 開発**F# サポートおよび ASP.NET Core プロジェクトの .NET Core のサポートがインストールされます。

次に、クリックして**変更**下部右側にあります。  これは、選択したすべてのものにインストールされます。 クリックして、F# 言語サポートと Visual Studio 2017 を開くことができますし、**起動**します。

## <a name="install-f-with-visual-studio-for-mac"></a>インストールF#Visual studio for Mac

既定で F# がインストールされている[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)、選択した構成に関係なく。

インストールが完了した後は、"Visual Studio を起動する"を選択します。 起動してもかまいませんが Finder を macOS でします。

## <a name="install-f-with-visual-studio-code"></a>Visual Studio Code で F# のインストールします。

必要があります[git がインストールされている](https://git-scm.com/download)を PATH にで使用可能なプロジェクト テンプレートの使用します。 」と入力して正しくインストールされていることを確認する`git --version`キーを押して、コマンド プロンプトで**Enter**します。

### [<a name="macos"></a>macOS](#tab/macos)

[Mono](https://www.mono-project.com)使用[F# Interactive](../tutorials/fsharp-interactive/index.md)をサポートします。 MacOS で Mono をインストールする最も簡単な方法は、Homebrew を使用してです。 単に、ターミナルに、次を入力します。

```console
brew install mono
```

インストールことも、 [.NET Core SDK](https://www.microsoft.com/net/download)します。

### [<a name="linux"></a>Linux](#tab/linux)

[Mono](https://www.mono-project.com)使用[F# Interactive](../tutorials/fsharp-interactive/index.md)をサポートします。 Debian または Ubuntu の場合は、次を使用できます。

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

インストールことも、 [.NET Core SDK](https://www.microsoft.com/net/download)します。

### [<a name="windows"></a>Windows](#tab/windows)

インストール[F# のサポートを使用した Visual Studio](#install-f-with-visual-studio)します。 これにより、書き込み、コンパイル、および F# コードの実行に必要なすべてのコンポーネントがインストールされます。

インストールことも、 [.NET Core SDK](https://www.microsoft.com/net/download/)します。

---

その後[Visual Studio Code](https://code.visualstudio.com)をインストールします。

次に、「ionide の概要」の検索と拡張機能アイコンをクリックします。

Visual Studio Code での F# サポートが必要な唯一のプラグイン[ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)します。 ただし、インストールすることも[Ionide フェイク](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)を取得する[フェイク](https://fsharp.github.io/FAKE/)サポートと[Ionide パケット](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)を取得する[パケットを作成](https://fsprojects.github.io/Paket/)をサポートします。 偽の追加 F# コミュニティのツールをプロジェクトのビルドとの依存関係をそれぞれ管理は、パケットを作成します。
