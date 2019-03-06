---
title: '方法: ページの読み込みを停止します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
ms.openlocfilehash: c5694bb2cb6c618cd84bad3dc893ae3855e44892
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357847"
---
# <a name="how-to-stop-a-page-from-loading"></a>方法: ページの読み込みを停止します。
この例では、呼び出し、<xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A>ダウンロードが完了前に、コンテンツへの移動を停止するメソッド。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> 要求されたコンテンツのダウンロードを停止し、<xref:System.Windows.Navigation.NavigationWindow.NavigationStopped>イベントが発生します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
