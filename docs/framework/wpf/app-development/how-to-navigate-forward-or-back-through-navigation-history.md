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
ms.openlocfilehash: 00a41fcf85583ec0d081a2fa099f3a77cfcd2900
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625352"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>方法: 移動履歴の前後への移動
この例では、ナビゲーション履歴にエントリに前後を移動する方法を示します。  
  
## <a name="example"></a>例  
 次のホスト内のコンテンツから実行するコードは、ナビゲーション履歴、一度に 1 つのエントリを前後に移動できます。  
  
- <xref:System.Windows.Navigation.NavigationWindow> 使用してください。 <xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame> 使用してください。 <xref:System.Windows.Navigation.NavigationService>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 前方の 1 つのエントリを移動する前にする必要があります最初ことを確認エントリ"進む"ナビゲーション履歴を調べることによって、 **CanGoForward**プロパティ。 転送の 1 つのエントリを移動するを呼び出す、 **GoForward**メソッド。 これは、次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 1 つのエントリをバックアップ移動するを調べることによって"戻る"ナビゲーション履歴にエントリが表示されている最初に確認する必要があります、 **CanGoBack**プロパティ。 1 つ戻りますエントリを移動するを呼び出す、 **GoBack**メソッド。 これは、次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**、 **GoForward**、 **CanGoBack**、および**GoBack**によって実装される<xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Frame>、および<xref:System.Windows.Navigation.NavigationService>します。  
  
> [!NOTE]
>  呼び出す場合**GoForward**、"進む"ナビゲーション履歴にエントリがないと、または呼び出す場合**GoBack**、戻るナビゲーション履歴にエントリがないと、<xref:System.InvalidOperationException>がスローされます。
