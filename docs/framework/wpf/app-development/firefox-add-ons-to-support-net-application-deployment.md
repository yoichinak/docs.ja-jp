---
title: .NET アプリケーションの配置をサポートするための Firefox のアドオン
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: ea42710f7963f485675279f25623f26bfd5d4f48
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582959"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>.NET アプリケーションの配置をサポートするための Firefox のアドオン
Firefox と、.NET Framework Assistant for Firefox プラグイン Windows Presentation Foundation (WPF) を有効にする[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]、loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、Mozilla Firefox ブラウザーを使用する ClickOnce アプリケーションとします。  
  
## <a name="wpf-plug-in-for-firefox"></a>WPF Firefox プラグイン  
 有効にした WPF プラグイン Firefox[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]や loose[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]に移動して、または Firefox ブラウザーで HTML IFRAME の最上位で実行するファイル。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]は、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Web サーバーにパブリッシュして内で起動できるアプリケーションには、ブラウザーがサポートされています。 Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XAML 専用ファイルに移動し、XML ファイルと同様に、サポートされているブラウザーに表示されることです。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]と Firefox がインストールされているは、プラグイン、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]します。 Window 7 が含まれています、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]には含まれませんが、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox 用のプラグイン。 インストールすることはできません、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Windows 7、Firefox 用のプラグイン。  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]は含まれません、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox 用のプラグイン。 ただし、両方の場合、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]と[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]は、インストールされている WPF Firefox プラグインをインストールで、 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。 そのため[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]WPF ホストは、framework の正しいバージョンを読み込むためのアプリケーションは引き続き実行します。 詳細については、次を参照してください。 [WPF ホスト (PresentationHost.exe)](wpf-host-presentationhost-exe.md)します。  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 Firefox ブラウザーから実行するスタンドアロンの ClickOnce アプリケーションを .NET Framework Assistant for Firefox にできます。 .NET Framework Assistant の Firefox 関数、Firefox ブラウザーの前後にインストールされているときに同じです。 Firefox ブラウザーが起動したときに、[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]がインストールされている場合、Firefox で検索し、Firefox の .NET Framework Assistant をインストールします。 ユーザーは、.NET Framework Assistant for Firefox では、次の操作を構成できます。  
  
- ClickOnce アプリケーションを実行する前に確認します。  
  
- インストールされているすべてのバージョンの .NET Framework または最新バージョンのみを報告します。  
  
 含まれている、.NET Framework Assistant for Firefox、[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]します。 Firefox 用の .NET Framework Assistant の削除方法の詳細については、次を参照してください。 [Firefox 用の .NET Framework Assistant の削除方法](https://go.microsoft.com/fwlink/?LinkId=177944)します。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)
- [WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)
- [Firefox に対応した WPF プラグインがインストールされているかどうかを確認する](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
