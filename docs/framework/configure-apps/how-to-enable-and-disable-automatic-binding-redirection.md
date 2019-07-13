---
title: 自動バインディング リダイレクトを有効/無効にする方法
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b6c9c3508c53e8a68a3f7e1cb12b6b6c95600e7b
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380098"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>方法: 自動バインディング リダイレクトを有効/無効にする

Visual Studio .NET Framework 4.5.1 を対象と以降のバージョンでアプリをコンパイルするときにアセンブリの統一をオーバーライドするアプリの構成ファイルにバインド リダイレクトを自動的に追加可能性があります。 アプリの構成ファイルで手動でバインド リダイレクトを指定している場合でも、アプリまたはそのコンポーネントが同じアセンブリの複数バージョンを参照している場合、バインド リダイレクトが追加されます。 自動バインド リダイレクトの機能に影響を与えますデスクトップ アプリと web アプリ .NET Framework 4.5.1 を対象にまたは以降のバージョンが動作は、web アプリに少しずつ異なります。 既存のアプリ、.NET Framework のターゲットを以前のバージョンがあるか、バインド リダイレクトを手動で作成する場合は、この機能を無効にすることができる場合、自動バインド リダイレクトを有効にできます。

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>デスクトップ アプリで自動バインド リダイレクトを無効にします。

.NET Framework 4.5.1 以降のバージョンを対象にした Windows デスクトップ アプリの既定では、自動バインド リダイレクトが有効にします。 バインド リダイレクトは、出力の構成に追加されます (**app.config**)、アプリがコンパイルされたときにファイルおよび配置する可能性のあるアセンブリの統一をオーバーライドします。 ソース**app.config**ファイルは変更されません。 この機能を無効にするには、アプリのプロジェクト ファイルを変更するか、Visual Studio でプロジェクトのプロパティのチェック ボックスの選択を解除します。

### <a name="disable-through-project-properties"></a>プロジェクトのプロパティを無効にします。

Visual Studio 2017 バージョン 15.7 以降があれば、簡単にプロジェクトのプロパティ ページで自動生成されたバインド リダイレクトを無効にすることができます。

1. **ソリューション エクスプローラー**でプロジェクトを右クリックして、 **[プロパティ]** を選択します。

2. **アプリケーション** ページで、オフに、**自動生成バインド リダイレクト**オプション。

3. キーを押して**Ctrl**+**S**の変更を保存します。

### <a name="disable-manually-in-the-project-file"></a>プロジェクト ファイルを手動で無効にします。

1. 次のメソッドのいずれかを使用して編集するためのプロジェクト ファイルを開きます。

   - Visual studio でプロジェクトを選択**ソリューション エクスプ ローラー**を選び、**ファイル エクスプ ローラーでフォルダーを開く**ショートカット メニューから。 ファイル エクスプ ローラーでプロジェクト (.csproj または .vbproj) ファイルを検索し、メモ帳で開きます。
   - Visual Studio での**ソリューション エクスプ ローラー**でプロジェクトを右クリックし、選択**プロジェクトのアンロード**します。 ここでも、アンロードされたプロジェクトを右クリックして **編集 [projectname.csproj]** します。

2. プロジェクト ファイルで、次のプロパティ エントリを検索します。

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. `true` を `false` に変更します。

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>自動バインド リダイレクトを手動で有効にします。

旧バージョンを対象を自動的に求められたら、リダイレクトを追加する場合や、.NET Framework の既存のアプリで自動バインド リダイレクトを有効にできます。 新しいバージョンの framework を対象としているリダイレクトの追加を自動的に求められません場合は、ビルド出力アセンブリを再マップすることを示す可能性がありますが表示されます。

1. 次のメソッドのいずれかを使用して編集するためのプロジェクト ファイルを開きます。

   - Visual studio でプロジェクトを選択**ソリューション エクスプ ローラー**を選び、**ファイル エクスプ ローラーでフォルダーを開く**ショートカット メニューから。 ファイル エクスプ ローラーでプロジェクト (.csproj または .vbproj) ファイルを検索し、メモ帳で開きます。
   - Visual Studio での**ソリューション エクスプ ローラー**でプロジェクトを右クリックし、選択**プロジェクトのアンロード**します。 ここでも、アンロードされたプロジェクトを右クリックして **編集 [projectname.csproj]** します。

2. 最初の構成プロパティ グループに次の要素を追加 (で、 \<PropertyGroup > タグ)。

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   次の要素が挿入されたプロジェクト ファイルの例を次に示します。

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. アプリをコンパイルします。

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Web apps での自動バインド リダイレクトを有効にします。

自動バインド リダイレクトは、Web アプリでは異なる方法で実装されます。 ソースの構成 (**web.config**) ファイルは、web アプリを変更する必要があります、バインド リダイレクトは自動的に追加されません、構成ファイルにします。 ただし、Visual Studio によってバインドの競合が通知されるため、バインド リダイレクトを追加して競合を解決できます。 常にバインド リダイレクトを追加する指示に従い、ため、web アプリに対してこの機能を明示的に無効にする必要はありません。

バインド リダイレクトを追加する、 **web.config**ファイル。

1. Visual Studio で、アプリをコンパイルし、ビルドの警告を確認します。

   ![ビルドのアセンブリ参照の競合の警告](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. アセンブリ バインドの競合がある場合、警告が表示されます。 警告をダブルクリックするか、警告とキーを押して選択**Enter**します。

   ダイアログ ボックスに自動的に必要なバインドを追加することができますが、ソースにリダイレクト**web.config**ファイルが表示されます。

   ![バインド リダイレクトのアクセス許可ダイアログ](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>関連項目

- [\<bindingRedirect > 要素](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
