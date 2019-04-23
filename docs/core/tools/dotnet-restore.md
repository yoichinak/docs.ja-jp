---
title: dotnet restore コマンド
description: dotnet restore コマンドを使用して、依存関係とプロジェクト固有のツールを復元する方法について説明します。
ms.date: 05/29/2018
ms.openlocfilehash: 3ddb9f679cfcab972483a4cb53ffe2b075867614
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613971"
---
# <a name="dotnet-restore"></a>dotnet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet restore` - プロジェクトの依存関係とツールを復元します。

## <a name="synopsis"></a>構文

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>説明

`dotnet restore` コマンドでは NuGet を使用して、依存関係と、プロジェクト ファイルに指定されているプロジェクト固有のツールを復元します。 既定では、依存関係とツールの復元は並列に実行されます。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

依存関係を復元するには、NuGet で、パッケージを配置するフィードが必要になります。 フィードは、通常、*NuGet.config* 構成ファイルを通じて提供されます。 既定の構成ファイルは、CLI ツールがインストールされている場合に提供されます。 プロジェクト ディレクトリに独自の *NuGet.config* ファイルを作成して、さらにフィードを指定します。 コマンド プロンプトで呼び出すごとにフィードをさらに指定することもできます。

依存関係については、`--packages` 引数を使用して、復元操作中に復元されたパッケージの配置場所を指定します。 指定されていない場合は、既定の NuGet パッケージ キャッシュが使用されます。これは、すべてのオペレーティング システムのユーザーのホーム ディレクトリ内の `.nuget/packages` ディレクトリにあります。 たとえば、Linux の場合は */home/user1*、Windows の場合は *C:\Users\user1* です。

プロジェクト固有のツールについては、`dotnet restore` はまず、ツールがパックされているパッケージを復元し、プロジェクト ファイルに指定されているツールの依存関係の復元に進みます。

*Nuget.Config* がある場合、`dotnet restore` コマンドの動作はその設定の一部に影響を受けます。 たとえば、*NuGet.Config* に `globalPackagesFolder` を設定すると、指定されたフォルダーに NuGet パッケージが復元されます。 これは `dotnet restore` コマンドで `--packages` オプションを指定する操作の代替方法です。 詳細については、「[NuGet.Config reference](/nuget/schema/nuget-config-file)」(NuGet.Config リファレンス) を参照してください。

## <a name="implicit-dotnet-restore"></a>暗黙的 `dotnet restore`

.NET Core 2.0 より、次のコマンドの発行時に必要な場合、`dotnet restore` が暗黙的に実行されます。

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

ほとんどの場合、`dotnet restore` コマンドを明示的に使用する必要がなくなりました。

ときには、`dotnet restore` を暗黙的に実行するのが不便な場合があります。 たとえば、ビルド システムなど、一部の自動化されているシステムでは、ネットワーク使用状況を制御できるように、`dotnet restore` を明示的に呼び出し、復元のタイミングを制御する必要があります。 `dotnet restore` の暗黙的実行を防ぐために、`--no-restore` フラグと共にこれらのコマンドのいずれかを使用し、暗黙的復元を無効にできます。

## <a name="arguments"></a>引数

`ROOT`

復元するプロジェクト ファイルへのオプションのパスです。

## <a name="options"></a>オプション

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--configfile <FILE>`

復元操作で使用する NuGet 構成ファイル (*NuGet.config*) です。

`--disable-parallel`

複数プロジェクトの並行復元を無効にします。

`--force`

最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。 このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。

`-h|--help`

コマンドの短いヘルプを印刷します。

`--ignore-failed-sources`

バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。

`--no-cache`

パッケージとの HTTP 要求をキャッシュしないように指定します。

`--no-dependencies`

プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。

`--packages <PACKAGES_DIRECTORY>`

復元されるパッケージのディレクトリを指定します。

`-r|--runtime <RUNTIME_IDENTIFIER>`

パッケージの復元用のランタイムを指定します。 これは、*.csproj* ファイルの `<RuntimeIdentifiers>` タグに明示的にリストされていないランタイムのパッケージを復元するために使用されます。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。 このオプションを複数回指定して、複数の RID を指定します。

`-s|--source <SOURCE>`

復元操作時に使用する NuGet パッケージのソースを指定します。 この設定により、*NuGet.config* ファイルに指定されているすべてのソースがオーバーライドされます。 このオプションを複数回指定することによって、複数のソースを指定できます。

`--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

`--interactive`

コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。 .NET Core 2.1.400 以降。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--configfile <FILE>`

復元操作で使用する NuGet 構成ファイル (*NuGet.config*) です。

`--disable-parallel`

複数プロジェクトの並行復元を無効にします。

`-h|--help`

コマンドの短いヘルプを印刷します。

`--ignore-failed-sources`

バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。

`--no-cache`

パッケージとの HTTP 要求をキャッシュしないように指定します。

`--no-dependencies`

プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。

`--packages <PACKAGES_DIRECTORY>`

復元されるパッケージのディレクトリを指定します。

`-r|--runtime <RUNTIME_IDENTIFIER>`

パッケージの復元用のランタイムを指定します。 これは、*.csproj* ファイルの `<RuntimeIdentifiers>` タグに明示的にリストされていないランタイムのパッケージを復元するために使用されます。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。 このオプションを複数回指定して、複数の RID を指定します。

`-s|--source <SOURCE>`

復元操作時に使用する NuGet パッケージのソースを指定します。 これにより、*NuGet.config* ファイルに指定されているすべてのソースがオーバーライドされます。 このオプションを複数回指定することによって、複数のソースを指定できます。

`--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

---

## <a name="examples"></a>使用例

現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore`

指定されたパスで見つかった `app1` プロジェクトの依存関係とツールを復元します。

`dotnet restore ~/projects/app1/app1.csproj`

ソースとして指定されたファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore -s c:\packages\mypackages`

ソースとして指定された 2 つのファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

現在のディレクトリでプロジェクトの依存関係とツールを復元し、最小限の出力のみを表示します。

`dotnet restore --verbosity minimal`
