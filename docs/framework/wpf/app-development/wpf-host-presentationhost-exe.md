---
title: WPF ホスト (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: cdd2b451324b1a0edd7aa76494da72623b8326ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591266"
---
# <a name="wpf-host-presentationhostexe"></a>WPF ホスト (PresentationHost.exe)
Windows Presentation Foundation (WPF) のホスト (PresentationHost.exe) は、アプリケーションを使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]互換性のあるブラウザーでホストされるアプリケーション (を含む[!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)]以降)。 シェルとして既定では、Windows Presentation Foundation (WPF) のホストが登録されていると[!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)]ハンドラーをブラウザーでホストされる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]コンテンツが含まれます。  
  
- Loose (コンパイルされていない) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル (.xaml)。  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap)。  
  
 これらの型では、Windows Presentation Foundation (WPF) のホストのファイル。  
  
- 登録されている起動[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]Windows Presentation Foundation (WPF) コンテンツをホストするハンドラー。  
  
- 必須の正しいバージョンを読み込みます[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]と Windows Presentation Foundation (WPF) のアセンブリ。  
  
- 展開のゾーンに適切なアクセス許可レベルが設定されるようにします。  
  
 このトピックでは、PresentationHost.exe で使用できるコマンド ライン パラメーターについて説明します。  
  
## <a name="usage"></a>使用方法  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|ファイル名|アクティブにするファイルのパス。 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] も指定できます。|  
|-debug|アプリケーションをアクティブにする場合に、このアプリケーションをストアにコミットしたり、ストアから実行しません。 これは、ローカル ファイルをアクティブにする場合に限って使用できます。|  
|-debugSecurityZoneURL \<url>|アプリケーションを、指定した [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] から展開されたものとしてデバッグする必要があることを PresentationHost.exe に指示するために、[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 値と共に使用します。 これは、展開ゾーンと起点サイトの両方を決定します。|  
|-embedding|OLE で必要になります。 `-event` パラメーターまたは `-debug` パラメーターを指定した場合、`-embedding` パラメーターは内部で設定されるため、指定する必要はありません。|  
|-event \<eventname>|PresentationHost.exe が初期化され、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツをホストする準備ができた時点で、この名前のイベントを開き、シグナルを送信します。 PresentationHost.exe は、イベントを開く際にエラーが発生すると (そのイベントがまだ作成されていない場合など) 終了します。|  
|-launchApplication \<url>|指定した URL から、スタンドアロンの [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] アプリケーションを起動します。 .NET アプリケーションに関する [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] と WinINet のセキュリティ ポリシーが適用されます。|  
  
## <a name="scenarios"></a>シナリオ  
  
### <a name="shell-handler"></a>シェル ハンドラー  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>MIME ハンドラー  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Visual Studio によるデバッグ  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Visual Studio によるゾーンでのデバッグ  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>関連項目

- [セキュリティ](../security-wpf.md)
