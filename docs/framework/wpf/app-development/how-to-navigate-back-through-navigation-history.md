---
title: '方法: 移動履歴を遡る'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 53b32e145390d7052262042c7a793699c163b373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969350"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>方法: 移動履歴を遡る
この例は、"戻る" ナビゲーション履歴のエントリに移動する方法を示しています。  
  
## <a name="example"></a>例  
 、、または Internet Explorer <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame>を使用して<xref:System.Windows.Navigation.NavigationService>、でホストされているコンテンツから実行されているコードは、一度に1つずつナビゲーション履歴に戻ることができます。  
  
 1つ前のエントリに移動するには、最初に、 **GoBack**メソッドを呼び出して、 **CanGoBack**プロパティを調べて、1つ前のエントリに戻る前に、戻るナビゲーション履歴にエントリがあることを確認する必要があります。 これを次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack**と**GoBack**は、、 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame>、および<xref:System.Windows.Navigation.NavigationService>によって実装されます。  
  
> [!NOTE]
> **GoBack**を呼び出し、[戻る] ナビゲーション履歴<xref:System.InvalidOperationException>にエントリがない場合は、が発生します。
