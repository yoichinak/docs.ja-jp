---
title: F# をインストールする
description: お客様の環境に基づいて、F# をインストールする方法について説明します。
ms.date: 09/05/2019
ms.openlocfilehash: dffa30eac0bdb59c85a66dca6cafd62b25daa572
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855804"
---
# <a name="install-f"></a>F のインストール\#

環境に応じて、複数の方法で F# をインストールできます。

## <a name="install-f-with-visual-studio"></a>Visual Studio で F# をインストールする

[Visual studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)を初めてダウンロードする場合は、最初に visual studio インストーラーをインストールします。 インストーラーから適切な SKU の Visual Studio をインストールします。 既にインストールされている場合は、 **[変更]** をクリックします。

次に、ワークロードの一覧が表示されます。 選択**ASP.NET および web 開発**F# サポートおよび ASP.NET Core プロジェクトの .NET Core のサポートがインストールされます。

次に、右下にある **[変更]** をクリックします。  これにより、選択したすべてのものがインストールされます。 クリックして、F# 言語サポートと Visual Studio 2017 を開くことができますし、**起動**します。

## <a name="install-f-with-visual-studio-for-mac"></a>Visual Studio for Macで F# をインストールする

F# は、選択した構成に関係なく、[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)にデフォルトでインストールされます。

インストールが完了したら、[Visual Studio の起動] を選択します。 また、macOS で Finder を使用して起動することもできます。

## <a name="install-f-with-visual-studio-code"></a>Visual Studio Code で F# のインストールします。

プロジェクトテンプレートを使用するには、 [git をインストール](https://git-scm.com/download)し、パスに使用できるようにする必要があります。 コマンドプロンプトで「」 `git --version`と入力し、 **enter**キーを押すと、正しくインストールされていることを確認できます。

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com)は[F# Interactive](../tutorials/fsharp-interactive/index.md)サポートに使用されます。 MacOS に Mono をインストールする最も簡単な方法は、Homebrew を使用することです。 ターミナルに次のように入力します。

```console
brew install mono
```

また、 [.NET Core SDK](https://dotnet.microsoft.com/download)もインストールします。

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com)は[F# Interactive](../tutorials/fsharp-interactive/index.md)サポートに使用されます。 Debian または Ubuntu を使用している場合は、次のものを使用できます。

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

また、 [.NET Core SDK](https://dotnet.microsoft.com/download)もインストールします。

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

インストール[F# のサポートを使用した Visual Studio](#install-f-with-visual-studio)します。 これにより、書き込み、コンパイル、および F# コードの実行に必要なすべてのコンポーネントがインストールされます。

また、 [.NET Core SDK](https://dotnet.microsoft.com/download)もインストールします。

---

その後、 [Visual Studio Code](https://code.visualstudio.com) をインストールする必要があります。

次に、[拡張機能] アイコンをクリックし、"Ionide" を検索します。

Visual Studio Code での F# サポートが必要な唯一のプラグイン[ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)します。 ただし、Ionide をインストールして、[偽](https://fsharp.github.io/FAKE/)[の](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)サポートと[Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)を取得し、[パケット](https://fsprojects.github.io/Paket/)のサポートを取得することもできます。 偽の追加 F# コミュニティのツールをプロジェクトのビルドとの依存関係をそれぞれ管理は、パケットを作成します。

## <a name="install-f-on-a-build-server"></a>ビルドサーバーに F＃ をインストールする

.Net Core または .net SDK を .NET Framework を経由で使用している場合は、.NET SDK をビルドサーバーにインストールするだけです。 必要なものはすべて揃っています。

.NET Framework を使用していて、.NET SDK を使用して**いない**場合は、 [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)を Windows Server にインストールする必要があります。 インストーラーで、 **[.net デスクトップビルドツール]** を選択し、インストーラーメニューの右側にある **F#コンパイラ**コンポーネントを選択します。
