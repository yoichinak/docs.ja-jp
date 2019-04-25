---
title: '方法: DockPanel を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], creating
ms.assetid: 9194f663-e279-4f1a-86d7-125a57d05c6f
ms.openlocfilehash: 35434a13386ae89fdc1428bd632d21c1551c9871
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911124"
---
# <a name="how-to-create-a-dockpanel"></a>方法: DockPanel を作成する
## <a name="example"></a>例  
 次の例は、作成しのインスタンスを使用して<xref:System.Windows.Controls.DockPanel>コードを使用しています。 例は、5 つを作成して領域をパーティション分割する方法を示します<xref:System.Windows.Shapes.Rectangle>要素と配置 (ドッキング)、親の内部に<xref:System.Windows.Controls.DockPanel>します。 既定の設定を保持する場合、最終的な四角形が残りの未割り当て領域を塗りつぶします。  
  
 [!code-csharp[DockPanelCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelCode/CSharp/DockPanel_Code.cs#1)]
 [!code-vb[DockPanelCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelCode/VisualBasic/dockpanel_vb.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Dock>
- [パネルの概要](panels-overview.md)
