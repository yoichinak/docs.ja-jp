---
title: WPF アプリを .NET Core 3.0 に移植する
description: .NET Framework Windows Presentation Foundation アプリケーションを .NET Core 3.0 for Windows に移植する方法について説明します。
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 5c7e3aca0a473abb831693244d1b194985f2ef7f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342207"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>方法: WPF デスクトップ アプリを .NET Core に移植する

この記事では、Windows Presentation Foundation (WPF) ベースのデスクトップ アプリを .NET Framework から .NET Core 3.0 に移植する方法について説明します。 .NET Core 3.0 SDK には、WPF アプリケーションのサポートが含まれています。 WPF は、まだ Windows 専用のフレームワークであるため、Windows 上でのみ実行されます。 この例では、.NET Core CLI を使用して、プロジェクトの作成と管理を行います。

この記事では、さまざまな名前が使用して、移行で使用されるファイルの種類を識別しています。 実際のファイルの名前とは異なっているため、自分のプロジェクトを移行するときは、次の一覧の名前に置き換えて説明をお読みください。

| ファイル | 説明 |
| ---- | ----------- |
| **MyApps.sln** | ソリューション ファイルの名前。 |
| **MyWPF.csproj** | 移植する .NET Framework WPF プロジェクトの名前。 |
| **MyWPFCore.csproj** | 作成する新しい .NET Core プロジェクトの名前。 |
| **MyAppCore.exe** | .NET Core WPF アプリの実行可能ファイル。 |

## <a name="prerequisites"></a>必須コンポーネント

