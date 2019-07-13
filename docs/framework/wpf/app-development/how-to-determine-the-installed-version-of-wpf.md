---
title: '方法: インストールされている WPF のバージョンを確認する'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052457"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>方法: インストールされている WPF のバージョンを確認する
現在インストールされているバージョンのバージョン番号[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]にある、**レジストリ**します。  
  
 バージョン番号を検索するには。  
  
1. **[スタート]** メニューで、 **[ファイル名を指定して実行]** をクリックします。  
  
2. **オープン**、型**regedit.exe**します。  
  
3. 次のキーを開きます。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にバージョン番号が格納されている、**バージョン**値。
