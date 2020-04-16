---
title: Azure .NET および .NET Core 開発者向けツール
description: Windows、Linux、Mac 環境から Azure .NET ライブラリを使い始めるためのツールを入手します。
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2020
ms.locfileid: "81433164"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a>.NET および .NET Core Azure 開発者向けツール

## <a name="sdk-downloads"></a>SDK ダウンロード

NET 用の Azure ライブラリは[、NuGet パッケージ](https://www.nuget.org/packages?q=windowsazureofficial)として実装されます。 Azure サービスで整理されたインストール手順については[、「API リファレンス」を参照](/dotnet/api/overview/azure/?view=azure-dotnet)してください。

## <a name="development-tools"></a>開発ツール

Visual Studio には、多くの Azure サービスに組み込まれているツールがあります。 Azure サービスによっては、Azure[ストレージ エクスプローラー](https://azure.microsoft.com/features/storage-explorer/)などの追加のツールやエミュレーターを利用できます。 必要に応じて、その他のツールについては、Azure サービスのドキュメントを参照してください。

以下の手順では、オペレーティング・システムに推奨される開始開発環境をインストールします。

## <a name="windows"></a>[Windows](#tab/windows)

Visual Studio バージョン 2017 以降では、Azure 開発のサポートが組み込まれています。 以下の手順では、Visual Studio で Azure 開発サポートを有効にする方法について説明します。

Visual Studio 2015 以前のバージョンでは、<a href="vs2015-install.md">次の手順に従ってください</a>。

### <a name="step-1-download-visual-studio-2019"></a>ステップ 1: ダウンロード Visual Studio 2019

既に Visual Studio 2019 がインストールされている場合は、この手順をスキップできます。

> [!div class="nextstepaction"]
> [Visual Studio 2019 をダウンロードする](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a>ステップ 2: 2 つの Azure ワークロードをインストールする

Visual Studio インストーラーで、Visual Studio をインストールします (または既存のインストールを変更します)。 *Azure*開発ワークロードと*ASP.NETワークロード、および Web 開発*ワークロードが選択されていることを確認します。

### <a name="step-3-develop-with-net-on-azure"></a>ステップ 3: Azure で .NET を使って開発する

まず、[最初の ASP.NET Core Web アプリを Azure App Service にデプロイ](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet)します。

## <a name="macos"></a>[macOS](#tab/macos)

Visual Studio for Mac には、Azure での開発に必要なすべてのものが揃っています。

### <a name="step-1-download-visual-studio-for-mac"></a>ステップ 1: Visual Studio for Mac をダウンロードする

> [!div class="nextstepaction"]
> [Visual Studio for Mac をダウンロードする](https://www.visualstudio.com/vs/visual-studio-mac/)

インストール時に、Azure ツールが既定で選択されます。

## <a name="linux"></a>[Linux](#tab/linux)

Visual Studio Code には、Linux における Azure での開発に必要なすべてのものが揃っています。

### <a name="step-1-download-the-net-core-sdk"></a>ステップ 1: .NET Core SDK をダウンロードする

.NET Core アプリ用の SDK とコマンド ライン ツールです。

> [!div class="nextstepaction"]
> [.NET Core SDK をダウンロードする](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a>ステップ 2: Visual Studio Code

任意のオペレーティング システム (Windows、Mac、Linux) 上で .NET Core アプリを編集し、デバッグします。

> [!div class="nextstepaction"]
> [Visual Studio Code をダウンロードする](https://code.visualstudio.com)

---
