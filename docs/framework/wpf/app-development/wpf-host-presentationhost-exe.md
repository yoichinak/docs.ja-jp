---
title: WPF ホスト (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: ec8ec42c174d87834af5d4c651c1e8c8bde3b3e2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581699"
---
# <a name="wpf-host-presentationhostexe"></a>WPF ホスト (PresentationHost.exe)
Windows Presentation Foundation (WPF) ホスト (プレゼンテーションホスト .exe) は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを互換性のあるブラウザー (Microsoft Internet Explorer 6 以降を含む) でホストできるようにするアプリケーションです。 既定では、Windows Presentation Foundation (WPF) ホストは、ブラウザーでホストされる [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツのシェルおよび MIME ハンドラーとして登録されます。これには次のものが含まれます。  
  
- Loose (コンパイルされていない) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル (.xaml)。  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap)。  
  
 これらの種類のファイルについては、Windows Presentation Foundation (WPF) ホスト:  
  
- Windows Presentation Foundation (WPF) コンテンツをホストするために、登録されている HTML ハンドラーを起動します。  
  
- 必要な共通言語ランタイム (CLR) アセンブリと Windows Presentation Foundation (WPF) アセンブリの適切なバージョンを読み込みます。  
  
- 展開のゾーンに適切なアクセス許可レベルが設定されるようにします。  
  
 このトピックでは、PresentationHost.exe で使用できるコマンド ライン パラメーターについて説明します。  
  
## <a name="usage"></a>使用方法  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|ファイル名|アクティブにするファイルのパス。 は URI でもかまいません。|  
|-debug|アプリケーションをアクティブにする場合に、このアプリケーションをストアにコミットしたり、ストアから実行しません。 これは、ローカル ファイルをアクティブにする場合に限って使用できます。|  
|-debugSecurityZoneURL \<url>|指定された URL からアプリケーションが配置されているかのように、アプリケーションをデバッグする必要があることを示すために、URL 値と共に使用されます。 これは、展開ゾーンと起点サイトの両方を決定します。|  
|-embedding|OLE で必要になります。 `-event` パラメーターまたは `-debug` パラメーターを指定した場合、`-embedding` パラメーターは内部で設定されるため、指定する必要はありません。|  
|-event \<eventname>|PresentationHost.exe が初期化され、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツをホストする準備ができた時点で、この名前のイベントを開き、シグナルを送信します。 PresentationHost.exe は、イベントを開く際にエラーが発生すると (そのイベントがまだ作成されていない場合など) 終了します。|  
|-launchApplication \<url>|指定された URL からスタンドアロンの ClickOnce アプリケーションを起動します。 .NET アプリケーションに関する Internet Explorer と WinINet のセキュリティポリシーが適用されます。|  
  
## <a name="scenarios"></a>監視プロセス  
  
### <a name="shell-handler"></a>シェル ハンドラー  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>MIME ハンドラー  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Visual Studio によるデバッグ  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Visual Studio によるゾーンでのデバッグ  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>関連項目

- [Security](../security-wpf.md)
