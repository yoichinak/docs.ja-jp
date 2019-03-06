---
title: '方法: ページがブラウザーでホストされているかを判断します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: ebc5612f059a6cf26f2568bbc08e705b4b3014c1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359992"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>方法: ページがブラウザーでホストされているかを判断します。
かどうか確認する方法を示します、<xref:System.Windows.Controls.Page>がブラウザーでホストされています。  
  
## <a name="example"></a>例  
 A<xref:System.Windows.Controls.Page>ホストに依存しないことができ、その結果、読み込むことができるなど、ホストのさまざまな種類に、 <xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Navigation.NavigationWindow>、またはブラウザー。 これは、1 つまたは複数のページを格納していると、複数のスタンドアロンによって参照されると、参照可能であるライブラリ アセンブリがある場合に発生することができます ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) アプリケーションをホストします。  
  
 次の例を使用する方法を示します<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>どうかを判断する<xref:System.Windows.Controls.Page>がブラウザーでホストされています。  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
