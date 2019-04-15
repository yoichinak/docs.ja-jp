---
title: '方法: StackPanel または DockPanel を選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: 8338421dfb1bea856c15edf9d324cec955584f9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206968"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>方法: StackPanel または DockPanel を選択する
この例では、使用するか、<xref:System.Windows.Controls.StackPanel>または<xref:System.Windows.Controls.DockPanel>でコンテンツをスタックする、<xref:System.Windows.Controls.Panel>します。  
  
## <a name="example"></a>例  
 いずれかを使用できますが、<xref:System.Windows.Controls.DockPanel>または<xref:System.Windows.Controls.StackPanel>を子要素をスタックには、2 つのコントロールは、常に結果を生成しない、同じです。 たとえば、子要素を配置する順序は内の子要素のサイズに影響を<xref:System.Windows.Controls.DockPanel>ではなく、<xref:System.Windows.Controls.StackPanel>します。 このさまざまな問題の原因<xref:System.Windows.Controls.StackPanel>で積み重ねの方向にメジャー <xref:System.Double>.<xref:System.Double.PositiveInfinity>。 ただし、<xref:System.Windows.Controls.DockPanel>のみ使用可能なサイズを測定します。  
  
 次の例では、この主な違い<xref:System.Windows.Controls.DockPanel>と<xref:System.Windows.Controls.StackPanel>します。  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [パネルの概要](panels-overview.md)