- 実行したいデザイナー作業用の [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。

  次の Visual Studio ワークロードをインストールします。
  - .NET デスクトップ開発
  - .NET クロスプラットフォーム開発

- 問題なくビルドされて実行されているソリューション内の作業用 WPF プロジェクト。
- プロジェクトは C# でコーディングされている必要があります。 
- 最新の [.NET Core 3.0](https://aka.ms/netcore3download) のプレビューをインストールします。

>[!NOTE]
>**Visual Studio 2017** では、.NET Core 3.0 プロジェクトはサポートされていません。 **Visual Studio 2019** では .NET Core 3.0 プロジェクトはサポートされていますが、.NET Core 3.0 WPF プロジェクト用のビジュアル デザイナーはまだサポートされていません。 ビジュアル デザイナーを使用するには、.NET Core プロジェクトとそのファイルを共有するソリューション内に .NET WPF プロジェクトを配置する必要です。

### <a name="consider"></a>次の例を考えてみましょう

.NET Framework WPF アプリケーションを移植するときは、いくつかの点を考慮する必要があります。

01. アプリケーションが移行に適した候補であることを確認する。

    [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) を使用して、プロジェクトを .NET Core 3.0 に移行できるかどうかを判断します。 プロジェクトが .NET Core 3.0 では問題が発生する場合は、アナライザーによってこれらの問題を特定できます。

01. WPF の別のバージョンを使用している。

    .NET Core 3.0 プレビュー 1 がリリースされたときに、WPF は GitHub でオープン ソースになりました。 .NET Core WPF のコードは、.NET Framework WPF コード ベースの 1 つの分岐です。 違いの存在によって、アプリが移植されない可能性があります。

01. [Windows 互換機能パック][compat-pack]が移行に役立つ可能性がある。

    .NET Framework で利用できる一部の API は、.NET Core 3.0 では利用できません。 [Windows 互換機能パック][compat-pack]によって多数の API が追加され、WPF アプリに .NET Core との互換性を持たせるために役立つ可能性があります。

01. 自分のプロジェクトで使用されている NuGet パッケージを更新する。

    移行する前に、常に NuGet パッケージの最新バージョンを使用することをお勧めします。 アプリケーションで NuGet パッケージを参照している場合は、最新バージョンに更新してください。 アプリケーションが正常にビルドされることを確認します。 アップグレード後にパッケージ エラーが発生した場合は、コードを壊さない最新のバージョンにパッケージをダウングレードします。

01. Visual Studio 2019 では、.NET Core 3.0 用の WPF デザイナーはまだサポートされていない

    現時点では、Visual Studio の WPF デザイナーを使用する場合は、既存の .NET Framework WPF プロジェクト ファイルを保持する必要があります。

## <a name="create-a-new-sdk-project"></a>新しい SDK プロジェクトを作成する

作成する新しい .NET Core 3.0 プロジェクトは、.NET Framework プロジェクトとは別のディレクトリに配置する必要があります。 両方が同じディレクトリに配置されている場合は、**obj** ディレクトリ内に生成されているファイルと競合する可能性があります。 この例では、**SolutionFolder** ディレクトリに **MyWPFAppCore** という名前のディレクトリを作成します。

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

次に、**MyWPFAppCore** ディレクトリに **MyWPFCore.csproj** プロジェクトを作成する必要があります。 このファイルは、任意のテキスト エディターを使用して手動で作成できます。 次の XML に貼り付けます。

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

プロジェクト ファイルを手動で作成しない場合は、Visual Studio または .NET Core SDK を使用して生成できます。 ただし、プロジェクト ファイル以外のプロジェクト テンプレートによって生成されるすべてのファイルを削除する必要があります。 SDK を使用するには、次のコマンドを **SolutionFolder** ディレクトリから実行します。

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

**MyWPFCore.csproj** を作成した後、ディレクトリ構造は次のようになります。

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

**SolutionFolder** ディレクトリから Visual Studio または .NET Core CLI を使用して、**MyWPFCore.csproj** プロジェクトを **MyApps.sln** に追加できます。

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>アセンブリ情報の生成を修正する

.NET Framework で作成された Windows Presentation Foundation プロジェクトには、生成されるアセンブリのバージョンなどのアセンブリの属性を格納する `AssemblyInfo.cs` ファイルが含まれています。 SDK スタイルのプロジェクトでは、SDK プロジェクト ファイルに基づいて、この情報が自動的に生成されます。 両方の種類の "アセンブリ情報" があると、競合が発生します。 この問題は、自動生成を無効にして、既存の `AssemblyInfo.cs` ファイルをプロジェクトに強制的に使用させることで解決します。

メインの `<PropertyGroup>` ノードに追加する 3 つの設定があります。 

- **GenerateAssemblyInfo**\
このプロパティを `false` に設定すると、アセンブリ属性が生成されなくなります。 これにより、.NET Framework プロジェクトからの既存の `AssemblyInfo.cs` ファイルとの競合を回避できます。

- **AssemblyName**\
このプロパティの値は、コンパイル時に作成される出力バイナリです。 名前には、拡張子を追加する必要はありません。 たとえば、`MyCoreApp` を使用すると、`MyCoreApp.exe` が作成されます。

- **RootNamespace**\
プロジェクトで使用される既定の名前空間。 これは、.NET Framework プロジェクトの既定の名前空間と一致させる必要があります。

これら 3 つの要素を、`MyWPFCore.csproj` ファイルの `<PropertyGroup>` ノードに追加します。

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>ソース コードを追加する
現時点では、**MyWPFCore.csproj** プロジェクトには、コンパイルされるコードはありません。 既定では、.NET Core プロジェクトには、現在のディレクトリとすべての子ディレクトリ内のすべてのソース コードが自動的に含まれます。 相対パスを使用して、.NET Framework プロジェクトのコードが含まれるようにプロジェクトを構成する必要があります。 .NET Framework プロジェクトで、ウィンドウとコントロールのアイコンとリソース用の **.resx** ファイルが使用されている場合は、それらも含める必要があります。 

プロジェクトに追加する必要がある最初の `<ItemGroup>` ノードには、アプリで使用されるスタートアップ構成とリソースを表す **App.xaml** ファイルがあります。 **App.xaml** ファイルには **App.xaml.cs** ファイルも付随しますが、それは別の `<ItemGroup>` に自動的に入ります。

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

次に、次の `<ItemGroup>` コードをプロジェクトに追加します。 各ステートメントには、子ディレクトリを含むファイルの glob パターンが含まれています。 これには、プロジェクトのソース コード、設定ファイル、リソースが含まれます。 **obj** ディレクトリは明示的に除外されます。

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

次に、**App.xaml** ファイルを除くすべての **xaml** ファイルの `<Page>` エントリが含まれる別の `<ItemGroup>` ノードをプロジェクトに含めます。 これには、**xaml** 形式のすべてのウィンドウ、ページ、リソースが含まれます。 ここでは glob パターンを使用できません。ファイルごとにエントリを追加し、使用されている `<Generator>` を示す必要があります。

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>NuGet パッケージを追加する

.NET Framework プロジェクトによって参照される各 NuGet パッケージを.NET Core プロジェクトに追加します。 

ほとんどの場合、.NET Framework WPF アプリには、**packages.config** プロジェクトによって参照されるすべての NuGet パッケージの一覧を含むファイルがあります。 この一覧を調べて、.NET Core プロジェクトに追加する NuGet パッケージを決定できます。 たとえば、.NET Framework プロジェクトで `MahApps.Metro` NuGet パッケージが参照される場合、Visual Studio でそれをプロジェクトに追加します。 **SolutionFolder** ディレクトリから .NET Core CLI を使用してパッケージ参照を追加することもできます。

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

上のコマンドによって、次の NuGet 参照が **MyWPFCore.csproj** プロジェクトに追加されます。

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>コンパイルの問題

プロジェクトのコンパイルで問題が発生した場合は、.NET Framework では使用できるが .NET Core では使用できない Windows 専用 API が使用されている可能性があります。 [Windows 互換機能パック][compat-pack] NuGet パッケージのプロジェクトへの追加を試すことができます。 このパッケージは Windows でのみ実行され、約 20,000 の Windows API を .NET Core と .NET Standard プロジェクトに追加します。

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

前のコマンドにより、以下が **MyWPFCore.csproj** プロジェクトに追加されます。

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>WPF デザイナー

この記事で説明したように、Visual Studio 2019 では、.NET Framework プロジェクトでのみ WPF デザイナーがサポートされます。 サイドバイサイドの .NET Core プロジェクトを作成することで、.NET Framework プロジェクトを使用してフォームをデザインしながら、.NET Core でプロジェクトをテストできます。 ソリューション ファイルには、.NET Framework と .NET Core の両方のプロジェクトが含まれます。 .NET Framework プロジェクトにフォームとコントロールを追加してデザインし、.NET Core プロジェクトに追加されたファイルの glob パターンに基づいて、新しいファイルまたは変更されたファイルが、.NET Core プロジェクトに自動的に追加されます。

Visual Studio 2019 で WPF デザイナーがサポートされるようになったら、.NET Core プロジェクト ファイルの内容を .NET Framework プロジェクト ファイルにコピーして貼り付けることができます。 その後、`<Source>` と `<EmbeddedResource>` 項目を使用して追加されたファイルの glob パターンを削除します。 アプリで使用されるすべてのプロジェクト参照のパスを修正します。 これにより、.NET Framework プロジェクトが .NET Core プロジェクトに効率的にアップグレードされます。
 
## <a name="next-steps"></a>次の手順

* [Windows 互換機能パック][compat-pack]の詳細を確認する。
* .NET Framework WPF プロジェクトの .NET Core への[移植に関するビデオ](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt)を視聴する。

[compat-pack]: windows-compat-pack.md
