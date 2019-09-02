---
title: dotnet publish コマンド
description: dotnet publish コマンドは、.NET Core プロジェクトをディレクトリに発行します。
ms.date: 05/29/2018
ms.openlocfilehash: 188a136c3e024f71f9b3e89d8e797fa3053f7e4c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202599"
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet publish` - ホスティング システムへの展開のため、アプリケーションとその依存関係をフォルダーにパックします。

## <a name="synopsis"></a>構文

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>説明

`dotnet publish` はアプリケーションをコンパイルし、プロジェクト ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。 出力には次のアセットが含まれます。

- アセンブリの中間言語 (IL) コード (*dll* 拡張子)。
- *.deps.json* ファイル。プロジェクトのすべての依存関係が含まれます。
- *.runtimeconfig.json* ファイル。アプリケーションが想定する共有ランタイムと、ランタイム用の他の構成オプション (ガベージ コレクションの種類など) を指定します。
- アプリケーションの依存関係。NuGet キャッシュから出力フォルダーにコピーされます。

`dotnet publish` コマンドの出力は、実行のためにホスト システム (サーバー、PC、Mac、ラップトップなど) にすぐに展開できます。 これは、アプリケーションの展開を準備するための正式にサポートされている唯一の方法です。 プロジェクトに指定されている展開の種類によっては、ホスティング システムに .NET Core 共有ランタイムがインストールされている場合とされていない場合があります。 詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。 発行されるアプリケーションのディレクトリ構造については、「[Directory structure](/aspnet/core/hosting/directory-structure)」 (ディレクトリ構造) をご覧ください。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>引数

`PROJECT`

発行するプロジェクト。 これは、[C#](csproj.md)、F#、または Visual Basic のプロジェクト ファイルのパスおよびファイル名か、C#、F#、または Visual Basic のプロジェクト ファイルを含むディレクトリへのパスです。 指定しない場合は、既定で現在のディレクトリに設定されます。

## <a name="options"></a>オプション

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

ビルド構成を定義します。 既定値は `Debug` です。

`-f|--framework <FRAMEWORK>`

指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。 ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。

`--force`

最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。 このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。

`-h|--help`

コマンドの短いヘルプを印刷します。

`--manifest <PATH_TO_MANIFEST_FILE>`

アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。 マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。 複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。 このオプションは、.NET Core 2.0 SDK 以降で使用できます。

`--no-build`

発行の前にプロジェクトをビルドしません。 また、`--no-restore` フラグが暗黙的に設定されます。

`--no-dependencies`

プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。

`--no-restore`

コマンドを実行するときに、暗黙的な復元を実行しません。

`-o|--output <OUTPUT_DIRECTORY>`

出力ディレクトリのパスを指定します。 指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/publish/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]/publish/* に設定されます。
パスが相対的である場合、生成された出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。

`--self-contained`

アプリケーションと一緒に .NET Core ランタイムを発行します。これにより、ランタイムをターゲット コンピューターにインストールする必要がなくなります。 ランタイム識別子を指定した場合、その既定値は `true` となります。 さまざまな展開方法の詳細については、「[.NET Core アプリケーションの展開](../deploying/index.md)」を参照してください。

`-r|--runtime <RUNTIME_IDENTIFIER>`

指定されたランタイムのアプリケーションを発行します。 これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。 既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

`--version-suffix <VERSION_SUFFIX>`

プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

ビルド構成を定義します。 既定値は `Debug` です。

`-f|--framework <FRAMEWORK>`

指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。 ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。

`--force`

最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。 このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。

`-h|--help`

コマンドの短いヘルプを印刷します。

`--manifest <PATH_TO_MANIFEST_FILE>`

アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。 マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。 複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。 このオプションは、.NET Core 2.0 SDK 以降で使用できます。

`--no-dependencies`

プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。

`--no-restore`

コマンドを実行するときに、暗黙的な復元を実行しません。

`-o|--output <OUTPUT_DIRECTORY>`

出力ディレクトリのパスを指定します。 指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/publish/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]/publish/* に設定されます。
パスが相対的である場合、生成された出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。

`--self-contained`

アプリケーションと一緒に .NET Core ランタイムを発行します。これにより、ランタイムをターゲット コンピューターにインストールする必要がなくなります。 ランタイム識別子を指定した場合、その既定値は `true` となります。 さまざまな展開方法の詳細については、「[.NET Core アプリケーションの展開](../deploying/index.md)」を参照してください。

`-r|--runtime <RUNTIME_IDENTIFIER>`

指定されたランタイムのアプリケーションを発行します。 これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。 既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

`--version-suffix <VERSION_SUFFIX>`

プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

ビルド構成を定義します。 既定値は `Debug` です。

`-f|--framework <FRAMEWORK>`

指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。 ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。

`-h|--help`

コマンドの短いヘルプを印刷します。

`--manifest <PATH_TO_MANIFEST_FILE>`

アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。 マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。 複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。 このオプションは、.NET Core 2.0 SDK 以降で使用できます。

`-o|--output <OUTPUT_DIRECTORY>`

出力ディレクトリのパスを指定します。 指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/publish/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]/publish/* に設定されます。
パスが相対的である場合、生成された出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。

`-r|--runtime <RUNTIME_IDENTIFIER>`

指定されたランタイムのアプリケーションを発行します。 これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。 既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

`--version-suffix <VERSION_SUFFIX>`

プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。

---

## <a name="examples"></a>使用例

現在のディレクトリのプロジェクトを発行します。

`dotnet publish`

指定されたプロジェクト ファイルを使用して、アプリケーションを発行します。

`dotnet publish ~/projects/app1/app1.csproj`

`netcoreapp1.1` フレームワークを使って現在のディレクトリ内のプロジェクトを発行します。

`dotnet publish --framework netcoreapp1.1`

`netcoreapp1.1` フレームワークと `OS X 10.10` のランタイム (この RID はプロジェクト ファイルに列挙しておく必要があります) を使って、現在のアプリケーションを発行します。

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

現在のアプリケーションを発行します。ただし、復元操作中はルート プロジェクトのみを復元し、プロジェクト間 (P2P) 参照は復元しないでください (.NET Core SDK 2.0 以降のバージョン)。

`dotnet publish --no-dependencies`

## <a name="see-also"></a>関連項目

- [ターゲット フレームワーク](../../standard/frameworks.md)
- [ランタイム識別子 (RID) のカタログ](../rid-catalog.md)
