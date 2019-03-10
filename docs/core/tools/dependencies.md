---
title: .NET Core ツールでの依存関係の管理
description: .NET Core ツールで依存関係を管理する方法について説明します。
ms.date: 03/06/2017
ms.custom: seodec18
ms.openlocfilehash: 701100476b8b08aa4b0229bd0de30d02c54ddce9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673874"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>.NET Core SDK 1.0 での依存関係の管理

.NET Core プロジェクトでの project.json から csproj と MSBuild への移行では、多額の投資も行われ、その結果、プロジェクト ファイルとアセットが統合され、依存関係を追跡できるようになりました。 .NET Core プロジェクトでの依存関係の追跡は、project.json と似ています。 NuGet の依存関係を追跡するための独立した JSON または XML ファイルはありません。 この変更により、`<PackageReference>` と呼ばれる別の*参照*の型も csproj 構文に導入されました。 

ここでは、新しい参照型について説明します。 また、この新しい参照型を使ってプロジェクトにパッケージの依存関係を追加する方法も示します。 

## <a name="the-new-packagereference-element"></a>新しい \<PackageReference> 要素
`<PackageReference>` の基本的な構造は次のとおりです。

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

MSBuild に詳しい場合は、既に存在する他の参照型と似ていることが分かります。 重要なのは、`Include` ステートメントではプロジェクトに追加するパッケージ ID を指定することです。 `<Version>` 子要素は取得するバージョンを指定します。 バージョンは、[NuGet のバージョン ルール](/nuget/create-packages/dependency-versions#version-ranges)に従って指定します。

> [!NOTE]
> `csproj` の構文に詳しくない場合は、詳細について、[MSBuild プロジェクトのリファレンス](/visualstudio/msbuild/msbuild-project-file-schema-reference) ドキュメントを参照してください。  

特定のターゲットでのみ使用可能な依存関係を追加するには、次の例のような条件を使用します。

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

これは、ビルドがその特定のターゲットに対して行われる場合にのみ依存関係が有効であることを意味します。 条件の `$(TargetFramework)` は、プロジェクトで設定されている MSBuild プロパティです。 最も一般的な .NET Core アプリケーションの場合、これを行う必要はありません。 

## <a name="adding-a-dependency-to-your-project"></a>プロジェクトへの依存関係の追加
簡単に依存関係をプロジェクトに追加できます。 ここでは、Json.NET バージョン `9.0.1` をプロジェクトに追加する方法の例を示します。 もちろん、NuGet の他の依存関係にも適用できます。 

プロジェクト ファイルを開くと、2 つ以上の `<ItemGroup>` ノードがあります。 ノードの 1 つには `<PackageReference>` 要素が既にあります。 このノードに新しい依存関係を追加することも、新しいノードを追加することもできます。結果は同じなので開発者次第です。 

この例では、`dotnet new console` によって削除される既定のテンプレートを使います。 これは、簡単なコンソール アプリケーションです。 プロジェクトを開き、最初に `<PackageReference>` が既に存在する `<ItemGroup>` を探します。 次に、以下のコードをそれに追加します。

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

## <a name="removing-a-dependency-from-the-project"></a>プロジェクトからの依存関係の削除
プロジェクト ファイルから依存関係を削除するには、プロジェクト ファイルから `<PackageReference>` を削除するだけです。
