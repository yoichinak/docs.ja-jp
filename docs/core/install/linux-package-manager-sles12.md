---
title: SLES 12 に .NET Core をインストールする - パッケージ マネージャー - .NET Core
description: パッケージ マネージャーを使用して、.NET Core SDK とランタイムを SLES 12 にインストールします。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 8358107c682274fc2b75bf72689eaa4b168a86c5
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134218"
---
# <a name="sles-12-package-manager---install-net-core"></a>SLES 12 パッケージ マネージャー - .NET Core をインストールする

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

この記事では、パッケージ マネージャーを使用して SLES 12 に .NET Core をインストールする方法について説明します。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Microsoft キーとフィードを登録する

.NET をインストールする前に、次のことを行う必要があります。

- Microsoft キーを登録する。
- 製品リポジトリを登録する。
- 必要な依存関係をインストールする。

これは、コンピューターごとに 1 回実行する必要があるだけです。

ターミナルを開き、次のコマンドを実行します。

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK をインストールする

インストール可能な製品を更新してから、.NET Core SDK をインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core ランタイムをインストールする

インストール可能な製品を更新してから、ASP.NET ランタイムをインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>.NET Core ランタイムをインストールする

インストール可能な製品を更新してから、.NET Core ランタイムをインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>その他のバージョンをインストールする方法

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>パッケージ マネージャーのトラブルシューティング

このセクションでは、パッケージ マネージャーを使用して .NET Core をインストールするときに発生する可能性のある一般的なエラーについて説明します。

### <a name="failed-to-fetch"></a>フェッチできない

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
