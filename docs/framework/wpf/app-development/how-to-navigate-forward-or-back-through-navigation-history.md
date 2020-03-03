---
title: '方法: 移動履歴の前後への移動'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: 76a78debdce14123cc465ac9abf4db906fe0a2df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961352"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>方法: 移動履歴の前後への移動
この例では、ナビゲーション履歴のエントリに前方または後方に移動する方法を示します。  
  
## <a name="example"></a>例  
 次のホストのコンテンツから実行されるコードは、一度に1つずつ、ナビゲーション履歴を前方または後方に移動できます。  
  
- <xref:System.Windows.Navigation.NavigationWindow>従っ<xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame>従っ<xref:System.Windows.Navigation.NavigationService>  
  
- Internet Explorer  
  
 1つ前のエントリに移動する前に、まず、 **CanGoForward**プロパティを調べることによって、"進む" ナビゲーション履歴にエントリがあることを確認する必要があります。 1つ前のエントリに移動するには、 **Goforward**メソッドを呼び出します。 これを次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 1つ前のエントリに移動するには、まず、 **CanGoBack**プロパティを調べて、[戻る] ナビゲーション履歴にエントリがあることを確認する必要があります。 1つ前のエントリに移動するには、 **GoBack**メソッドを呼び出します。 これを次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**、 **goforward**、 **CanGoBack**、および**GoBack**は、、 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame>、および<xref:System.Windows.Navigation.NavigationService>によって実装されます。  
  
> [!NOTE]
> **Goforward**を呼び出し、"進む" ナビゲーション履歴にエントリがない場合、または**GoBack**を呼び出し、[戻る] ナビゲーション<xref:System.InvalidOperationException>履歴にエントリがない場合は、がスローされます。
