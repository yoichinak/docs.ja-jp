---
title: '方法: パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: 4ef28118975d02500916676ca50e0f9622c7a3e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129591"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>方法: パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション)
この例は、使用する方法を示します、<xref:System.Windows.Media.Animation.PointAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Point>曲線のパスに沿ってします。  
  
## <a name="example"></a>例  
 次の例では、移動、<xref:System.Windows.Media.EllipseGeometry>によって定義されたパスに沿って、<xref:System.Windows.Media.PathGeometry>します。 楕円ジオメトリの<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティを<xref:System.Windows.Point>値をアニメーション化する、楕円ジオメトリを移動する位置を指定します、<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティ。 この例では、<xref:System.Windows.Media.Animation.PointAnimationUsingPath>をアニメーション化する、<xref:System.Windows.Media.EllipseGeometry>オブジェクトの<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティ。  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 サンプル全体については、次を参照してください。[パス アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160028)します。  
  
 使用前の例のコードのバージョン、<xref:System.Windows.Media.Animation.Storyboard>をアニメーション化する、 <xref:System.Windows.Media.EllipseGeometry>1 つだけのアニメーションが適用された場合でも、します。 A<xref:System.Windows.Media.Animation.Storyboard>同じこれらのアニメーションを制御できるため、複数のアニメーションを適用する最も簡単な方法は、多くの場合、<xref:System.Windows.Media.Animation.Storyboard>します。 しかし、コードを使用する場合は、1 つのアニメーションをプロパティに適用する簡単な方法は、使用する、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッド。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [パス アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160028)
- [アニメーションの概要](animation-overview.md)
- [パス アニメーションに関する「方法」トピック](path-animation-how-to-topics.md)
