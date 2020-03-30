---
title: Linux RHEL 8 に .NET Core をインストールする - パッケージ マネージャー - .NET Core
description: パッケージ マネージャーを使用して、.NET Core SDK とランタイムを RHEL 8 にインストールします。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b564a386eb67b6e414a832ad3bca10d3d09022bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134190"
---
# <a name="rhel-8-package-manager---install-net-core"></a>RHEL 8 パッケージ マネージャー - .NET Core をインストールする

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

この記事では、パッケージ マネージャーを使用して RHEL 8 に .NET Core をインストールする方法について説明します。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>ご利用の Red Hat サブスクリプションを登録する

Red Hat から RHEL に .NET Core をインストールするには、まず、Red Hat Subscription Manager を使用して登録する必要があります。 ご利用のシステム上でこれがまだ行われていない場合、または不明な場合は、[.NET Core 向け Red Hat 製品ドキュメント](https://access.redhat.com/documentation/net_core/)を参照してください。

## <a name="install-the-net-core-sdk"></a>.NET Core SDK をインストールする

Subscription Manager に登録すると、.NET Core SDK をインストールして有効にする準備が整います。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core ランタイムをインストールする

Subscription Manager に登録すると、ASP.NET Core ランタイムをインストールして有効にする準備が整います。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>.NET Core ランタイムをインストールする

Subscription Manager に登録すると、.NET Core ランタイムをインストールして有効にする準備が整います。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a>関連項目

- [Red Hat Enterprise Linux 8 での .NET Core 3.1 の使用](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
