---
title: '方法: グリッドを使用して標準 UI ダイアログ ボックスをビルドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923416"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>方法: グリッドを使用して標準 UI ダイアログ ボックスをビルドする
この例では、 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.Grid>要素を使用して標準のダイアログボックスを作成する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、Windows オペレーティングシステムの **[実行]** ダイアログボックスなどのダイアログボックスを作成します。  
  
 この例では<xref:System.Windows.Controls.Grid> 、を作成<xref:System.Windows.Controls.ColumnDefinition>し<xref:System.Windows.Controls.RowDefinition> 、クラスとクラスを使用して、5つの列と4つの行を定義します。  
  
 次に、この例では<xref:System.Windows.Controls.Image>、 `RunIcon.png`ダイアログボックスに表示されるイメージを表す、、を追加して配置します。 イメージは、 <xref:System.Windows.Controls.Grid>の最初の列と行 (左上隅) に配置されます。  
  
 次に、最初の行<xref:System.Windows.Controls.TextBlock>の残りの列にまたがる要素を最初の列に追加します。 最初の列<xref:System.Windows.Controls.TextBlock>の2行目に、**開い**ているテキストボックスを表す別の要素が追加されます。 データ入力領域を表すを次に示します。<xref:System.Windows.Controls.TextBlock>  
  
 最後に、最後の行<xref:System.Windows.Controls.Button>に3つの要素を追加します。これは**OK**、 **Cancel**、および**Browse**イベントを表します。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [パネルの概要](panels-overview.md)
- [方法トピック](grid-how-to-topics.md)
