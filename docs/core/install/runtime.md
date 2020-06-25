---
title: Windows、Linux、および macOS に .NET Core ランタイムをインストールする - .NET Core
description: Windows、Linux、および macOS に .NET Core をインストールする方法について説明します。 .NET Core アプリの実行に必要な依存関係を確認します。
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d3f7083366e2019d01884b5dff6e60d05ed565dd
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768288"
---
# <a name="install-the-net-core-runtime"></a>.NET Core ランタイムのインストール

この記事では、.NET Core ランタイムをダウンロードしてインストールする方法について説明します。 .Net Core ランタイムは、.NET Core で作成されたアプリを実行するために使用されます。

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>インストーラーを使用してインストールする

Windows には、.NET Core 3.1 ランタイムのインストールに使用できるスタンドアロン インストーラーが用意されています。

- [x64 (64 ビット) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32 ビット) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>インストーラーを使用したインストール

macOS には、.NET Core 3.1 ランタイムのインストールに使用できるスタンドアロン インストーラーが用意されています。

- [x64 (64 ビット) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>手動でダウンロードしてインストールする

.NET Core 用 macOS インストーラーの代わりに、ランタイムをダウンロードして手動でインストールすることもできます。

ランタイムをインストールし、.NET Core CLI コマンドをターミナルで使用できるようにするには、最初に .NET Core のバイナリ リリースを[ダウンロード](#all-net-core-downloads)します。 次に、ターミナルを開き、以下のコマンドを実行します。 ランタイムが `~/Downloads/dotnet-runtime.pkg` ファイルにダウンロードされることを前提としています。

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a>Linux にインストールする

この記事は間もなく削除されます。 現在、「[Linux に .NET Core をインストールする](linux.md)」に置き換えられています。

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>PowerShell オートメーションを使用してインストールする

[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの自動化および管理者以外によるインストールに使用されます。 スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。

スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。 `Channel` スイッチを指定することで、特定のリリースを選択できます。 ランタイムをインストールするには、`Runtime` スイッチを含めます。 それ以外の場合は、スクリプトによって [SDK](sdk.md) がインストールされます。

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> 上のコマンドでは、互換性を最大限に高めるために ASP.NET Core ランタイムをインストールします。 ASP.NET Core ランタイムには、標準の .NET Core ランタイムも含まれています。

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

## <a name="install-with-bash-automation"></a>bash オートメーションを使用してインストールする

[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの自動化および管理者以外によるインストールに使用されます。 スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。

スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。 `current` スイッチを指定することで、特定のリリースを選択できます。 ランタイムをインストールするには、`runtime` スイッチを含めます。 それ以外の場合は、スクリプトによって [SDK](sdk.md) がインストールされます。

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> 上のコマンドでは、互換性を最大限に高めるために ASP.NET Core ランタイムをインストールします。 ASP.NET Core ランタイムには、標準の .NET Core ランタイムも含まれています。

::: zone-end

## <a name="all-net-core-downloads"></a>すべての .NET Core のダウンロード

次のいずれかのリンクを使用して、.NET Core を直接ダウンロードしてインストールすることができます。

- [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。 同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。

.NET Core は Docker コンテナー内で実行できます。 公式の .NET Core Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET Core の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet-core/)で見つけられます。 各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。

Microsoft は、特定のシナリオに対応したイメージを用意しています。 たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。

Docker コンテナー内で .NET Core を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)に関するページを参照してください。

## <a name="next-steps"></a>次の手順

- [.NET Core が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md)。
