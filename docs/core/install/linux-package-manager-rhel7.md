---
title: Linux RHEL 7 に .NET Core をインストールする - パッケージ マネージャー - .NET Core
description: パッケージ マネージャーを使用して、.NET Core SDK とランタイムを RHEL 7 にインストールします。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1f1372b32c7b2471a96492d48aab5533dadb64a
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134199"
---
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 パッケージ マネージャー - .NET Core をインストールする

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

この記事では、パッケージ マネージャーを使用して RHEL 7 に .NET Core をインストールする方法について説明します。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>ご利用の Red Hat サブスクリプションを登録する

Red Hat から RHEL に .NET Core をインストールするには、まず、Red Hat Subscription Manager を使用して登録する必要があります。 ご利用のシステム上でこれがまだ行われていない場合、または不明な場合は、[.NET Core 向け Red Hat 製品ドキュメント](https://access.redhat.com/documentation/net_core/)を参照してください。

## <a name="install-the-net-core-sdk"></a>.NET Core SDK をインストールする

Subscription Manager に登録すると、.NET Core SDK をインストールして有効にする準備が整います。 ご利用のターミナルで、次のコマンドを実行することで、RHEL 7 dotnet チャネルを有効にしてインストールします。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core ランタイムをインストールする

Subscription Manager に登録すると、ASP.NET Core ランタイムをインストールして有効にする準備が整います。 ご利用のターミナルで、次のコマンドを実行します。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a>.NET Core ランタイムのインストール

Subscription Manager に登録すると、.NET Core ランタイムをインストールして有効にする準備が整います。 ご利用のターミナルで、次のコマンドを実行します。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a>参照

- [Red Hat Enterprise Linux 7 での .NET Core 3.1 の使用](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
