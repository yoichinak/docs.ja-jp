---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI とその機能に関する概要です。
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920478"
---
# <a name="net-core-cli-overview"></a>.NET Core CLI の概要

.NET Core コマンド ライン インターフェイス (CLI) は、.NET Core アプリケーションを開発、ビルド、実行、発行するためのクロスプラットフォーム ツールチェーンです。

.NET Core CLI は、[.NET Core SDK](../sdk.md) に含まれています。 .NET Core SDK をインストールする方法については、「[.NET Core SDK をインストールする](../install/sdk.md)」をご覧ください。

## <a name="cli-commands"></a>CLI コマンド

既定では、次のコマンドがインストールされます。

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**基本的なコマンド**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [help](dotnet-help.md)
- [store](dotnet-store.md)

**プロジェクトの変更コマンド**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**高度なコマンド**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install スクリプト](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**基本的なコマンド**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)

**プロジェクトの変更コマンド**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**高度なコマンド**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install スクリプト](dotnet-install-script.md)

---

CLI では、プロジェクトに追加のツールを指定できるようにする拡張モデルが適用されます。 詳細については、「[.NET Core CLI の拡張モデル](extensibility.md)」を参照してください。

## <a name="command-structure"></a>コマンド構造

CLI コマンド構造は、[ドライバー ("dotnet")](#driver) と[コマンド](#command)、また場合によってはコマンドの[引数](#arguments)と[オプション](#options)で構成されます。 *my_app* という名前のディレクトリから実行する場合、次のコマンドで示されているように、新しいコンソール アプリの作成やコマンド ラインからの実行など、ほとんどの CLI 操作でこのパターンが見られます。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
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

```dotnetcli
dotnet build
```

最初に、ドライバーは使用する SDK のバージョンを決定します。 ['global.json'](global-json.md) がない場合は、利用可能な SDK の最新バージョンを使用します。 コンピューターで最新のプレビューまたは安定したバージョンになります。  SDK バージョンが決定されたら、コマンドを実行します。

### <a name="command"></a>コマンド

コマンドは、アクションを実行します。 たとえば、`dotnet build` はコードをビルドします。 `dotnet publish` はコードを発行します。 コマンドは、`dotnet {command}` 規則を使用してコンソール アプリケーションとして実装されます。

### <a name="arguments"></a>引数

コマンド ラインで渡す引数は、呼び出されたコマンドへの引数です。 たとえば、`dotnet publish my_app.csproj` を実行した場合、`my_app.csproj` 引数は、発行するプロジェクトを示し、`publish` コマンドに渡されます。

### <a name="options"></a>オプション

コマンド ラインで渡すオプションは、呼び出されたコマンドへのオプションです。 たとえば、`dotnet publish --output /build_output` を実行した場合、`--output` オプションとその値は `publish` コマンドに渡されます。

## <a name="migration-from-projectjson"></a>project.json からの移行

Preview 2 ツールを使用して *project.json* ベースのプロジェクトを生成した場合は、リリース ツールで使用するための MSBuild/ *.csproj* へのプロジェクトの移行について、「[dotnet-migrate](dotnet-migrate.md)」トピックを参照してください。 Preview 2 ツールのリリースの前に作成された .NET Core プロジェクトの場合は、「[DNX から .NET Core CLI への移行 (project.json)](../migration/from-dnx.md)」のガイダンスに従って手動でプロジェクトを更新してから `dotnet migrate` を使用するか、プロジェクトを直接アップグレードします。

## <a name="see-also"></a>関連項目

- [dotnet/sdk GitHub リポジトリ](https://github.com/dotnet/sdk/)
- [.NET Core のインストール ガイド](https://aka.ms/dotnetcoregs)
