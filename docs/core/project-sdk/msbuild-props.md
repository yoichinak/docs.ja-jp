---
title: Microsoft.NET.Sdk の MSBuild プロパティ
description: .NET Core SDK によって認識される MSBuild プロパティのリファレンスです。
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "81386658"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>.NET Core SDK プロジェクトの MSBuild プロパティ

このページでは、.NET Core プロジェクトを構成するための MSBuild プロパティについて説明します。

> [!NOTE]
> このページの編集は進行中であり、.NET Core SDK の便利な MSBuild プロパティがすべて記載されている訳ではありません。 一般的な MSBuild プロパティの一覧については、「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。

## <a name="framework-properties"></a>フレームワークのプロパティ

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework` プロパティには、[ メタパッケージ ](../packages.md#metapackages) を暗黙的に参照するアプリのターゲット フレームワーク バージョンを指定します。 有効なターゲット フレームワーク モニカーの一覧については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md#supported-target-framework-versions)」を参照してください。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

詳細については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md)」を参照してください。

### <a name="targetframeworks"></a>TargetFrameworks

アプリで複数のプラットフォームをターゲットにする場合は、`TargetFrameworks` プロパティを使用します。 有効なターゲット フレームワーク モニカーの一覧については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md#supported-target-framework-versions)」を参照してください。

> [!NOTE]
> `TargetFramework` (単数形) が指定されている場合、このプロパティは無視されます。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

詳細については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md)」を参照してください。

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> このプロパティは、`netstandard1.x` を使用するプロジェクトにのみ適用されます。 `netstandard2.x` を使用するプロジェクトには適用されません。

[メタパッケージ](../packages.md#metapackages) バージョンよりも低いフレームワーク バージョンを指定する場合は、`NetStandardImplicitPackageVersion` プロパティを使用します。 次の例のプロジェクト ファイルは、`netstandard1.3` をターゲットにしていますが、`NETStandard.Library` の 1.6.0 バージョンを使用しています。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>[発行] プロパティ

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`RuntimeIdentifier` プロパティを使用すると、プロジェクトに 1 つの[ランタイム識別子 (RID)](../rid-catalog.md) を指定できます。 RID により、自己完結型の展開を発行できます。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`RuntimeIdentifiers` プロパティには、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) のセミコロン区切りリストを指定できます。 複数のランタイムに発行する必要がある場合は、このプロパティを使用します。 `RuntimeIdentifiers` は、復元時に適切な資産をグラフに確実に含めるために使用されます。

> [!TIP]
> `RuntimeIdentifier` (単数形) を使用すると、必要なランタイムが 1 つだけのとき、ビルドが速くなります。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost` プロパティは、.NET Core SDK の 2.1.400 バージョンで導入されました。 デプロイ用にネイティブ実行可能ファイルを作成するかどうかを制御できます。 自己完結型の配置にはネイティブの実行可能ファイルが必要です。

.NET Core 3.0 以降のバージョンでは、既定でフレームワークに依存する実行可能ファイルが作成されます。 実行可能ファイルの生成を無効にするには、`UseAppHost` プロパティを `false` に設定します。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

配置の詳細については、[.NET Core アプリケーションの配置](../deploying/index.md)に関するページを参照してください。

## <a name="compile-properties"></a>コンパイルのプロパティ

### <a name="langversion"></a>LangVersion

`LangVersion` プロパティを使用すると、特定のプログラミング言語バージョンを指定できます。 たとえば、C# プレビュー機能にアクセスする場合は、`LangVersion` を `preview` に設定します。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

詳細については、「[C# 言語のバージョン管理](../../csharp/language-reference/configure-language-version.md#override-a-default)」を参照してください。

## <a name="nuget-packages"></a>NuGet パッケージ

- [PackageReference](#packagereference)
- [AssetTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>PackageReference

`PackageReference` 項目を使用すると、NuGet の依存関係を指定できます。 たとえば、[メタパッケージ](../packages.md#metapackages)ではなく 1 つのパッケージを参照する場合があります。 `Include` 属性は、パッケージ ID を指定します。 次の例のプロジェクト ファイル スニペットでは、[System.Runtime](https://www.nuget.org/packages/System.Runtime/) パッケージを参照しています。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

詳細については、[プロジェクト ファイルのパッケージ参照](/nuget/consume-packages/package-references-in-project-files)に関するページを参照してください。

### <a name="assettargetfallback"></a>AssetTargetFallback

`AssetTargetFallback` プロパティを使用すると、プロジェクトから参照されるプロジェクトの互換性のある追加のフレームワーク バージョンと、プロジェクトに使用する NuGet パッケージを指定できます。 たとえば、`PackageReference` を使用してパッケージの依存関係を指定し、そのパッケージにプロジェクトの `TargetFramework` と互換性のある資産が含まれない場合は、`AssetTargetFallback` プロパティが機能します。 参照されたパッケージの互換性は、`AssetTargetFallback` で指定された各ターゲット フレームワークを使用して再確認されます。

`AssetTargetFallback` プロパティを 1 つ以上の[ターゲット フレームワーク バージョン](../../standard/frameworks.md#supported-target-framework-versions)に設定できます。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>ターゲットのパックと復元

MSBuild 15.1 では、ビルドの一部として NuGet パッケージを作成および復元するための `pack` および `restore` ターゲットが導入されました。 `PackageTargetFallback` など、これらのターゲットの MSBuild プロパティについては、「[MSBuild ターゲットとしての NuGet の pack と restor](/nuget/reference/msbuild-targets)」を参照してください。

## <a name="see-also"></a>関連項目

- [MSBuild スキーマ リファレンス](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [MSBuild の共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet pack の MSBuild プロパティ](/nuget/reference/msbuild-targets#pack-target)
- [NuGet restore の MSBuild プロパティ](/nuget/reference/msbuild-targets#restore-properties)
- [ビルドのカスタマイズ](/visualstudio/msbuild/customize-your-build)
