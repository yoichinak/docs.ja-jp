---
title: '方法: 描画に GuidelineSet を適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 88c44cadce916c2ce10165a586e813ecaaaec672
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362995"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>方法: 描画に GuidelineSet を適用する
この例では、適用、<xref:System.Windows.Media.GuidelineSet>を<xref:System.Windows.Media.DrawingGroup>。  
  
 <xref:System.Windows.Media.DrawingGroup>クラスは、唯一の種類の<xref:System.Windows.Media.Drawing>を持つ、<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>プロパティ。 適用する、<xref:System.Windows.Media.GuidelineSet>の別の型に<xref:System.Windows.Media.Drawing>、追加、<xref:System.Windows.Media.DrawingGroup>し、適用、<xref:System.Windows.Media.GuidelineSet>を<xref:System.Windows.Media.DrawingGroup>。  
  
## <a name="example"></a>例  
 次の例では、2 つ作成されます<xref:System.Windows.Media.DrawingGroup>はほとんど同じです。 唯一の違いは、オブジェクト: 2 つ目<xref:System.Windows.Media.DrawingGroup>が、<xref:System.Windows.Media.GuidelineSet>と 1 つ目はありません。  
  
 この例からの出力を次の図に示します。 2 つの間の差。 レンダリングため<xref:System.Windows.Media.DrawingGroup>オブジェクトは、あまり目立たない、図面の特定の部分を拡大します。  
  
 ![GuidelineSet が有効/無効な DrawingGroup](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
