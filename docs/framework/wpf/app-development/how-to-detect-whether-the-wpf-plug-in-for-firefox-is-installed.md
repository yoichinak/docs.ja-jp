---
title: '方法: Firefox に対応した WPF プラグインがインストールされているかどうかを確認する'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 3cc2f95627bc35fa4cb6c486d3b8ad61f69d7fea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372894"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>方法: Firefox に対応した WPF プラグインがインストールされているかどうかを確認する
Windows Presentation Foundation (WPF) の Firefox プラグインにより[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Mozilla Firefox ブラウザーで実行するための XAML ファイルが失われるとします。 このトピックでは、HTML と WPF の Firefox プラグインがインストールされているかどうかを判断する管理者が使用できる JavaScript で記述されたスクリプトを提供します。  
  
> [!NOTE]
>  インストール、展開、および検出の詳細については、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]を参照してください[開発者向けの .NET Framework のインストール](../../install/guide-for-developers.md)します。  
  
## <a name="example"></a>例  
 ときに、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]がインストールされている、クライアント コンピューターで構成されますプラグイン WPF firefox に対応します。 次のサンプル スクリプトでは、firefox に対応した WPF プラグインを確認し、適切な状態メッセージが表示されます。  
  
```  
<HTML>  
  
  <HEAD>  
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT type="text/javascript">  
    <!--  
    function OnLoad()  
    {  
  
       // Check for the WPF plug-in for Firefox and report  
       var msg = "The WPF plug-in for Firefox is ";  
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];  
       if( wpfPlugin != null ) {  
          document.writeln(msg + " installed.");  
       }  
       else {  
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");  
       }  
    }  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY onload="OnLoad()" />  
  
</HTML>  
```  
  
 Firefox に対応した WPF プラグインのチェックが成功した場合は、次のステータス メッセージが表示されます。  
  
 `The WPF plug-in for Firefox is installed.`  
  
 それ以外の場合、次のステータス メッセージが表示されます。  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>関連項目
- [.NET Framework 3.0 がインストールされているかどうかを確認する](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [.NET Framework 3.5 がインストールされているかどうかを確認する](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)
