---
title: dotnet-install スクリプト
description: .NET Core CLI ツールと共有ランタイムをインストールする dotnet-install スクリプトについて説明します。
ms.date: 01/16/2019
ms.openlocfilehash: 6404a8332a7196f0e6fdfe649c2c180970390775
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204796"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet-install スクリプト参照

## <a name="name"></a>name

`dotnet-install.ps1` | `dotnet-install.sh` - .NET Core CLI ツールと共有ランタイムをインストールするために使うスクリプトです。

## <a name="synopsis"></a>構文

Windows の場合:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

macOS/Linux の場合:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>説明

`dotnet-install` スクリプトは、.NET Core CLI ツールや共有ランタイムが含まれる .NET Core SDK の非管理者インストールを実行するために使用されます。

[.NET Core のメインの Web サイト](https://dot.net)でホストされる安定したバージョンを使用することをお勧めします。 スクリプトへの直接パスは次のとおりです。

* <https://dot.net/v1/dotnet-install.sh> (Bash、UNIX)
* <https://dot.net/v1/dotnet-install.ps1> (PowerShell、Windows)

これらのスクリプトの主な有用性は、オートメーションのシナリオと管理者以外のインストールにおいてです。 2 つのスクリプトがあります。1 つは Windows 上で動作する PowerShell スクリプトで、もう 1 つは Linux/macOS 上で動作する bash スクリプトです。 スクリプトの動作は両方とも同じです。 bash スクリプトは PowerShell のスイッチも読み取るので、Linux/macOS システムのスクリプトで PowerShell のスイッチを使うことができます。

インストール スクリプトは CLI ビルド ドロップから ZIP/tarball ファイルをダウンロードし、既定の場所または `-InstallDir|--install-dir` で指定された場所へのインストールに進みます。 既定では、インストール スクリプトは SDK をダウンロードしてインストールします。 共有ランタイムの取得だけを行いたい場合は、`--runtime` 引数を指定します。

既定では、スクリプトはインストールの場所を現在のセッションの $PATH に追加します。 `--no-path` 引数を指定することによってこの既定の動作をオーバーライドします。

スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールします。

`--version` 引数を使用して、特定のバージョンをインストールすることができます。 バージョンは 3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。 指定しない場合は、`latest` バージョンが使用されます。

## <a name="options"></a>オプション

* **`-Channel <CHANNEL>`**

  インストールのソース チャネルを指定します。 次の値を指定できます。

  * `Current` - 最新リリース。
  * `LTS` - 長期的なサポート チャネル (サポートされている最新リリース)。
  * 特定のリリースを表す X.Y 形式の 2 部構成のバージョン (たとえば、`2.0` または `1.0`)。
  * ブランチ名。 たとえば、`release/2.0.0`、`release/2.0.0-preview2`、`master` (夜間リリース用)

  既定値は `LTS` です。 .NET のサポート チャネルの詳細については、「[.NET Support Policy](https://www.microsoft.com/net/platform/support-policy#dotnet-core)」(.NET のサポート ポリシー) ページを参照してください。

* **`-Version <VERSION>`**

  特定のビルド バージョンを表します。 次の値を指定できます。

  * `latest` - チャネルの最新ビルド (`-Channel` オプションで使用)。
  * `coherent` - チャネルの最新のコヒーレント ビルド。最新の安定版パッケージの組み合わせを使用します (ブランチ名の `-Channel` オプションで使用)。
  * 特定のビルド バージョンを表す X.Y.Z 形式の 3 部構成のバージョン。`-Channel` オプションよりも優先されます。 たとえば、`2.0.0-preview2-006120` のように指定します。

  指定しない場合、`-Version` の既定値は `latest` です。

* **`-InstallDir <DIRECTORY>`**

  インストール パスを指定します。 存在しない場合は、ディレクトリが作成されます。 既定値は *%LocalAppData%\Microsoft\dotnet*です。 バイナリは、このディレクトリに直接配置されます。

* **`-Architecture <ARCHITECTURE>`**

  インストールする .NET Core バイナリのアーキテクチャです。 指定できる値は、`<auto>`、`amd64`、`x64`、`x86`、`arm64`、および `arm` です。 既定値は `<auto>` です。これは実行中の OS アーキテクチャを示します。

* **`-SharedRuntime`**

  > [!NOTE]
  > このパラメーターは非推奨であり、今後のバージョンのスクリプトでは削除される可能性があります。 別の方法として、`Runtime` オプションを使用することをお勧めします。

  SDK 全体ではなく共有ランタイム ビットのみがインストールされます。 これは、`-Runtime dotnet` を指定することと同じです。

* **`-Runtime <RUNTIME>`**

  SDK 全体ではなく共有ランタイムのみがインストールされます。 次の値を指定できます。

  * `dotnet` - `Microsoft.NETCore.App` 共有ランタイム。
  * `aspnetcore` - `Microsoft.AspNetCore.App` 共有ランタイム。

* **`-DryRun`**

  設定すると、スクリプトでインストールは実行されません。 代わりに、現在要求されているバージョンの .NET Core CLI を一貫してインストールするために使用するコマンド ラインが表示されます。 たとえば、バージョン `latest` を指定すると、そのバージョンのリンクが表示されるので、ビルド スクリプトで確定的にこのコマンドを使用できます。 また、自分でインストールまたはダウンロードしたい場合、バイナリの場所も表示されます。

* **`-NoPath`**

  設定すると、インストール フォルダーは現在のセッションのパスにはエクスポートされません。 既定では、スクリプトによって PATH が変更されます。その結果、インストール後すぐに CLI ツールを使用できるようになります。

* **`-Verbose`**

  診断情報を表示します。

* **`-AzureFeed`**

  Azure フィードの URL をインストーラーに指定します。 この値は変更しないことをお勧めします。 既定値は `https://dotnetcli.azureedge.net/dotnet` です。

* **`-UncachedFeed`**

  このインストーラーで使用されている、キャッシュされていないフィードの URL を変更することを許可します。 この値は変更しないことをお勧めします。

* **`-NoCdn`**

  [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) からのダウンロードを無効にし、キャッシュされていないフィードを直接使用します。

* **`-FeedCredential`**

  Azure フィードに付加するクエリ文字列として使用されます。 非公開の BLOB ストレージ アカウントを使用するように URL を変更することができます。

* **`-ProxyAddress`**

  設定すると、インストーラーで Web 要求を行うときにプロキシが使われます。 (Windows でのみ有効)

* **`ProxyUseDefaultCredentials`**

  設定すると、プロキシ アドレスの使用時に、インストーラーでは現在のユーザーの資格情報が使用されます。 (Windows でのみ有効)

* **`-SkipNonVersionedFiles`**

  *dotnet.exe* など、バージョン管理されていないファイルが既に存在する場合は、そのインストールをスキップします。

* **`-Help`**

  スクリプトのヘルプを出力します。

## <a name="examples"></a>使用例

* 最新の長期サポート (LST) バージョンを既定の場所にインストールします。

  Windows の場合:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux の場合:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* 2.0 チャネルから、最新バージョンを指定した場所にインストールします。

  Windows の場合:

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  macOS/Linux の場合:

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* 共有ランタイムの 1.1.0 バージョンをインストールします。

  Windows の場合:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  macOS/Linux の場合:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

* スクリプトを入手し、会社のプロキシの背後に 2.1.2 バージョンをインストールします (Windows のみ)。

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* スクリプトを入手し、.NET Core CLI の 1 行コードのサンプルをインストールします。

  Windows の場合:

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux の場合:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>関連項目

- [.NET Core のリリース](https://github.com/dotnet/core/releases)
- [.NET Core ランタイムと SDK ダウンロード アーカイブ](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
