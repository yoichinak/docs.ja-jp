---
title: '方法 : ジオメトリック パスを使用してオブジェクトを回転させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186876"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>方法 : ジオメトリック パスを使用してオブジェクトを回転させる
この例では、オブジェクトによって定義されたジオメトリパスに沿ってオブジェクトを回転 (ピボット)<xref:System.Windows.Media.PathGeometry>する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、3 つの<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>オブジェクトを使用して、四角形をジオメトリパスに沿って移動します。  
  
- 最初<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>のアニメーション<xref:System.Windows.Media.RotateTransform>は、四角形に適用されます。 アニメーションは、角度の値を生成します。 これにより、四角形がパスの輪郭に沿って回転 (ピボット) します。  
  
- 他の 2 つのオブジェクトは<xref:System.Windows.Media.TranslateTransform.X%2A>、<xref:System.Windows.Media.TranslateTransform.Y%2A>四角形に<xref:System.Windows.Media.TranslateTransform>適用される の と の値をアニメーション化します。 これにより、四角形が、パスに沿って水平方向と垂直方向に移動します。  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 ジオメトリパスを使用してオブジェクトを回転するもう 1 つの方法<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>は、オブジェクトを<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>使用して`true`そのプロパティを に設定することです。 詳細と例については、「[ジオメトリック パスを使用してオブジェクトを回転する (行列アニメーション)」](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)を参照してください。  
  
 完全なサンプルについては、「[パス アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [パス アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [パス アニメーションに関する「方法」トピック](path-animation-how-to-topics.md)
