---
title: '方法: インストールされている WPF のバージョンを確認する'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305677"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>方法: インストールされている WPF のバージョンを確認する
現在インストールされているバージョンのバージョン番号[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]にある、**レジストリ**します。  
  
 バージョン番号を検索するには。  
  
1. **[スタート]** メニューで、 **[ファイル名を指定して実行]** をクリックします。  
  
2. **オープン**、型**regedit.exe**します。  
  
3. 次のキーを開きます。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にバージョン番号が格納されている、**バージョン**値。
