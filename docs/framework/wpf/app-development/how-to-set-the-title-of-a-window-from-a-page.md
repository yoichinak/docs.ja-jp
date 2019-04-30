---
title: '方法: ページからウィンドウのタイトルを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 55444de6c61107979307b94910ba944e7001cf9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054004"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>方法: ページからウィンドウのタイトルを設定する
この例は、ウィンドウのタイトルを設定する方法を示しています、<xref:System.Windows.Controls.Page>がホストされています。  
  
## <a name="example"></a>例  
 ページを設定してそれをホストしているウィンドウのタイトルを変更することができます、<xref:System.Windows.Controls.Page.WindowTitle%2A>プロパティ、次のようにします。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  設定、<xref:System.Windows.Controls.Page.Title%2A>ページのプロパティには、ウィンドウのタイトルの値は変わりません。 代わりに、<xref:System.Windows.Controls.Page.Title%2A>ナビゲーション履歴にページ エントリの名前を指定します。
