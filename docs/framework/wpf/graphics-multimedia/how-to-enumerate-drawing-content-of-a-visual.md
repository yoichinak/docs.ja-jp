---
title: '方法: ビジュアルの描画コンテンツを列挙する'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 6414026090766544585c8e5e940ef9f0c62566d2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360015"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>方法: ビジュアルの描画コンテンツを列挙する
<xref:System.Windows.Media.Drawing>オブジェクトの内容を列挙するためのオブジェクト モデルの提供、<xref:System.Windows.Media.Visual>します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>を取得するメソッド、<xref:System.Windows.Media.DrawingGroup>の値を<xref:System.Windows.Media.Visual>し、それを列挙します。  
  
> [!NOTE]
>  ビジュアルの内容を列挙するときは、取得する<xref:System.Windows.Media.Drawing>オブジェクト、およびしない、ベクター グラフィックス命令リストとしてのレンダリング データの基になる表現。 詳しくは、「[WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)」をご覧ください。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
