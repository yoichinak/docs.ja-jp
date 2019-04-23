---
title: '方法: Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: dcaabf9ecd47bc88095e92aa8ed28ad5f13fd1dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314374"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>方法: Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] インターネット ゾーン アクセス許可のセットに制限されている部分信頼セキュリティ サンド ボックス内で実行します。 このアクセス許可セットのみであるサービスを Web に Web サービス呼び出しを制限する、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]アプリケーションの起点サイト。 ときに、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]は、デバッグ、Visual Studio 2005 とは見なされません起点のサイトと同じように、Web サービスが参照にします。 ときに発生します。 このエラーの原因のセキュリティ例外、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web サービスを呼び出すしようとしています。 ただし、Visual Studio 2005[!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]プロジェクトは、デバッグ中に呼び出す Web サービスと同じサイトの配信元をシミュレートするように構成できます。 これにより、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]を安全にセキュリティ例外を発生させることがなく、Web サービスを呼び出します。

## <a name="configuring-visual-studio"></a>Visual Studio の構成
 デバッグを Visual Studio 2005 を構成する、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web サービスを呼び出します。

1. **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

2. **プロジェクト デザイナー**、クリックして、**デバッグ**タブ。

3. **開始動作**セクションで、**外部プログラムの開始**」と入力します。

     `C:\WINDOWS\System32\PresentationHost.exe`

4. **開始オプション**セクションで、次の点を入力してください、**コマンドライン引数**テキスト ボックス。

     `-debug`  *filename*

     *ファイル名*の値、 **-デバッグ**パラメーターが .xbap ファイル名。 例。

     `-debug c:\example.xbap`

> [!NOTE]
>  これは、Visual Studio 2005 で作成したソリューションの既定の構成は、[!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]プロジェクト テンプレート。

1. **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

2. **プロジェクト デザイナー**、クリックして、**デバッグ**タブ。

3. **開始オプション**セクションで、次のコマンド ライン パラメーターを追加、**コマンドライン引数**テキスト ボックス。

     `-debugSecurityZoneURL`  *URL*

     *URL*値、 **- debugSecurityZoneURL**パラメーターは、[!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)]の場所として、アプリケーションの起点のサイトをシミュレートします。

 たとえばを検討してください、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]に次の Web サービスを使用する[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 起点サイト[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]この Web サービスは。

 `http://services.msdn.microsoft.com`

 その結果、完全な **- debugSecurityZoneURL**コマンド ライン パラメーターと値には。

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>関連項目

- [WPF ホスト (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
