---
title: '方法: ページからウィンドウの幅を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: 1e16b75ecb85550facdf24a5b9e341cf0c061178
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940775"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>方法: ページからウィンドウの幅を設定する
この例は、 <xref:System.Windows.Controls.Page>からウィンドウの幅を設定する方法を示しています。  
  
## <a name="example"></a>例  
 で<xref:System.Windows.Controls.Page>は、を設定<xref:System.Windows.Controls.Page.WindowWidth%2A>することによって、ホストウィンドウの幅を設定できます。 このプロパティを使用<xref:System.Windows.Controls.Page>すると、は、それをホストするウィンドウの種類に関する明示的な知識を持つことができません。  
  
> [!NOTE]
> を使用して<xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page>ウィンドウの幅を設定するには、がウィンドウの子である必要があります。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
