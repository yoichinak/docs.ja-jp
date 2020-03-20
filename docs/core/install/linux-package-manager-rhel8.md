---
title: Linux RHEL 8 に .NET Core をインストールする - パッケージ マネージャー - .NET Core
description: パッケージ マネージャーを使用して、.NET Core SDK とランタイムを RHEL 8 にインストールします。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 054494a9b77e1c7803e42c947e067d3eb290f73c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "78849796"
---
# <a name="rhel-8-package-manager---install-net-core"></a>RHEL 8 パッケージ マネージャー - .NET Core をインストールする

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

この記事では、パッケージ マネージャーを使用して RHEL 8 に .NET Core をインストールする方法について説明します。

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
