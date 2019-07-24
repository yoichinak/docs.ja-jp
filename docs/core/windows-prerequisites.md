---
title: Windows における .NET Core の前提条件
description: Windows コンピューターで .NET Core アプリケーションを開発および実行する場合に必要な依存関係について説明します。
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 1921ef565c2d04624009f7684e439ddba1cdf57e
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331077"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows における .NET Core の前提条件

この記事では、Windows 上で .NET Core アプリケーションを実行するためにサポートされる OS のバージョンについて説明します。 後述のサポート対象 OS のバージョンと依存関係は、Windows で .NET Core アプリを開発する次の 3 つの方法に適用されます。

* [コマンド ライン](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

また、Visual Studio 2017 を使用して Windows 上で開発している場合、.NET Core 開発でサポートされている最小バージョンの詳細については、「[Visual Studio 2017 の前提条件](#prerequisites-with-visual-studio-2017)」セクションを参照してください。

## <a name="net-core-supported-operating-systems"></a>.NET Core がサポートされたオペレーティング システム

次の記事では、.NET Core がサポートされたオペレーティング システム (バージョンごと) の完全な一覧を示します。

* [.NET Core 3.0 (Preview)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

ダウンロード リンクと詳細については、最新バージョンをダウンロードするには [.NET ダウンロード](https://dotnet.microsoft.com/download)、以前のバージョンについて [.NET ダウンロードのアーカイブ](https://dotnet.microsoft.com/download/archives#dotnet-core)に関するページを参照してください。

## <a name="net-core-dependencies"></a>.NET Core の依存関係

.NET Core 1.1 以前のバージョンを Windows 10 と Windows Server 2016 よりも前の Windows バージョンで実行する場合、Visual C++ 再頒布可能パッケージが必要です。 この依存関係は、.NET Core インストーラーにより自動でインストールされます。

次の場合には、[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=52685) を手動でインストールする必要があります。

* [インストーラー スクリプト](./tools/dotnet-install-script.md)を使用して .NET Core をインストールする。
* 自己完結型の .NET Core アプリケーションを展開する。
* ソースから製品をビルドする。
* *.zip* ファイルを使用して .NET Core をインストールする。 これにはビルド/CI/CD サーバーを含めることができます。

> [!NOTE]
> **Windows 8.1 以前のバージョン、または Windows Server 2012 R2 以前のバージョンの場合:**
>
> Windows のインストールが最新であり、Windows Update から修正プログラム [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows) をインストールしていることを確認してください。 この更新プログラムがインストールされていない場合は、.NET Core アプリケーションを起動するときに、次のようなエラーが表示されます。`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Windows 7 または Windows Server 2008 R2 の場合:**
>
> KB2999226 に加え、[KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) もインストールされていることを確認します。 この更新プログラムがインストールされていない場合は、.NET Core アプリケーションを起動するときに、次のようなエラーが表示されます。`The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`

## <a name="prerequisites-for-net-core-30-preview-3"></a>.NET Core 3.0 Preview 3 の前提条件

.NET Core 3.0 Preview 3 の前提条件は、.NET Core の他のバージョンと同じです。 ただし、Visual Studio を使用して .NET Core 3.0 プロジェクトを作成する場合は、[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) を使用する必要があります。 Visual Studio 2019 は、Visual Studio の他のバージョンと競合することなく、side-by-side でインストールできます。

## <a name="prerequisites-with-visual-studio-2017"></a>Visual Studio 2017 の前提条件
    
.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。 Visual Studio 2017 では、Windows 上に .NET Core アプリ用の統合開発環境が提供されます。

Visual Studio 2017 での変更の詳細については、[リリース ノート](/visualstudio/releasenotes/vs2017-relnotes)を参照してください。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Visual Studio 2017 で .NET Core 2.2 SDK を使用して .NET Core アプリを開発するには:

 1. ( **[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 バージョン 15.9.0 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。

![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs-2017-workloads.jpg)

**.NET Core クロスプラットフォーム開発**ツールセットをインストールすると、通常、Visual Studio には以前のバージョンの .NET Core SDK がインストールされます。
たとえば、ワークロードをインストールすると、Visual Studio 2017 15.9 には既定で .NET Core 2.1 SDK が使用されます。

.NET Core 2.2 SDK を使用するように Visual Studio を更新するには:

 1. [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) をインストールします。

 1. プロジェクトで最新の .NET Core ランタイムを使用する場合は、次の手順を使用して、既存または新規の .NET Core プロジェクトを .NET Core 2.2 に再ターゲットします。

    * **[プロジェクト]** メニューの **[プロパティ]** をクリックします。
    * **[ターゲット フレームワーク]** 選択メニューで、値を **[.NET Core 2.2]** に設定します。

![ターゲット フレームワーク メニュー項目で [.NET Core 2.2] が選択された Visual Studio 2017 のアプリケーション プロジェクト プロパティのスクリーンショット](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Visual Studio が .NET Core 2.2 SDK で構成されている場合は、次の操作を行うことができます。

* 既存の .NET Core 1.x および 2.x プロジェクトを開き、ビルドし、実行する。
* .NET Core 1.x および 2.x プロジェクトを .NET Core 2.2 に再ターゲットし、ビルドし、実行する。
* .NET Core 2.2 の新しいプロジェクトを作成する。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Visual Studio で .NET Core 1.x アプリを開発するには、( **[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。

![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> .NET Core 1.x の開発に Visual Studio 2015 を使用することはできますが、次の理由からお勧めできません。
  > * .NET Core Tooling は、サポートされていないプレビュー バージョンです。
  > * プロジェクトは、非推奨の project.json ベースです。
>
> プロジェクト形式の変更の詳細については、[変更点の概要](./tools/cli-msbuild-architecture.md)に関するページをご覧ください。

---

<a name="vs-mapping"></a>

> [!TIP]
> お使いの Visual Studio バージョンを確認するには、次の手順を実行します。
>
> * **[ヘルプ]** メニューの **[About Microsoft Visual Studio]** (Microsoft Visual Studio のバージョン情報) を選択します。
> * **[Microsoft Visual Studio のバージョン情報]** ダイアログで、バージョン番号を確認します。
>   * .NET Core 3.0 Preview 3 アプリの場合は、Visual Studio 2019 バージョン 16.0 以降です。
>   * .NET Core 2.2 アプリの場合は、Visual Studio 2017 バージョン 15.9 以降です。
>   * .NET Core 2.1 アプリの場合は、Visual Studio 2017 バージョン 15.7 以降です。
>   * .NET Core 1.x アプリの場合は、Visual Studio 2017 バージョン 15.0 以降です。
