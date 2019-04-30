---
title: '方法: ページからウィンドウの幅を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: fee6d4c9ae9dae03e81cc4be56576763cb59958b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006717"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>方法: ページからウィンドウの幅を設定する
この例から、ウィンドウの幅を設定する方法を示しています、<xref:System.Windows.Controls.Page>します。  
  
## <a name="example"></a>例  
 A<xref:System.Windows.Controls.Page>を設定して、そのホスト ウィンドウの幅を設定できます<xref:System.Windows.Controls.Page.WindowWidth%2A>します。 このプロパティにより、<xref:System.Windows.Controls.Page>をそれをホストするウィンドウの種類の明示的な知識を持たない。  
  
> [!NOTE]
>  使用してウィンドウの幅を設定する<xref:System.Windows.Controls.Page.WindowWidth%2A>、<xref:System.Windows.Controls.Page>ウィンドウの子である必要があります。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
