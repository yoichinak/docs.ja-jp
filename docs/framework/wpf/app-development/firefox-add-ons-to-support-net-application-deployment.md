---
title: .NET アプリケーションの配置をサポートするための Firefox のアドオン
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 6e8a333fc84eb85b7a312cb87207ebc235fbfe9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424565"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>.NET アプリケーションの配置をサポートするための Firefox のアドオン
Firefox 用の Windows Presentation Foundation (WPF) プラグインと Firefox 用の .NET Framework Assistant を使用すると、XAML ブラウザーアプリケーション (Xbap)、ルース [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、ClickOnce アプリケーションが Mozilla Firefox ブラウザーで動作できるようになります。  
  
## <a name="wpf-plug-in-for-firefox"></a>Firefox 用 WPF プラグイン  
 Firefox 用の WPF プラグインを使用すると、Xbap およびルース [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルは、Firefox ブラウザーの最上位または HTML IFRAME に移動して実行できます。 XBAP は [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションであり、Web サーバーに発行し、サポートされているブラウザー内で起動できます。 緩い [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は、XML ファイルのように、サポートされているブラウザーに移動して表示できる XAML のみのファイルです。  
  
 Firefox 用の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プラグインは、.NET Framework 3.5 と共にインストールされます。 ウィンドウ7には .NET Framework 3.5 が含まれていますが、Firefox の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プラグインは含まれていません。 Windows 7 に Firefox 用の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プラグインをインストールすることはできません。  
  
 .NET Framework 4 には、Firefox の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プラグインは含まれていません。 ただし、.NET Framework 3.5 と .NET Framework 4 の両方がインストールされている場合、Firefox 用の WPF プラグインは .NET Framework 3.5 と共にインストールされます。 そのため .NET Framework 4 つのアプリケーションが引き続き実行されます。これは、WPF ホストが正しいバージョンのフレームワークを読み込むためです。 詳細については、「 [WPF ホスト (プレゼンテーション用のホスト .exe)](wpf-host-presentationhost-exe.md)」を参照してください。  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 Firefox 用の .NET Framework Assistant を使用すると、スタンドアロンの ClickOnce アプリケーションを Firefox ブラウザーから実行できます。 Firefox ブラウザーの前と後にインストールされている場合、Firefox の .NET Framework Assistant は同じように機能します。 Firefox ブラウザーが起動し .NET Framework 3.5 SP1 がインストールされると、firefox の .NET Framework Assistant が検索され、インストールされます。 ユーザーは、Firefox の .NET Framework Assistant を次のように構成できます。  
  
- ClickOnce アプリケーションを実行する前にプロンプトを表示します。  
  
- インストールされているすべてのバージョンの .NET Framework または最新バージョンのみを報告します。  
  
 Firefox の .NET Framework Assistant は、.NET Framework 3.5 SP1 に含まれています。 Firefox の .NET Framework Assistant の削除の詳細については、「 [firefox の .NET Framework assistant を削除する方法](https://go.microsoft.com/fwlink/?LinkId=177944)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)
- [WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)
- [Firefox に対応した WPF プラグインがインストールされているかどうかを確認する](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
