---
title: F# をインストールする
description: お客様の環境に基づいて、F# をインストールする方法について説明します。
ms.date: 09/05/2019
ms.openlocfilehash: 18b660ff640904119d63f57405752a14f7673e0c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400716"
---
# <a name="install-f"></a>F のインストール\#

複数の方法で F# をインストールと、環境に応じてことができます。

## <a name="install-f-with-visual-studio"></a>Visual Studio を使用した F# のインストールします。

[Visual studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)を初めてダウンロードする場合は、最初に visual studio インストーラーをインストールします。 インストーラーから適切な SKU の Visual Studio をインストールします。 既にインストールされている場合は、 **[変更]** をクリックします。

次に、ワークロードの一覧が表示されます。 選択**ASP.NET および web 開発**F# サポートおよび ASP.NET Core プロジェクトの .NET Core のサポートがインストールされます。

次に、右下にある **[変更]** をクリックします。  これにより、選択したすべてのものがインストールされます。 クリックして、F# 言語サポートと Visual Studio 2017 を開くことができますし、**起動**します。

## <a name="install-f-with-visual-studio-for-mac"></a>Visual Studio for Mac F#と共にインストールする

既定で F# がインストールされている[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)、選択した構成に関係なく。

インストールが完了したら、[Visual Studio の起動] を選択します。 また、macOS で Finder を使用して起動することもできます。

## <a name="install-f-with-visual-studio-code"></a>Visual Studio Code で F# のインストールします。

プロジェクトテンプレートを使用するには、 [git をインストール](https://git-scm.com/download)し、パスに使用できるようにする必要があります。 コマンドプロンプトで「」 `git --version`と入力し、 **enter**キーを押すと、正しくインストールされていることを確認できます。

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com)使用[F# Interactive](../tutorials/fsharp-interactive/index.md)をサポートします。 MacOS に Mono をインストールする最も簡単な方法は、Homebrew を使用することです。 ターミナルに次のように入力します。

```console
brew install mono
```

また、 [.NET Core SDK](https://www.microsoft.com/net/download)もインストールします。

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com)使用[F# Interactive](../tutorials/fsharp-interactive/index.md)をサポートします。 Debian または Ubuntu を使用している場合は、次のものを使用できます。

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

また、 [.NET Core SDK](https://www.microsoft.com/net/download)もインストールします。

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

インストール[F# のサポートを使用した Visual Studio](#install-f-with-visual-studio)します。 これにより、書き込み、コンパイル、および F# コードの実行に必要なすべてのコンポーネントがインストールされます。

また、 [.NET Core SDK](https://www.microsoft.com/net/download/)もインストールします。

---

その後、 [Visual Studio Code](https://code.visualstudio.com)インストールする必要があります。

次に、[拡張機能] アイコンをクリックし、"Ionide" を検索します。

Visual Studio Code での F# サポートが必要な唯一のプラグイン[ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)します。 ただし、Ionide をインストールして、[偽](https://fsharp.github.io/FAKE/)[の](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)サポートと[Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)を取得し、[パケット](https://fsprojects.github.io/Paket/)のサポートを取得することもできます。 偽の追加 F# コミュニティのツールをプロジェクトのビルドとの依存関係をそれぞれ管理は、パケットを作成します。

## <a name="install-f-on-a-build-server"></a>ビルドF#サーバーへのインストール

.Net Core または .net SDK を使用して .NET Framework を使用している場合は、単に .NET SDK をビルドサーバーにインストールする必要があります。 必要なものがすべて揃っています。

.NET Framework を使用していて、.NET SDK を使用して**いない**場合は、 [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)を Windows Server にインストールする必要があります。 インストーラーで、 **[.net デスクトップビルドツール]** を選択し、インストーラーメニューの右側にある **F#コンパイラ**コンポーネントを選択します。
