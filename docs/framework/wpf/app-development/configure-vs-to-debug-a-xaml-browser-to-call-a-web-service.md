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
ms.openlocfilehash: e41dd46e4ddbdcde6448c68b4f9fb2e073baca43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958686"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>方法: Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]インターネットゾーンのアクセス許可セットに制限されている部分信頼セキュリティサンドボックス内で実行します。 このアクセス許可セットは、web サービスの呼び出しを、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]アプリケーションの起点サイトにある web サービスのみに制限します。 ただし、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]が Visual Studio 2005 からデバッグされている場合、参照している Web サービスと同じサイトの元のサイトがあるとは見なされません。 これにより、が Web サービスを呼び出そう[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]とすると、セキュリティ例外が発生します。 ただし、Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]プロジェクトは、デバッグ中に呼び出し元の Web サービスと同じサイトがあることをシミュレートするように構成できます。 これにより[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 、はセキュリティ例外を発生させることなく、Web サービスを安全に呼び出すことができます。

## <a name="configuring-visual-studio"></a>Visual Studio の構成
 Web サービスを呼び出すをデバッグ[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]するように Visual Studio 2005 を構成するには、次のようにします。

1. **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

2. **プロジェクトデザイナー**で、 **[デバッグ]** タブをクリックします。

3. **[開始アクション]** セクションで、 **[外部プログラムの開始]** を選択し、次のように入力します。

     `C:\WINDOWS\System32\PresentationHost.exe`

4. **[開始オプション]** セクションで、 **[コマンドライン引数]** ボックスに次の内容を入力します。

     `-debug`  */db*

     **-Debug**パラメーターの*filename*値は、. xbap ファイル名です。例えば：

     `-debug c:\example.xbap`

> [!NOTE]
> これは、Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]プロジェクトテンプレートを使用して作成されたソリューションの既定の構成です。

1. **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

2. **プロジェクトデザイナー**で、 **[デバッグ]** タブをクリックします。

3. **[開始オプション]** セクションで、次のコマンドラインパラメーターを **[コマンドライン引数]** テキストボックスに追加します。

     `-debugSecurityZoneURL`  *URL*

     **-Debugsecurityゾーン url**パラメーターの[!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] *url*値は、アプリケーションの起点サイトとしてシミュレートする場所のになります。

 例として、次[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]のような Web サービスを使用するについて考えてみます。

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 この Web サービスの[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]起点サイトは次のとおりです。

 `http://services.msdn.microsoft.com`

 その結果、完全な**debugsecurityゾーン url**コマンドラインパラメーターと値は次のようになります。

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>関連項目

- [WPF ホスト (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
