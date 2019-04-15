---
title: '方法: Dock の値を取得または設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: fb6c8a7d62aa09a6e1d82cb4079d1425a7f39f8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160740"
---
# <a name="how-to-get-or-set-a-dock-value"></a>方法: Dock の値を取得または設定する
次の例を割り当てる方法を示しています、<xref:System.Windows.Controls.Dock>オブジェクトの値。 この例では、<xref:System.Windows.Controls.DockPanel.GetDock%2A>と<xref:System.Windows.Controls.DockPanel.SetDock%2A>メソッドの<xref:System.Windows.Controls.DockPanel>します。  
  
## <a name="example"></a>例  
 例では、インスタンスを作成する、<xref:System.Windows.Controls.TextBlock>要素、 `txt1`、割り当てます、<xref:System.Windows.Controls.Dock>の値`Top`を使用して、<xref:System.Windows.Controls.DockPanel.SetDock%2A>メソッドの<xref:System.Windows.Controls.DockPanel>します。 値を追加し、<xref:System.Windows.Controls.Dock>プロパティを<xref:System.Windows.Controls.TextBlock.Text%2A>の<xref:System.Windows.Controls.TextBlock>要素を使用して、<xref:System.Windows.Controls.DockPanel.GetDock%2A>メソッド。 最後に、例、<xref:System.Windows.Controls.TextBlock>要素を親<xref:System.Windows.Controls.DockPanel>、`dp1`します。  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [パネルの概要](panels-overview.md)
