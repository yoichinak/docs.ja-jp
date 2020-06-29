---
title: Windows、Linux、および macOS に .NET Core SDK をインストールする - .NET Core
description: Windows、Linux、および macOS に .NET Core をインストールする方法について説明します。 .NET Core アプリの開発に必要な依存関係を確認します。
author: adegeo
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a11d1eb3bae6affaa548407cbd68c166a30e99da
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324655"
---
# <a name="install-the-net-core-sdk"></a>.NET Core SDK をインストールする

この記事では、.NET Core SDK をインストールする方法について説明します。 .NET Core SDK は、.NET Core アプリとライブラリの作成に使用されます。 .NET Core ランタイムは、常に SDK と共にインストールされます。

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>インストーラーを使用してインストールする

Windows には、.NET Core 3.1 SDK のインストールに使用できるスタンドアロン インストーラーが用意されています。

- [x64 (64 ビット) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32 ビット) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>インストーラーを使用してインストールする

macOS には、.NET Core 3.1 SDK のインストールに使用できるスタンドアロン インストーラーが用意されています。

- [x64 (64 ビット) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>手動でダウンロードしてインストールする

.NET Core 用 macOS インストーラーの代わりに、SDK をダウンロードして手動でインストールすることもできます。

SDK を抽出し、.NET Core CLI コマンドをターミナルで使用できるようにするには、最初に .NET Core のバイナリ リリースを[ダウンロード](#all-net-core-downloads)します。 次に、ターミナルを開き、以下のコマンドを実行します。 ランタイムが `~/Downloads/dotnet-sdk.pkg` ファイルにダウンロードされることを前提としています。

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a>Linux にインストールする

この記事は間もなく削除されます。 現在、「[Linux に .NET Core をインストールする](linux.md)」に置き換えられています。

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Visual Studio を使用してインストールする

次の表では、Visual Studio を使用して .NET Core アプリを開発している場合に、ターゲットの .NET Core SDK バージョンに基づいて最低限必要な Visual Studio のバージョンを説明します。

| .NET Core SDK のバージョン | Visual Studio のバージョン                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 バージョン 16.4 以降。 |
| 3.0                   | Visual Studio 2019 バージョン 16.3 以降。 |
| 2.2                   | Visual Studio 2017 バージョン 15.9 以降。 |
| 2.1                   | Visual Studio 2017 バージョン 15.7 以降。 |

Visual Studio を既にインストールしてある場合は、次の手順でバージョンを確認できます。

01. Visual Studio を開きます。
01. **[ヘルプ]**  >  **[Microsoft Visual Studio のバージョン情報]** を選択します。
01. **[バージョン情報]** ダイアログで、バージョン番号を確認します。

Visual Studio では、最新の .NET Core SDK とランタイムをインストールできます。

- [Visual Studio をダウンロードします](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。

### <a name="select-a-workload"></a>ワークロードを選択する

Visual Studio をインストールまたは変更するときは、ビルドするアプリケーションの種類に応じて、次の 1 つ以上のワークロードを選択します。

- **[他のツールセット]** セクションの **[.NET Core クロスプラットフォームの開発]** ワークロード。
- **[Web クラウド]** セクションの **[ASP.NET と Web 開発]** ワークロード。
- **[Web クラウド]** セクションの **[Azure の開発]** ワークロード。
- **[デスクトップとモバイル]** セクションの **[.NET デスクトップ開発]** ワークロード。

[![Windows Visual Studio 2019 と .NET Core ワークロード](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="download-and-manually-install"></a>手動でダウンロードしてインストールする

ランタイムを抽出し、.NET Core CLI コマンドをターミナルで使用できるようにするには、最初に .NET Core のバイナリ リリースを[ダウンロード](#all-net-core-downloads)します。 次に、インストール先のディレクトリ (`%USERPROFILE%\dotnet` など) を作成します。 最後に、ダウンロードした zip ファイルをそのディレクトリに抽出します。

既定では、.NET Core CLI コマンドおよびアプリでは、この方法でインストールされた .NET Core は使用されません。使用することを明示的に選択する必要があります。 これを行うには、アプリケーションの起動に使用する環境変数を変更します。

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

この方法では、複数のバージョンを別々の場所にインストールして、その場所を参照する環境変数を使ってアプリケーションを実行することで、アプリケーションによって使用されるインストール場所を明示的に選択できます。

これらの環境変数が設定されている場合でも、.NET Core では、アプリケーションを実行するための最適なフレームワークを選択するときに、既定のグローバル インストールの場所が引き続き考慮されます。 既定値は通常、インストーラーによって使用される `C:\Program Files\dotnet` です。 この環境変数の設定も行うことで、カスタムのインストール場所のみを使用するように、ランタイムに指示できます。

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Visual Studio for Mac を使用してインストールする

Visual Studio for Mac では、 **[.NET Core]** ワークロードを選択すると、.NET Core SDK がインストールされます。 macOS で .NET Core の開発を始めるには、「[Visual Studio 2019 for Mac をインストールする](/visualstudio/mac/installation)」を参照してください。 最新リリースである .NET Core 3.1 の場合は、Visual Studio for Mac 8.4 Preview を使用する必要があります。

[![macOS Visual Studio 2019 for Mac と .NET Core ワークロード機能](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

::: zone pivot="os-windows,os-macos"

## <a name="install-alongside-visual-studio-code"></a>Visual Studio Code と共にインストールする

Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。 Visual Studio Code は、Windows、macOS、Linux で利用できます。

Visual Studio Code には、Visual Studio のような自動化された .NET Core インストーラーは付属していませんが、.NET Core のサポートを簡単に追加できます。

01. [Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。
01. [.NET Core SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet-core)。
01. [Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>PowerShell オートメーションを使用してインストールする

[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、SDK のインストールの自動化および管理者以外によるインストールに使用されます。 スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。

スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。 NET Core の最新リリースをインストールするには、次のスイッチを使用してスクリプトを実行します。

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a>bash オートメーションを使用してインストールする

[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、SDK のインストールの自動化および管理者以外によるインストールに使用されます。 スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。

スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。 NET Core の最新リリースをインストールするには、次のスイッチを使用してスクリプトを実行します。

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>すべての .NET Core のダウンロード

次のいずれかのリンクを使用して、.NET Core を直接ダウンロードしてインストールすることができます。

- [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 3.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET Core 2.2 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。 同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。

.NET Core は Docker コンテナー内で実行できます。 公式の .NET Core Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET Core の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet-core/)で見つけられます。 各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。

Microsoft は、特定のシナリオに対応したイメージを用意しています。 たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。

Docker コンテナー内で .NET Core を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)に関するページを参照してください。

## <a name="next-steps"></a>次の手順

::: zone pivot="os-windows"

- [チュートリアル: Hello World チュートリアル](../tutorials/with-visual-studio.md)。
- [チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。
- [チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。

::: zone-end

::: zone pivot="os-macos"

- [macOS Catalina の公証に対応する](macos-notarization-issues.md)。
- [チュートリアル: macOS での作業を始める](../tutorials/using-on-mac-vs.md).
- [チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。
- [チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。

::: zone-end

::: zone pivot="os-linux"

- [チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。
- [チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。

::: zone-end
