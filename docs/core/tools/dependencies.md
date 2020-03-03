---
title: .NET Core ツールでの依存関係の管理
description: .NET Core ツールで依存関係を管理する方法について説明します。
ms.date: 03/06/2017
ms.openlocfilehash: 916daca0240c10dc63ca96048590a426bc51d450
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965621"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a>.NET Core SDK 1.0 で依存関係を管理する

.NET Core プロジェクトでの project.json から csproj と MSBuild への移行では、多額の投資も行われ、その結果、プロジェクト ファイルとアセットが統合され、依存関係を追跡できるようになりました。 .NET Core プロジェクトでは、これは project.json の動作に似ています。 NuGet の依存関係を追跡するための独立した JSON または XML ファイルはありません。 この変更により、`<PackageReference>` と呼ばれる別の*参照*の型も csproj 構文に導入されました。

ここでは、新しい参照型について説明します。 また、この新しい参照型を使ってプロジェクトにパッケージの依存関係を追加する方法も示します。

## <a name="the-new-packagereference-element"></a>新しい \<PackageReference> 要素

`<PackageReference>` の基本的な構造は次のとおりです。

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

MSBuild に詳しい場合は、既に存在する他の参照型と似ていることが分かります。 重要なのは、`Include` ステートメントではプロジェクトに追加するパッケージ ID を指定することです。 `<Version>` 子要素は取得するバージョンを指定します。 バージョンは、[NuGet のバージョン ルール](/nuget/create-packages/dependency-versions#version-ranges)に従って指定します。

> [!NOTE]
> プロジェクト ファイルの構文に詳しくない場合は、詳細について、[MSBuild プロジェクトのリファレンス](/visualstudio/msbuild/msbuild-project-file-schema-reference) ドキュメントを参照してください。

次の例に示すように、条件を使用して、特定のターゲットでのみ使用できる依存関係を追加します。

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

依存関係は、指定されたターゲットでビルドが行われている場合にのみ有効になります。 条件の `$(TargetFramework)` は、プロジェクトで設定される MSBuild プロパティです。 最も一般的な .NET Core アプリケーションの場合、これを行う必要はありません。

## <a name="add-a-dependency-to-the-project"></a>プロジェクトへの依存関係の追加

簡単に依存関係をプロジェクトに追加できます。 ここでは、Json.NET バージョン `9.0.1` をプロジェクトに追加する方法の例を示します。 もちろん、NuGet の他の依存関係にも適用できます。

プロジェクト ファイルに 2 つ以上の `<ItemGroup>` ノードがあります。 ノードの 1 つには、`<PackageReference>` 要素が既に存在します。 新しい依存関係をこのノードに追加するか、新しい依存関係を作成することができます。結果は同じになります。

次の例では、`dotnet new console` によって作成された既定のテンプレートを使用します。 これは、簡単なコンソール アプリケーションです。 プロジェクトを開くと、既に存在している `<PackageReference>` を含んだ `<ItemGroup>` が表示されます。 それに以下を追加します。

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

その後、プロジェクトを保存し、`dotnet restore` コマンドを実行して依存関係をインストールします。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

完全なプロジェクトは次のようになります。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="remove-a-dependency-from-the-project"></a>プロジェクトから依存関係を削除する

プロジェクト ファイルから依存関係を削除するには、プロジェクト ファイルから `<PackageReference>` を削除するだけです。
