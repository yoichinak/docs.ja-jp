---
title: Linux における .NET Core の前提条件
description: Linux マシンで .NET Core アプリケーションを開発、展開、および実行するために必要なサポートされている Linux のバージョンと .NET Core の依存関係。
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 31c53b2cc0fe576e56685f4a5561258136fd2541
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116579"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Linux における .NET Core の前提条件

この記事では、Linux で .NET Core アプリケーションを開発するために必要な依存関係を示します。 後述のサポートされている Linux ディストリビューション/バージョンと依存関係は、Linux で .NET Core アプリを開発する次の 2 つの方法に適用されます。

* [好みのエディターでのコマンドライン](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> .NET Core SDK パッケージは、運用サーバー/環境には必要はありません。 運用環境に展開されるアプリに必要なものは、.NET Core ランタイム パッケージだけです。 .NET Core ランタイムは自己完結型の展開の一部としてアプリと供に展開されますが、フレームワークに依存して展開されるアプリでは個別に展開する必要があります。 フレームワークに依存する展開と自己完結型の展開について詳しくは、「[.NET Core アプリケーションの展開](./deploying/index.md)」をご覧ください。 具体的なガイドラインについては、「[Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」(自己完結型 Linux アプリケーション) もご覧ください。

## <a name="supported-linux-versions"></a>サポートされている Linux バージョン

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.x は、1 つのオペレーティング システムとして Linux を扱います。 サポートされている Linux ディストリビューション用に、1 つの Linux ビルド (チップ アーキテクチャあたり) があります。 

ダウンロード リンクと詳細については、[.NET Core 2.2 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.2)または [.NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1) のダウンロードのページを参照してください。

.NET Core 2.x は、次の Linux ディストリビューション/バージョンでサポートされています。

* Red Hat Enterprise Linux 7、6 - 64 ビット (`x86_64` または `amd64`)
* CentOS 7 - 64 ビット (`x86_64` または `amd64`) 
* Oracle Linux 7 - 64 ビット (`x86_64` または `amd64`) 
* Fedora 28、27 - 64 ビット (`x86_64` または `amd64`) 
* Debian 9 (64 ビット、`arm32`), 8.7 以降のバージョン - 64 ビット (`x86_64` または `amd64`)
* Ubuntu 18.04 (64 ビット、`arm32`)、16.04、14.04 - 64 ビット (`x86_64` または `amd64`)
* Linux Mint 18、17 - 64 ビット (`x86_64` または `amd64`)
* openSUSE 42.3 以降のバージョン - 64 ビット (`x86_64` または `amd64`)
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 以降 - 64 ビット (`x86_64` または `amd64`)
* Alpine Linux 3.7 以降のバージョン - 64 ビット (`x86_64` または `amd64`)

.NET Core 2.1 と .NET Core 2.2 がサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS バージョン、ライフサイクル ポリシー リンクの完全なリストについては、[.NET Core 2.1 がサポートされる OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)と [.NET Core 2.2 がサポートされている OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)に関するページを参照してください。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

ダウンロード リンクと詳細については、[.NET Core 1.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/1.1)または [.NET Core 1.0](https://dotnet.microsoft.com/download/dotnet-core/1.0) のダウンロードのページを参照してください。

.NET Core 1.x は、次の Linux 64 ビット (`x86_64` または `amd64`) ディストリビューション/バージョンでサポートされています。

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1)、27
* Debian 8.2 以降のバージョン
* Ubuntu 18.04 (.NET Core 1.1)、16.04、14.04
* Linux Mint 17
* openSUSE 42.3 以降のバージョン (.NET Core 1.1)

.NET Core 1.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET Core 3.0 Preview 1](#tab/netcore30)

.NET Core 3.0 Preview 1 は、1 つのオペレーティング システムとして Linux を扱います。 サポートされている Linux ディストリビューション用に、1 つの Linux ビルド (チップ アーキテクチャあたり) があります。 

ダウンロード リンクと詳細については、[.NET Core 3.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.0) ページを参照してください。

.NET Core 3.0 Preview 1 は、次の Linux ディストリビューション/バージョンでサポートされています。 

OS                            | Version               | アーキテクチャ  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | X64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | X64
Fedora                        | 28                    | X64
Debian                        | 9                     | x64、ARM32\*、ARM64\*
Ubuntu                        | 16.04+、18.04+        | x64、ARM32\*、ARM64\*
Linux Mint                    | 18                    | X64
openSUSE                      | 42.3+                 | X64
SUSE Enterprise Linux (SLES)  | 12 SP2+               | X64
Alpine Linux                  | 3.8+                  | x64、ARM64

\* ARM32 および ARM64 は、Debian 9 以降および Ubuntu 16.04 以降でサポートされています。 これらのディストリビューションのこれより古いバージョンでは、ARM チップはサポートされていません。

.NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS バージョン、ライフサイクル ポリシー リンクの完全なリストについては、[.NET Core 3.0 がサポートされる OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)に関するページを参照してください。

ARM64 で .NET Core 3.0 をインストールする方法の詳細については、「[Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)」 (Linux ARM64 での .NET Core 3.0 のインストール) を参照してください。

---

## <a name="linux-distribution-dependencies"></a>Linux ディストリビューションの依存関係

次に例を示します。 選択した Linux ディストリビューションで、バージョンと名前が多少異なる場合があります。

### <a name="ubuntu"></a>Ubuntu

Ubuntu ディストリビューションには、次のライブラリがインストールされている必要があります。

* liblttng-ust0
* libcurl3 (14.x および 16.x 用)
* libcurl4 (18.x 用)
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (14.x 用)
* libicu55 (16.x 用)
* libicu57 (17.x 用)
* libicu60 (18.x 用)

.NET Core 2.1 より前のバージョンには、次の依存関係も必要です。

* libunwind8
* libuuid1

### <a name="centos-and-fedora"></a>CentOS と Fedora

CentOS ディストリビューションには、次のライブラリがインストールされている必要があります。

* lttng-ust
* libcurl
* openssl-libs
* krb5-libs
* libicu
* zlib

Fedora ユーザー:ご使用の openssl のバージョンが 1.1 以降の場合は、compat-openssl10 をインストールする必要があります。

.NET Core 2.1 より前のバージョンには、次の依存関係も必要です。

* libunwind
* libuuid

依存関係の詳細については、「[Self-contained Linux applications (自己完結型 Linux アプリケーション)](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」をご覧ください。

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>ネイティブ インストーラーを使用した .NET Core の依存関係のインストール

.NET Core ネイティブ インストーラーは、サポートされている Linux ディストリビューション/バージョンに利用できます。 このネイティブ インストーラーは、サーバーへの admin (sudo) アクセスを必要とします。 ネイティブ インストーラーを使用することの利点は、.NET Core ネイティブの依存関係がすべてインストールされることです。 また、ネイティブ インストーラーでは、.NET Core SDK もシステム全体にインストールします。

Linux では、2 つのインストーラー パッケージから選択できます。

* フィードベースのパッケージ マネージャー (Ubuntu では apt-get、CentOS/RHEL では yum など) を使用する
* パッケージ自体 (DEB または RPM) を使用する

### <a name="scripting-installs-with-the-net-core-installer-script"></a>.NET Core インストーラー スクリプトを使用したスクリプトのインストール

[dotnet-install スクリプト](./tools/dotnet-install-script.md)は、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。 このスクリプトは <https://dot.net/v1/dotnet-install.sh> からダウンロードできます。

スクリプトは、既定で最新の "LTS" のバージョン (現在は .NET Core 1.1) をインストールします。 NET Core 2.1 をインストールするには、次のスイッチを使用してスクリプトを実行します。

```bash
./dotnet-install.sh -c Current
```

インストーラーの bash スクリプトは、自動化シナリオと管理者以外のインストールで使用されます。 このスクリプトは、PowerShell のスイッチも読み取るので、Linux/OS X システムのスクリプトで使うことができます。

## <a name="troubleshoot"></a>トラブルシューティング

サポートされている Linux ディストリビューション/バージョンへの .NET Core のインストールに問題がある場合は、インストールしているディストリビューション/バージョンに関する以下のトピックをご覧ください。

* [.NET Core 3.0 の既知の問題](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [.NET Core 2.2 の既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [.NET Core 2.1 の既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [.NET Core 1.1 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [.NET Core 1.0 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0)
