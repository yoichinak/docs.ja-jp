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
ms.openlocfilehash: c489a1593b3d1f22fe1ad6e648d3f8a3f7a6cd44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947785"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>方法: 移動履歴を遡る
この例では、ナビゲーション履歴を戻るエントリに移動する方法を示します。  
  
## <a name="example"></a>例  
 ホストされているコンテンツから実行されているコードを<xref:System.Windows.Navigation.NavigationWindow>、<xref:System.Windows.Controls.Frame>を使用して<xref:System.Windows.Navigation.NavigationService>、または[!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]ナビゲーション履歴に、一度に 1 つのエントリを後方に移動できます。  
  
 1 エントリは、最初にチェックを調べることによってナビゲーションの履歴にエントリが表示ことが必要です、 **CanGoBack**プロパティ、1 つのエントリを呼び出すことによってバックアップを移動する前に、 **GoBack**メソッド。 これは、次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack**と**GoBack**によって実装される<xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Frame>、および<xref:System.Windows.Navigation.NavigationService>します。  
  
> [!NOTE]
>  呼び出す場合**GoBack**、戻るナビゲーション履歴にエントリがないと、<xref:System.InvalidOperationException>が発生します。
