---
title: For Azure でF#の Package Management の使用
description: パケットまたは Nuget を使用F#して Azure の依存関係を管理する
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214227"
---
# <a name="package-management-for-f-azure-dependencies"></a>F# の Azure の依存関係のためのパッケージ管理

パッケージマネージャーを使用すると、Azure 開発用のパッケージを簡単に取得できます。 [パケット](https://fsprojects.github.io/Paket/)と[NuGet](https://www.nuget.org/)の2つのオプションがあります。

## <a name="using-paket"></a>パケットの使用

[パケット](https://fsprojects.github.io/Paket/)を dependency manager として使用している場合は、 `paket.exe`ツールを使用して Azure の依存関係を追加できます。 次に例を示します。

```console
> paket add nuget WindowsAzure.Storage
```

または、クロスプラットフォームの .NET 開発に[Mono](https://www.mono-project.com/)を使用している場合は、次のようにします。

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

これにより`WindowsAzure.Storage` 、現在のディレクトリ内のプロジェクトに対するパッケージの依存関係のセットが`paket.dependencies`追加され、ファイルが変更され、パッケージがダウンロードされます。 以前に依存関係を設定している場合、または他の開発者によって依存関係が設定されているプロジェクトを操作している場合は、次のようにローカルに依存関係を解決してインストールすることができます。

```console
> paket install
```

または、Mono 開発の場合:

```console
> mono paket.exe install
```

次のように、すべてのパッケージの依存関係を最新バージョンに更新できます。

```console
> paket update
```

または、Mono 開発の場合:

```console
> mono paket.exe update
```

## <a name="using-nuget"></a>Nuget の使用

依存関係マネージャーとして[NuGet](https://www.nuget.org/)を使用している場合は`nuget.exe` 、ツールを使用して Azure の依存関係を追加できます。 次に例を示します。

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

または、Mono 開発の場合:

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

これにより`WindowsAzure.Storage` 、現在のディレクトリ内のプロジェクトに対するパッケージの依存関係のセットが追加され、パッケージがダウンロードされます。 以前に依存関係を設定している場合、または他の開発者によって依存関係が設定されているプロジェクトを操作している場合は、次のようにローカルに依存関係を解決してインストールすることができます。

```console
> nuget restore
```

または、Mono 開発の場合:

```console
> mono nuget.exe restore
```

次のように、すべてのパッケージの依存関係を最新バージョンに更新できます。

```console
> nuget update
```

または、Mono 開発の場合:

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>参照元のアセンブリ

F#スクリプトでパッケージを使用するには、 `#r`ディレクティブを使用して、パッケージに含まれているアセンブリを参照する必要があります。 次に例を示します。

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

ご覧のとおり、DLL への相対パスと完全な DLL 名を指定する必要があります。これは、パッケージ名とまったく同じではない可能性があります。 このパスには、フレームワークのバージョンと、場合によってはパッケージのバージョン番号が含まれます。 インストールされているすべてのアセンブリを検索するには、Windows のコマンドラインで次のように使用します。

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

Unix シェルでは、次のようなものがあります。

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

これにより、インストールされているアセンブリへのパスが得られます。 そこから、フレームワークのバージョンに適したパスを選択できます。
