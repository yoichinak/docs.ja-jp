---
title: dotnet build コマンド
description: dotnet build コマンドは、プロジェクトとそのすべての依存関係をビルドします。
ms.date: 08/08/2019
ms.openlocfilehash: 0b353d60691fb4bb85536c68dc4ab248f45c3a76
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117754"
---
# <a name="dotnet-build"></a>dotnet build

**この記事の対象: ✓** .NET Core 1.x SDK 以降のバージョン

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>name

`dotnet build` - プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>説明

`dotnet build` コマンドは、プロジェクトとその依存関係をバイナリ セットにビルドします。 バイナリには、拡張子が *.dll* である中間言語 (IL) ファイルのプロジェクトのコードと、拡張子が *.pdb* でありデバッグに使われるシンボル ファイルが含まれます。 アプリケーションの依存関係をリストする依存関係 JSON ファイル ( *.deps.json*) が生成されます。 アプリケーションのための共有ランタイムとそのバージョンを指定する、 *.runtimeconfig.json* ファイルが生成されます。

サードパーティ (NuGet のライブラリなど) との依存関係があるプロジェクトの場合、NuGet キャッシュから解決され、プロジェクトのビルドの出力では使うことができません。 この点を考慮すると、`dotnet build` の生成物は別のコンピューターに転送して実行することはできません。 これは .NET Framework の動作とは対照的です。 .NET Framework の場合、実行可能なプロジェクト (アプリケーション) をビルドすると、.NET Framework がインストールされている任意のコンピューター上で実行できる出力が生成されます。 .NET Core でも同様の動作にするには、[dotnet publish](dotnet-publish.md) コマンドを使用する必要があります。 詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。

ビルドには *project.assets.json* ファイルが必要です。このファイルには、アプリケーションの依存関係が一覧表示されています。 このファイルは、[`dotnet restore`](dotnet-restore.md) を実行すると作成されます。 アセット ファイルが配置されていないと、ツールは参照アセンブリを解決できないため、エラーになります。 .NET Core 1.x SDK の場合、`dotnet build` を実行する前に `dotnet restore` を明示的に実行する必要がありました。 .NET Core 2.0 SDK 以降では、`dotnet build` を実行すると、`dotnet restore` が暗黙的に実行されます。 ビルド コマンドの実行時に暗黙的な復元を無効にする場合は、`--no-restore` オプションを渡します。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

プロジェクトを実行できるかどうかは、プロジェクト ファイルの `<OutputType>` プロパティで決まります。 次の例は、実行可能なコードを生成するプロジェクトを示しています。

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

ライブラリを生成するには、`<OutputType>` プロパティを省略します。 ビルドされる出力の主な違いは、ライブラリの IL DLL にはエントリ ポイントが含まれず、実行できないことです。

### <a name="msbuild"></a>MSBuild

`dotnet build` では MSBuild を使用してプロジェクトをビルドするため、並列ビルドとインクリメンタル ビルドの両方がサポートされます。 詳しくは、「[インクリメンタル ビルド](/visualstudio/msbuild/incremental-builds)」を参照してください。

このオプションに加え、`dotnet build` コマンドは、プロパティを設定する `-p` やロガーを定義する `-l` などの MSBuild オプションも受け入れます。 これらのオプションの詳細については、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。 また、[dotnet msbuild](dotnet-msbuild.md) コマンドを使用することもできます。

`dotnet build` の実行は `dotnet msbuild -restore -target:Build` と同じです。

## <a name="arguments"></a>引数

`PROJECT | SOLUTION`

ビルドするプロジェクトまたはソリューションのファイル。 プロジェクトまたはソリューションのファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* または *sln* のどちらかで終わるファイル拡張子を持つファイルを検索して、そのファイルを使います。

## <a name="options"></a>オプション

* **`-c|--configuration {Debug|Release}`**

  ビルド構成を定義します。 既定値は `Debug` です。

* **`-f|--framework <FRAMEWORK>`**

  特定の[フレームワーク](../../standard/frameworks.md)用にコンパイルします。 フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。

* **`--force`**

  最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。 このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。 .NET Core 2.0 SDK 以降で使用できます。

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`--interactive`**

  コマンドを停止して、ユーザーの入力または操作のために待機させることができます。 たとえば、認証を完了する場合があります。 .NET Core 3.0 SDK 以降で使用できます。

* **`--no-dependencies`**

  プロジェクト間 (P2P) 参照を無視し、指定されたルート プロジェクトのみをビルドします。

* **`--no-incremental`**

  インクリメンタル ビルドとして安全でないビルドをマークします。 このフラグにより、インクリメンタル コンパイルは無効になり、プロジェクトの依存関係グラフのクリーン再ビルドが強制的に行われます。

* **`--no-restore`**

  ビルド時に暗黙的な復元は実行されません。 .NET Core 2.0 SDK 以降で使用できます。

* **`--nologo`**

  著作権情報を表示しません。 .NET Core 3.0 SDK 以降で使用できます。

* **`-o|--output <OUTPUT_DIRECTORY>`**

  ビルド済みバイナリを配置するディレクトリ。 このオプションを指定する場合は、`--framework` を定義する必要もあります。 指定しない場合、既定のパスは `./bin/<configuration>/<framework>/` になります。

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  ターゲットのランタイムを指定します。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。

* **`-v|--verbosity <LEVEL>`**

  MSBuild の詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。 既定値は、`minimal` です。

* **`--version-suffix <VERSION_SUFFIX>`**

  プロジェクトをビルドするときに使用する `$(VersionSuffix)` プロパティの値を設定します。 これは、`$(Version)` プロパティが設定されていない場合にのみ機能します。 次に、`$(Version)` には、ダッシュで区切り `$(VersionSuffix)` と組み合わせた `$(VersionPrefix)` が設定されます。

## <a name="examples"></a>使用例

* プロジェクトとその依存関係をビルドします。

  ```dotnetcli
  dotnet build
  ```

* リリース構成を使用して、プロジェクトとその依存関係をビルドします。

  ```dotnetcli
  dotnet build --configuration Release
  ```

* 特定のランタイム (この例では、Ubuntu 18.04) 用にプロジェクトとその依存関係をビルドします。

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

* プロジェクトをビルドし、復元操作中に指定された NuGet パッケージ ソースを使用します (.NET Core 2.0 SDK 以降のバージョン)。

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

* `-p` [MSBuild オプション](#msbuild)を使用してプロジェクトをビルドし、バージョン 1.2.3.4 をビルド パラメーターとして設定します。

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
