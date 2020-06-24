---
title: SLES に .NET Core をインストールする - .NET Core
description: SLES に .NET Core SDK と .NET Core ランタイムをインストールするさまざまな方法を示します。
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9816e1f0253be58dc04c1302f334a7ea0b810810
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768400"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a>SLES に .NET Core SDK または .NET Core ランタイムをインストールする

.NET Core は SLES でサポートされています。 この記事では、SLES に .NET Core をインストールする方法について説明します。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a>サポートされているディストリビューション

次の表は、SLES 12 SP2 と SLES 15 の両方で現在サポートされている .NET Core リリースの一覧です。 これらのバージョンは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、SLES のバージョンがサポート終了になるまでサポートされます。

- ✔️ は、SLES または .NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、SLES または .NET Core のバージョンがその SLES のリリースではサポートされていないことを示しています。
- SLES のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](#sles-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [12 SP2](#sles-12-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

次のバージョンの .NET Core は、サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>その他のバージョンをインストールする方法

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a>SLES 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

現時点では、SLES 15 Microsoft リポジトリ セットアップ パッケージによって "*microsoft-prod.repo*" ファイルが間違ったディレクトリにインストールされるため、zypper が .NET Core パッケージを見つけることができません。 この問題を解決するには、正しいディレクトリにシンボリックリンクを作成します。

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a>SLES 12 ✔️

.NET Core では、SLES 12 ファミリの最小要件として SP2 が必要です。

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>パッケージ マネージャーのトラブルシューティング

このセクションでは、パッケージ マネージャーを使用して .NET Core をインストールするときに発生する可能性のある一般的なエラーについて説明します。

### <a name="failed-to-fetch"></a>フェッチできない

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>依存関係

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a>スクリプトでのインストール

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動インストール

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>次の手順

- [チュートリアル: Visual Studio Code を使用して .NET Core SDK でコンソール アプリケーションを作成する](../tutorials/with-visual-studio-code.md)
