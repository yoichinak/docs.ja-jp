---
title: '方法: ScrollChanged イベントの処理'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], raising ScrollChanged events
- ScrollChanged events [WPF]
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
ms.openlocfilehash: 34a3c97453df334e8c12da1a31cfb029294da687
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352522"
---
# <a name="how-to-handle-the-scrollchanged-event"></a>方法: ScrollChanged イベントの処理
## <a name="example"></a>例  
 この例では、処理、<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>のイベントを<xref:System.Windows.Controls.ScrollViewer>します。  
  
 A<xref:System.Windows.Documents.FlowDocument>を持つ要素<xref:System.Windows.Documents.Paragraph>で定義されているパーツ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 ときに、<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>イベントは、ユーザーの相互作用のために発生します、ハンドラーが呼び出されると、およびテキストを書き込む、<xref:System.Windows.Controls.TextBlock>イベントが発生したことを示します。  
  
 [!code-xaml[scrollchangedeventargsLayout#1](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xaml[scrollchangedeventargsLayout#2](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>
- <xref:System.Windows.Controls.ScrollChangedEventHandler>
- <xref:System.Windows.Controls.ScrollChangedEventArgs>
