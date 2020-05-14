---
title: Azure .NET および .NET Core 開発者向けツール
description: Windows、Linux、Mac 環境から Azure .NET ライブラリを使い始めるためのツールを入手します。
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2020
ms.locfileid: "81433164"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a>.NET および .NET Core Azure 開発者向けツール

## <a name="sdk-downloads"></a>SDK のダウンロード

.NET 用 Azure ライブラリは [NuGet パッケージ](https://www.nuget.org/packages?q=windowsazureofficial)として実装されています。 Azure サービス別のインストール手順については、[API リファレンス](/dotnet/api/overview/azure/?view=azure-dotnet)に関する記事を参照してください。

## <a name="development-tools"></a>開発ツール

Visual Studio には、Azure サービス向けの多くのツールが組み込まれています。 一部の Azure サービスでは、[Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) などの追加のツールやエミュレーターが提供されています。 必要に応じて、その他のツールについては、Azure サービスのドキュメントを参照してください。

これらの手順では、お使いのオペレーティン グシステムで推奨される最初の開発環境をインストールします。

## <a name="windows"></a>[Windows](#tab/windows)

Visual Studio バージョン 2017 以降には、Azure 開発の組み込みサポートがあります。 以下の手順では、Visual Studio での Azure 開発サポートの有効化について説明します。

Visual Studio 2015 以前の場合は、<a href="vs2015-install.md">これらの手順</a>に従います。

### <a name="step-1-download-visual-studio-2019"></a>手順 1: Visual Studio 2019 のダウンロード

Visual Studio 2019 を既にインストールしてある場合は省略できます。

> [!div class="nextstepaction"]
> [Visual Studio 2019 のダウンロード](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a>手順 2: 2 つの Azure ワークロードをインストールする

Visual Studio インストーラーで、Visual Studio をインストールします (または既存のインストールを変更します)。 *Azure 開発*および *ASP.NET と Web 開発*ワークロードが選択されていることを確認します。

### <a name="step-3-develop-with-net-on-azure"></a>手順 3: Azure で .NET を使って開発する

まず、[最初の ASP.NET Core Web アプリを Azure App Service にデプロイ](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet)します。

## <a name="macos"></a>[macOS](#tab/macos)

Visual Studio for Mac には、Azure での開発に必要なすべてのものが揃っています。

### <a name="step-1-download-visual-studio-for-mac"></a>手順 1: Visual Studio for Mac をダウンロードする

> [!div class="nextstepaction"]
> [Visual Studio for Mac をダウンロードする](https://www.visualstudio.com/vs/visual-studio-mac/)

インストール中に、Azure ツールが既定で選択されます。

## <a name="linux"></a>[Linux](#tab/linux)

Visual Studio Code には、Linux における Azure での開発に必要なすべてのものが揃っています。

### <a name="step-1-download-the-net-core-sdk"></a>手順 1: .NET Core SDK をダウンロードする

.NET Core アプリ用の SDK とコマンド ライン ツールです。

> [!div class="nextstepaction"]
> [.NET Core SDK をダウンロードする](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a>手順 2: Visual Studio Code

任意のオペレーティング システム上で .NET Core アプリを編集し、デバッグします (Windows、Mac、Linux)。

> [!div class="nextstepaction"]
> [Visual Studio Code をダウンロードする](https://code.visualstudio.com)

---
