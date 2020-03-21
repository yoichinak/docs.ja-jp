---
title: '方法 : ToolTip を配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186950"
---
# <a name="how-to-position-a-tooltip"></a>方法 : ToolTip を配置する
この例では、画面上のツールヒントの位置を指定する方法を示します。  
  
## <a name="example"></a>例  
 ツールヒントは、 クラスと<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.ToolTipService>クラスの両方で定義された 5 つのプロパティのセットを使用して配置できます。 次の表は、これら 2 つの 5 つのプロパティ セットを示し、クラスに従って参照ドキュメントへのリンクを示しています。  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>クラスに応じた対応するツールヒントプロパティ  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>クラスプロパティ|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>クラスプロパティ|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 オブジェクトを使用してツールヒントの内容を<xref:System.Windows.Controls.ToolTip>定義する場合は、どちらのクラスのプロパティを使用しても問題ありません。ただし、プロパティ<xref:System.Windows.Controls.ToolTipService>が優先されます。 オブジェクトとして<xref:System.Windows.Controls.ToolTipService><xref:System.Windows.Controls.ToolTip>定義されていないツールチップのプロパティを使用します。  
  
 次の図は、これらのプロパティを使用してツールヒントを配置する方法を示しています。 ただし、これらの[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]図の例では、クラスによって定義されるプロパティを設定する方法を<xref:System.Windows.Controls.ToolTip>示していますが、<xref:System.Windows.Controls.ToolTipService>クラスの対応するプロパティは同じレイアウト規則に従います。 [配置] プロパティで使用できる値の詳細については、「[ポップアップ配置の動作](popup-placement-behavior.md)」を参照してください。  

 次の図は、Placement プロパティを使用したツールヒントの配置を示しています。  
  
 ![配置プロパティを使用してツールヒントの配置を示す図。](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 次の図は、配置および配置矩形プロパティを使用して、ツールヒントの配置を示しています。

 ![配置四角形プロパティを使用してツールヒントの配置を示す図。](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 次の図は、[配置]、[配置]、および [オフセット] プロパティを使用したツールヒントの配置を示しています。
  
 ![Offset プロパティを使用したツールヒントの配置を示す図。](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 <xref:System.Windows.Controls.ToolTip>プロパティを使用して、コンテンツがオブジェクトであるツールヒントの位置を指定する方法を次の<xref:System.Windows.Controls.ToolTip>例に示します。  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 プロパティを使用<xref:System.Windows.Controls.ToolTipService>して、コンテンツがオブジェクトではないツールヒントの位置を指定する方法を次の例<xref:System.Windows.Controls.ToolTip>に示します。  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [ハウツートピック](tooltip-how-to-topics.md)
- [ToolTip の概要](tooltip-overview.md)
