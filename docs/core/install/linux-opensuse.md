---
title: openSUSE に .NET Core をインストールする - .NET Core
description: openSUSE に .NET Core SDK と .NET Core ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 3a2ff1ca1519428f42c88048dde22aa11baaaa01
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324750"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a>openSUSE に .NET Core SDK または .NET Core ランタイムをインストールする

.NET Core は openSUSE でサポートされています。 この記事では、openSUSE に .NET Core をインストールする方法について説明します。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>サポートされているディストリビューション

次の表は、openSUSE 15 で現在サポートされている .NET Core リリースの一覧です。 これらのバージョンは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、openSUSE のバージョンがサポート終了になるまでサポートされます。

- ✔️ は、openSUSE または .NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、openSUSE または .NET Core のバージョンがその openSUSE のリリースではサポートされていないことを示しています。
- openSUSE のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](#opensuse-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

次のバージョンの .NET Core は、サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>その他のバージョンをインストールする方法

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a>openSUSE 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>パッケージ マネージャーのトラブルシューティング

このセクションでは、パッケージ マネージャーを使用して .NET Core をインストールするときに発生する可能性のある一般的なエラーについて説明します。

### <a name="failed-to-fetch"></a>フェッチできない

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>依存関係

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a>スクリプトでのインストール

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動インストール

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>次の手順

- [チュートリアル: Visual Studio Code を使用して .NET Core SDK でコンソール アプリケーションを作成する](../tutorials/with-visual-studio-code.md)
