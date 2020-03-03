---
title: '方法: DockPanel 要素を使用して領域を分割する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960198"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>方法: DockPanel 要素を使用して領域を分割する
次の例では、 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.DockPanel>要素を使用して単純なフレームワークを作成します。 は<xref:System.Windows.Controls.DockPanel> 、子要素に使用できる領域をパーティション分割します。  
  
## <a name="example"></a>例  
 この例では<xref:System.Windows.Controls.DockPanel.Dock%2A> 、添付プロパティであるプロパティを使用して、パーティション<xref:System.Windows.Controls.Border>分割され<xref:System.Windows.Controls.Dock.Top>た領域のに同一の2つの要素をドッキングします。 3番<xref:System.Windows.Controls.Border>目の要素は<xref:System.Windows.Controls.Dock.Left>にドッキングされ、幅は200ピクセルに設定されます。 4番<xref:System.Windows.Controls.Border>目のは画面<xref:System.Windows.Controls.Dock.Bottom>のにドッキングされます。 最後<xref:System.Windows.Controls.Border>の要素は、残りの領域を自動的に入力します。  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> 既定では、 <xref:System.Windows.Controls.DockPanel>要素の最後の子が残りの未割り当て領域を塗りつぶします。 この動作にしない場合は、`LastChildFill="False"`を設定します。  
  
 コンパイル済みのアプリケーションでは、次のような新しい UI を生成します。  
  
 ![代表的な DockPanel シナリオ: ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DockPanel>
- [パネルの概要](panels-overview.md)
