---
title: 自動バインディング リダイレクトを有効/無効にする方法
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: d914310559403fba2f1fe8e4a60469ec3a867c24
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733448"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>方法: 自動バインディング リダイレクトを有効/無効にする

.NET Framework 4.5.1 以降のバージョンを対象とする Visual Studio でアプリをコンパイルすると、アセンブリの統一をオーバーライドするために、アプリケーション構成ファイルにバインドリダイレクトが自動的に追加される場合があります。 アプリの構成ファイルで手動でバインド リダイレクトを指定している場合でも、アプリまたはそのコンポーネントが同じアセンブリの複数バージョンを参照している場合、バインド リダイレクトが追加されます。 自動バインドリダイレクト機能は、.NET Framework 4.5.1 以降のバージョンを対象とするデスクトップアプリと web アプリに影響します。ただし、web アプリで動作は少し異なります。 以前のバージョンの .NET Framework を対象とする既存のアプリがある場合は、自動バインドリダイレクトを有効にすることができます。また、バインディングリダイレクトを手動で作成する場合は、この機能を無効にすることもできます。

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>デスクトップアプリでの自動バインドリダイレクトを無効にする

.NET Framework 4.5.1 以降のバージョンを対象とする Windows デスクトップアプリでは、自動バインドリダイレクトが既定で有効になっています。 バインドリダイレクトは、アプリがコンパイルされるときに出力構成 (**app.config**) ファイルに追加され、それ以外の場合に発生する可能性があるアセンブリの統一をオーバーライドします。 ソース**app.config**ファイルは変更されません。 この機能を無効にするには、アプリのプロジェクトファイルを変更するか、Visual Studio でプロジェクトの [プロパティ] のチェックボックスをオフにします。

### <a name="disable-through-project-properties"></a>プロジェクトのプロパティを使用して無効化

Visual Studio 2017 バージョン15.7 以降を使用している場合は、プロジェクトのプロパティページで自動生成されたバインドリダイレクトを無効にすることができます。

1. **ソリューション エクスプローラー**でプロジェクトを右クリックして、 **[プロパティ]** を選択します。

2. [**アプリケーション**] ページで、[**バインドリダイレクトを自動生成**する] オプションをオフにします。

3. **Ctrl**+**S**キーを押して変更を保存します。

### <a name="disable-manually-in-the-project-file"></a>プロジェクトファイルで手動で無効にする

1. 次のいずれかの方法を使用して、プロジェクトファイルを編集用に開きます。

   - Visual Studio で**ソリューションエクスプローラー**でプロジェクトを選択し、ショートカットメニューの [**エクスプローラーでフォルダーを開く**] をクリックします。 ファイルエクスプローラーで、プロジェクト (.csproj または .vbproj) ファイルを見つけ、メモ帳で開きます。
   - Visual Studio の**ソリューションエクスプローラー**で、プロジェクトを右クリックし、[**プロジェクトのアンロード**] を選択します。 アンロードされたプロジェクトをもう一度右クリックし、[**編集] [projectname. .csproj]** の順に選択します。

2. プロジェクト ファイルで、次のプロパティ エントリを検索します。

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. `true` を `false` に変更します。

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>自動バインドリダイレクトを手動で有効にする

以前のバージョンの .NET Framework を対象とする既存のアプリで自動バインドリダイレクトを有効にすることができます。また、自動的にリダイレクトを追加するように求められない場合は、リダイレクトを有効にすることもできます。 新しいバージョンのフレームワークを対象としていても、自動的にリダイレクトの追加を求めるメッセージが表示されない場合は、アセンブリの再マップを提案するビルド出力が得られる可能性があります。

1. 次のいずれかの方法を使用して、プロジェクトファイルを編集用に開きます。

   - Visual Studio で**ソリューションエクスプローラー**でプロジェクトを選択し、ショートカットメニューの [**エクスプローラーでフォルダーを開く**] をクリックします。 ファイルエクスプローラーで、プロジェクト (.csproj または .vbproj) ファイルを見つけ、メモ帳で開きます。
   - Visual Studio の**ソリューションエクスプローラー**で、プロジェクトを右クリックし、[**プロジェクトのアンロード**] を選択します。 アンロードされたプロジェクトをもう一度右クリックし、[**編集] [projectname. .csproj]** の順に選択します。

2. 最初の構成プロパティグループ (PropertyGroup > タグの\<下) に次の要素を追加します。

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   要素が挿入されたプロジェクトファイルの例を次に示します。

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. アプリをコンパイルします。

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Web アプリで自動バインドリダイレクトを有効にする

自動バインド リダイレクトは、Web アプリでは異なる方法で実装されます。 ソース構成 (**web.config**) ファイルは web apps 用に変更する必要があるため、バインドリダイレクトは構成ファイルに自動的に追加されません。 ただし、Visual Studio によってバインドの競合が通知されるため、バインド リダイレクトを追加して競合を解決できます。 バインドリダイレクトを追加するように求められるので、web アプリに対してこの機能を明示的に無効にする必要はありません。

**Web.config** ファイルにバインドリダイレクトを追加するには、次のようにします。

1. Visual Studio で、アプリをコンパイルし、ビルドの警告を確認します。

   ![アセンブリ参照の競合に関するビルド警告](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. アセンブリ バインドの競合がある場合、警告が表示されます。 警告をダブルクリックするか、警告を選択して**enter** キーを押します。

   ソースの**web.config**ファイルに必要なバインドリダイレクトを自動的に追加できるダイアログボックスが表示されます。

   ![バインドリダイレクトのアクセス許可ダイアログ](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>関連項目

- [\<bindingRedirect > 要素](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
