---
title: '方法: ページに移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: c8e808180682bfd97f397d8cadd1e4deafd7eb06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947741"
---
# <a name="how-to-navigate-to-a-page"></a>方法: ページに移動する
この例で、ページからナビゲートできますをいくつかの方法を示しています、<xref:System.Windows.Navigation.NavigationWindow>します。  
  
## <a name="example"></a>例  
 可能性があります、<xref:System.Windows.Navigation.NavigationWindow>を使用して、次のいずれかのページに移動します。  
  
- <xref:System.Windows.Navigation.NavigationWindow.Source%2A> プロパティ。  
  
- <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> メソッド。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] 相対または絶対のいずれかを指定できます。 詳細については、「[WPF におけるパック URI](pack-uris-in-wpf.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
