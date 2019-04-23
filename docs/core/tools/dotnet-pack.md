---
title: dotnet pack コマンド
description: dotnet pack コマンドでは、.NET Core プロジェクトの NuGet パッケージを作成します。
ms.date: 12/04/2018
ms.openlocfilehash: 8faa99bf35d9802b16f951082b20644d45a939c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672127"
---
# <a name="dotnet-pack"></a>dotnet pack

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet pack` - NuGet パッケージにコードをパックします。

## <a name="synopsis"></a>構文

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a>説明

`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。 このコマンドの結果が NuGet パッケージです。 `--include-symbols` オプションが存在する場合、デバッグ シンボルを含む別のパッケージが作成されます。

パックされるプロジェクトの NuGet 依存関係が *.nuspec* ファイルに追加されるため、パッケージのインストール時に適切に解決されます。 プロジェクト間参照はプロジェクト内にはパッケージ化されません。 現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。

既定では、`dotnet pack` は最初にプロジェクトをビルドします。 この動作を避けたい場合は、`--no-build` オプションを渡します。 このオプションは、コードが既にビルドされていることがわかっている場合の継続的インテグレーション (CI) ビルド シナリオで役立つことがよくあります。

パッキング プロセスのために `dotnet pack` コマンドに MSBuild のプロパティを使用できます。 詳細については、「[NuGet メタデータ プロパティ](csproj.md#nuget-metadata-properties)」と「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。 「[例](#examples)」のセクションでは、MSBuild の -p スイッチを使用する方法について、2 つの異なるシナリオで説明します。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>引数

* **`PROJECT`**

  パックするプロジェクトです。 [csproj ファイル](csproj.md)またはディレクトリのいずれかへのパスです。 指定しない場合は、既定で現在のディレクトリに設定されます。

## <a name="options"></a>オプション

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  ビルド構成を定義します。 既定値は `Debug` です。

* **`--force`**

  最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。 このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`--include-source`**

  NuGet パッケージにソース ファイルを含めます。 ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。

* **`--include-symbols`**

  シンボルの `nupkg` を生成します。

* **`--no-build`**

  パッキングの前にプロジェクトをビルドしません。 また、`--no-restore` フラグが暗黙的に設定されます。

* **`--no-dependencies`**

  プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。

* **`--no-restore`**

  コマンドを実行するときに、暗黙的な復元を実行しません。

* **`-o|--output <OUTPUT_DIRECTORY>`**

  指定したディレクトリにビルド済みパッケージを配置します。

* **`--runtime <RUNTIME_IDENTIFIER>`**

  パッケージを復元するターゲット ランタイムを指定します。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。

* **`-s|--serviceable`**

  パッケージに処理可能フラグを設定します。 詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。

* **`--version-suffix <VERSION_SUFFIX>`**

  プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。

* **`-v|--verbosity <LEVEL>`**

  コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

> [!NOTE]
> Web プロジェクトは既定でパッケージ化可能ではありません。 既定の動作をオーバーライドするには、*.csproj* ファイルに次のプロパティを追加します。
>
> ```xml
> <PropertyGroup>
>    <IsPackable>true</IsPackable>
> </PropertyGroup>
> ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  ビルド構成を定義します。 既定値は `Debug` です。

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`--include-source`**

  NuGet パッケージにソース ファイルを含めます。 ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。

* **`--include-symbols`**

  シンボルの `nupkg` を生成します。

* **`--no-build`**

  パッキングの前にプロジェクトをビルドしません。

* **`-o|--output <OUTPUT_DIRECTORY>`**

  指定したディレクトリにビルド済みパッケージを配置します。

* **`-s|--serviceable`**

  パッケージに処理可能フラグを設定します。 詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。

* **`--version-suffix <VERSION_SUFFIX>`**

  プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。

* **`-v|--verbosity <LEVEL>`**

  コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

---

## <a name="examples"></a>使用例

* 現在のディレクトリのプロジェクトをパックします。

  ```console
  dotnet pack
  ```

* `app1` プロジェクトをパックします。

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* プロジェクトを現在のディレクトリにパックし、`nupkgs` フォルダーに生成されたパッケージを配置します。

  ```console
  dotnet pack --output nupkgs
  ```

* 現在のディレクトリのプロジェクトを `nupkgs` フォルダーにパックし、ビルド ステップをスキップします。

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* *.csproj* ファイルで `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` として構成されているプロジェクトのバージョン サフィックスで、現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* `PackageVersion` MSBuild プロパティで `2.1.0` にパッケージ バージョンを設定します。

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* プロジェクトを特定の[ターゲット フレームワーク](../../standard/frameworks.md)用にパックします。

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* プロジェクトをパックして、復元操作の特定のランタイム (Windows 10) を使用します(.NET Core SDK 2.0 以降のバージョン)。

  ```console
  dotnet pack --runtime win10-x64
  ```

* [.nuspec ファイル](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)を使用してプロジェクトをパックします。

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
