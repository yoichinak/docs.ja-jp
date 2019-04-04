---
title: '方法: パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: c0c4f1fad5ab6b8d30e6809aa866b4629d08af23
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363736"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>方法: パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)
この例は、使用する方法を示します、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>で定義されているパスに沿ってオブジェクトをアニメーション化するクラス、<xref:System.Windows.Media.PathGeometry>します。  
  
## <a name="example"></a>例  
 次の例では、以下の処理を実行し、パスに沿ってオブジェクトをアニメーション化します。  
  
-   適用対象を<xref:System.Windows.Media.MatrixTransform>移動するには、オブジェクトにします。  
  
-   使用してパスを定義、<xref:System.Windows.Media.PathGeometry>します。  
  
-   作成、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>をアニメーション化するために使用して、<xref:System.Windows.Media.Matrix>のプロパティ、<xref:System.Windows.Media.MatrixTransform>します。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>は、<xref:System.Windows.Media.PathGeometry>しを使用して生成<xref:System.Windows.Media.Matrix>値。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 サンプル全体については、[パス アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160028)を参照してください。 ジオメトリック パスの詳細については、、[ジオメトリの概要](geometry-overview.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [アニメーションの概要](animation-overview.md)
- [パス アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160028)
- [パス アニメーションに関する「方法」トピック](path-animation-how-to-topics.md)
