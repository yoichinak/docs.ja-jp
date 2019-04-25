---
title: .NET Core コマンドライン インターフェイス (CLI) ツール
description: .NET Core コマンドライン インターフェイス (CLI) ツールとその機能の概要です。
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: e174867ce06e573fc85579183df0196d8276fb37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647425"
---
# <a name="net-core-command-line-interface-cli-tools"></a>.NET Core コマンドライン インターフェイス (CLI) ツール

.NET Core コマンドライン インターフェイス (CLI) は、.NET アプリケーションを開発するための新しいクロスプラットフォーム ツールチェーンです。 CLI は、統合開発環境 (IDE)、エディター、ビルド オーケストレーターなど、上位レベル ツールの基になるものです。

## <a name="installation"></a>インストール

ネイティブ インストーラーを使用するか、インストール シェル スクリプトを使用します。

* ネイティブ インストーラーは主に開発者のコンピューター上で使用され、それぞれサポートされるプラットフォームのネイティブ インストール メカニズムを使用します。たとえば、Ubuntu の場合は DEB パッケージ、Windows の場合は MSI バンドルを使用します。 これらのインストーラーでは、開発者がすぐに使用できる環境をインストールして構成します。ただし、コンピューターに対する管理者特権が必要になります。 インストール手順は、[.NET Core のインストール ガイド](https://aka.ms/dotnetcoregs)で確認できます。
* シェル スクリプトは主に管理者特権なしでツールをインストールするときや、ビルド サーバーを設定するために使用されます。 インストール スクリプトの場合、前提条件はインストールされないため、手動でインストールする必要があります。 詳細については、[インストール スクリプト参照](dotnet-install-script.md)に関するトピックを参照してください。 継続的インテグレーション (CI) ビルド サーバーで CLI を設定する方法については、「[継続的インテグレーション (CI) で .NET Core SDK とツールを使用する](using-ci-with-cli.md)」を参照してください。

既定では、CLI は SxS (side-by-side) 方式でインストールを実行するため、複数のバージョンの CLI ツールが 1 台のコンピューターで共存できます。 複数のバージョンがインストールされたコンピューターで使用するバージョンの決定方法について詳しくは、「[ドライバー](#driver)」セクションを参照してください。

## <a name="cli-commands"></a>CLI コマンド

既定では、次のコマンドがインストールされます。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**基本的なコマンド**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [build](dotnet-build.md)
* [publish](dotnet-publish.md)
* [run](dotnet-run.md)
* [test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [migrate](dotnet-migrate.md)
* [clean](dotnet-clean.md)
* [sln](dotnet-sln.md)
* [help](dotnet-help.md)
* [ストア](dotnet-store.md)

**プロジェクトの変更コマンド**

* [add package](dotnet-add-package.md)
* [add reference](dotnet-add-reference.md)
* [remove package](dotnet-remove-package.md)
* [remove reference](dotnet-remove-reference.md)
* [list reference](dotnet-list-reference.md)

**高度なコマンド**

* [nuget delete](dotnet-nuget-delete.md)
* [nuget locals](dotnet-nuget-locals.md)
* [nuget push](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [dotnet install script](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**基本的なコマンド**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [build](dotnet-build.md)
* [publish](dotnet-publish.md)
* [run](dotnet-run.md)
* [test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [migrate](dotnet-migrate.md)
* [clean](dotnet-clean.md)
* [sln](dotnet-sln.md)

**プロジェクトの変更コマンド**

* [add package](dotnet-add-package.md)
* [add reference](dotnet-add-reference.md)
* [remove package](dotnet-remove-package.md)
* [remove reference](dotnet-remove-reference.md)
* [list reference](dotnet-list-reference.md)

**高度なコマンド**

* [nuget delete](dotnet-nuget-delete.md)
* [nuget locals](dotnet-nuget-locals.md)
* [nuget push](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [dotnet install script](dotnet-install-script.md)

---

CLI では、プロジェクトに追加のツールを指定できるようにする拡張モデルが適用されます。 詳細については、「[.NET Core CLI の拡張モデル](extensibility.md)」を参照してください。

## <a name="command-structure"></a>コマンド構造

CLI コマンド構造は、[ドライバー ("dotnet")](#driver) と[コマンド (または "動詞")](#command-verb)、また場合によってはコマンドの[引数](#arguments)と[オプション](#options)で構成されます。 *my_app* という名前のディレクトリから実行する場合、次のコマンドで示されているように、新しいコンソール アプリの作成やコマンド ラインからの実行など、ほとんどの CLI 操作でこのパターンが見られます。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>ドライバー

ドライバーは [dotnet](dotnet.md) という名前で、2 つの役割 ([フレームワークに依存するアプリ](../deploying/index.md)の実行と、コマンドの実行) があります。 

フレームワークに依存するアプリを実行するには、`dotnet /path/to/my_app.dll` など、ドライバーの後にアプリを指定します。 アプリの DLL が存在するフォルダーからコマンドを実行する場合は、`dotnet my_app.dll` を実行するだけです。 .NET Core ランタイムの特定のバージョンを使用する場合は、`--fx-version <VERSION>` オプションを使用してください (「[dotnet コマンド](dotnet.md)」リファレンスを参照)。

ドライバーにコマンドを指定すると、`dotnet.exe` は CLI コマンドの実行プロセスを開始します。 次に例を示します。

```bash
> dotnet build
```

最初に、ドライバーは使用する SDK のバージョンを決定します。 ['global.json'](global-json.md) がない場合は、利用可能な SDK の最新バージョンを使用します。 コンピューターで最新のプレビューまたは安定したバージョンになります。  SDK バージョンが決定されたら、コマンドを実行します。

### <a name="command-verb"></a>コマンド ("動詞")

コマンド (または "動詞") は、単にアクションを実行するコマンドです。 たとえば、`dotnet build` はコードをビルドします。 `dotnet publish` はコードを発行します。 コマンドは、`dotnet {verb}` 規則を使用してコンソール アプリケーションとして実装されます。

### <a name="arguments"></a>引数

コマンド ラインで渡す引数は、呼び出されたコマンドへの引数です。 たとえば、`dotnet publish my_app.csproj` を実行した場合、`my_app.csproj` 引数は、発行するプロジェクトを示し、`publish` コマンドに渡されます。

### <a name="options"></a>オプション

コマンド ラインで渡すオプションは、呼び出されたコマンドへのオプションです。 たとえば、`dotnet publish --output /build_output` を実行した場合、`--output` オプションとその値は `publish` コマンドに渡されます。

## <a name="migration-from-projectjson"></a>project.json からの移行

Preview 2 ツールを使用して *project.json* ベースのプロジェクトを生成した場合は、リリース ツールで使用するための MSBuild/*.csproj* へのプロジェクトの移行について、「[dotnet-migrate](dotnet-migrate.md)」トピックを参照してください。 Preview 2 ツールのリリースの前に作成された .NET Core プロジェクトの場合は、「[DNX から .NET Core CLI への移行 (project.json)](../migration/from-dnx.md)」のガイダンスに従って手動でプロジェクトを更新してから `dotnet migrate` を使用するか、プロジェクトを直接アップグレードします。

## <a name="see-also"></a>関連項目

- [dotnet/CLI GitHub リポジトリ](https://github.com/dotnet/cli/)
- [.NET Core のインストール ガイド](https://aka.ms/dotnetcoregs)
