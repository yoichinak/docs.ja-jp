---
title: Ubuntu 19.04 パッケージ マネージャーに .NET Core をインストールする - .NET Core
description: パッケージ マネージャーを使用して、Ubuntu 19.04 に .NET Core SDK とランタイムをインストールします。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: a0a6cedb6dbf572750fcc238aff59b7f66edf44f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134137"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a>Ubuntu 19.04 パッケージ マネージャー - .NET Core のインストール

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

この記事では、パッケージ マネージャーを使用して Ubuntu 19.04 に .NET Core をインストールする方法について説明します。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Microsoft キーとフィードを登録する

.NET をインストールする前に、次のことを行う必要があります。

- Microsoft キーを登録する。
- 製品リポジトリを登録する。
- 必要な依存関係をインストールする。

これは、コンピューターごとに 1 回実行する必要があるだけです。

ターミナルを開き、次のコマンドを実行します。

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK をインストールする

インストール可能な製品を更新してから、.NET Core SDK をインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> "**パッケージ dotnet-sdk-3.1 が見つかりません**" のようなエラー メッセージが表示される場合は、「[パッケージ マネージャーのトラブルシューティング](#troubleshoot-the-package-manager)」セクションを参照してください。

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core ランタイムをインストールする

インストール可能な製品を更新してから、ASP.NET Core ランタイムをインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> "**パッケージ aspnetcore-runtime-3.1 が見つかりません**" のようなエラー メッセージが表示される場合は、「[パッケージ マネージャーのトラブルシューティング](#troubleshoot-the-package-manager)」セクションを参照してください。

## <a name="install-the-net-core-runtime"></a>.NET Core ランタイムをインストールする

インストール可能な製品を更新してから、.NET Core ランタイムをインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> "**パッケージ dotnet-runtime-3.1 が見つかりません**" のようなエラー メッセージが表示される場合は、「[パッケージ マネージャーのトラブルシューティング](#troubleshoot-the-package-manager)」セクションを参照してください。

## <a name="how-to-install-other-versions"></a>その他のバージョンをインストールする方法

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>パッケージ マネージャーのトラブルシューティング

このセクションでは、パッケージ マネージャーを使用して .NET Core をインストールするときに発生する可能性のある一般的なエラーについて説明します。

### <a name="unable-to-locate"></a>見つからない

"**パッケージ <.NET Core パッケージ> が見つかりません**" のようなエラー メッセージが表示される場合は、次のコマンドを実行します。

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

それでも解決しない場合は、次のコマンドを使用して手動インストールを実行できます。

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>フェッチできない

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
