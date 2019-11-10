---
title: '方法 : Firefox に対応した WPF プラグインがインストールされているかどうかを確認する'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: fdc7b516c316c7efc7056b549baf43191a5aedd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423745"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>方法 : Firefox に対応した WPF プラグインがインストールされているかどうかを確認する

Firefox 用の Windows Presentation Foundation (WPF) プラグインを使用すると、XAML ブラウザーアプリケーション (Xbap) とルース XAML ファイルを Mozilla Firefox ブラウザーで実行できます。 このトピックでは、管理者が Firefox 用の WPF プラグインがインストールされているかどうかを判断するために使用できる HTML および JavaScript で記述されたスクリプトについて説明します。

> [!NOTE]
> .NET Framework のインストール、配置、および検出の詳細については、「[開発者向けの .NET Framework のインストール](../../install/guide-for-developers.md)」を参照してください。

## <a name="example"></a>例

.NET Framework 3.5 がインストールされている場合、クライアントコンピューターは Firefox 用の WPF プラグインを使用して構成されます。 次のサンプルスクリプトでは、Firefox 用の WPF プラグインを確認し、適切なステータスメッセージを表示します。

```html
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

Firefox の WPF プラグインの確認が成功すると、次のステータスメッセージが表示されます。

`The WPF plug-in for Firefox is installed.`

それ以外の場合は、次のステータスメッセージが表示されます。

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>関連項目

- [.NET Framework 3.0 がインストールされているかどうかを確認する](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [.NET Framework 3.5 がインストールされているかどうかを確認する](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)
