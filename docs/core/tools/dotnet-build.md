---
title: dotnet build コマンド
description: dotnet build コマンドは、プロジェクトとそのすべての依存関係をビルドします。
ms.date: 12/04/2018
ms.openlocfilehash: 6a701ee371221c780a878e64b996df95f709371f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612694"
---
# <a name="dotnet-build"></a>dotnet build

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet build` - プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

---

## <a name="description"></a>説明

`dotnet build` コマンドは、プロジェクトとその依存関係をバイナリ セットにビルドします。 バイナリには、拡張子が *.dll* である中間言語 (IL) ファイルのプロジェクトのコードと、拡張子が *.pdb* でありデバッグに使われるシンボル ファイルが含まれます。 アプリケーションの依存関係を一覧表示する依存関係 JSON ファイル (*\*.deps.json*) が生成されます。 共有ランタイムと、そのアプリケーションのバージョンを指定する、*\*.runtimeconfig.json* ファイルが生成されます。

サードパーティ (NuGet のライブラリなど) との依存関係があるプロジェクトの場合、NuGet キャッシュから解決され、プロジェクトのビルドの出力では使うことができません。 この点を考慮すると、`dotnet build` の生成物は別のコンピューターに転送して実行することはできません。 これは .NET Framework の動作とは対照的です。 .NET Framework の場合、実行可能なプロジェクト (アプリケーション) をビルドすると、.NET Framework がインストールされている任意のコンピューター上で実行できる出力が生成されます。 .NET Core でも同様の動作にするには、[dotnet publish](dotnet-publish.md) コマンドを使用する必要があります。 詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。

ビルドには *project.assets.json* ファイルが必要です。このファイルには、アプリケーションの依存関係が一覧表示されています。 このファイルは、[`dotnet restore`](dotnet-restore.md) を実行すると作成されます。 アセット ファイルがないと、ツールは参照アセンブリを解決できないため、エラーになります。 .NET Core 1.x SDK の場合、`dotnet build` を実行する前に `dotnet restore` を明示的に実行する必要がありました。 .NET Core 2.0 SDK 以降では、`dotnet build` を実行すると、`dotnet restore` が暗黙的に実行されます。 ビルド コマンドの実行時に暗黙的な復元を無効にする場合は、`--no-restore` オプションを渡します。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

プロジェクトを実行できるかどうかは、プロジェクト ファイルの `<OutputType>` プロパティで決まります。 次の例は、実行可能なコードを生成するプロジェクトを示しています。

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

ライブラリを生成するには、`<OutputType>` プロパティを省略してください。 ビルドされる出力の主な違いは、ライブラリの IL DLL にはエントリ ポイントが含まれず、実行できないことです。

### <a name="msbuild"></a>MSBuild

`dotnet build` では MSBuild を使用してプロジェクトをビルドするため、並列ビルドとインクリメンタル ビルドの両方がサポートされます。 詳しくは、「[インクリメンタル ビルド](/visualstudio/msbuild/incremental-builds)」を参照してください。

このオプションに加え、`dotnet build` コマンドは、プロパティを設定する `-p` やロガーを定義する `-l` などの MSBuild オプションも受け入れます。 これらのオプションの詳細については、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。 また、[dotnet msbuild](dotnet-msbuild.md) コマンドを使用することもできます。

`dotnet build` の実行は `dotnet msbuild -restore -target:Build` と同じです。

## <a name="arguments"></a>引数

`PROJECT | SOLUTION`

ビルドするプロジェクトまたはソリューションのファイル。 プロジェクトまたはソリューションのファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* または *sln* のどちらかで終わるファイル名拡張子を検索し、そのファイルを使います。

## <a name="options"></a>オプション

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  ビルド構成を定義します。 既定値は `Debug` です。

* **`-f|--framework <FRAMEWORK>`**

  特定の[フレームワーク](../../standard/frameworks.md)用にコンパイルします。 フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。

* **`--force`**

  最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。 このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`--no-dependencies`**

  プロジェクト間 (P2P) 参照を無視し、指定されたルート プロジェクトのみをビルドします。

* **`--no-incremental`**

  インクリメンタル ビルドとして安全でないビルドをマークします。 このフラグにより、インクリメンタル コンパイルは無効になり、プロジェクトの依存関係グラフのクリーン再ビルドが強制的に行われます。

* **`--no-restore`**

  ビルド時に暗黙的な復元は実行されません。

* **`-o|--output <OUTPUT_DIRECTORY>`**

  ビルド済みバイナリを配置するディレクトリ。 このオプションを指定する場合は、`--framework` を定義する必要もあります。 指定しない場合、既定のパスは `./bin/<configuration>/<framework>/` になります。

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  ターゲットのランタイムを指定します。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。

* **`-v|--verbosity <LEVEL>`**

  コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

* **`--version-suffix <VERSION_SUFFIX>`**

  プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) のバージョン サフィックスを定義します。 形式は NuGet のバージョン ガイドラインに従います。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  ビルド構成を定義します。 既定値は `Debug` です。

* **`-f|--framework <FRAMEWORK>`**

  特定の[フレームワーク](../../standard/frameworks.md)用にコンパイルします。 フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`--no-dependencies`**

  プロジェクト間 (P2P) 参照を無視し、指定されたルート プロジェクトのみをビルドします。

* **`--no-incremental`**

  インクリメンタル ビルドとして安全でないビルドをマークします。 このフラグにより、インクリメンタル コンパイルは無効になり、プロジェクトの依存関係グラフのクリーン再ビルドが強制的に行われます。

* **`-o|--output <OUTPUT_DIRECTORY>`**

  ビルド済みバイナリを配置するディレクトリ。 このオプションを指定する場合は、`--framework` を定義する必要もあります。

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  ターゲットのランタイムを指定します。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。

* **`-v|--verbosity <LEVEL>`**

  コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

* **`--version-suffix <VERSION_SUFFIX>`**

  プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) のバージョン サフィックスを定義します。 形式は NuGet のバージョン ガイドラインに従います。

---

## <a name="examples"></a>使用例

* プロジェクトとその依存関係をビルドします。

  ```console
  dotnet build
  ```

* リリース構成を使用して、プロジェクトとその依存関係をビルドします。

  ```console
  dotnet build --configuration Release
  ```

* 特定のランタイム (この例では、Ubuntu 16.04) 用にプロジェクトとその依存関係をビルドします。

  ```console
  dotnet build --runtime ubuntu.16.04-x64
  ```

* プロジェクトをビルドし、復元操作中に指定された NuGet パッケージ ソースを使用します (.NET Core 2.0 SDK 以降のバージョン)。

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* プロジェクトをビルドし、ビルド パラメーターに 1.2.3.4 バージョンを設定します。

  ```console
  dotnet build -p:Version=1.2.3.4
  ```