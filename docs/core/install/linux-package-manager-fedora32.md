---
title: Fedora 32 に .NET Core をインストールする - パッケージ マネージャー - .NET Core
description: パッケージ マネージャーを使用して、.NET Core SDK とランタイムを Fedora 32 にインストールします。
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624952"
---
# <a name="fedora-32-package-manager---install-net-core"></a>Fedora 32 パッケージ マネージャー - .NET Core をインストールする

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

この記事では、パッケージ マネージャーを使用して Fedora 32 に .NET Core をインストールする方法について説明します。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

Fedora 32 以降、.NET Core 3.1 は Fedora の既定のパッケージ リポジトリで利用できます。

## <a name="install-the-net-core-sdk"></a>.NET Core SDK をインストールする

.NET Core SDK をインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core ランタイムをインストールする

ASP.NET ランタイムをインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>.NET Core ランタイムをインストールする

.NET Core ランタイムをインストールします。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>その他のバージョンをインストールする方法

.NET Core のその他のバージョンをインストールするには、[.NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) または [.NET Core Runtime](runtime.md?pivots=os-linux#download-and-manually-install) を手動でインストールします。
