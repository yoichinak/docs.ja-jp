---
title: '方法: パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 1838b2492e7ea8a33139fdb5682362998d84a98d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363403"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>方法: パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション)
この例は、使用する方法を示します、<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>クラスによって定義されたパスに沿ってオブジェクトを移動する、<xref:System.Windows.Media.PathGeometry>します。  
  
## <a name="example"></a>例  
 次の例を使用して 2 つ<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>四角形をジオメトリ パスに沿って移動するオブジェクト。  
  
-   最初の<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をアニメーション化、<xref:System.Windows.Media.TranslateTransform.X%2A>の<xref:System.Windows.Media.TranslateTransform>四角形に適用します。 これにより、四角形がパスに沿って水平に移動します。  
  
-   2 番目の<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をアニメーション化、<xref:System.Windows.Media.TranslateTransform.Y%2A>の<xref:System.Windows.Media.TranslateTransform>四角形に適用します。 これにより、四角形がパスに沿って垂直に移動します。  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 サンプル全体については、[パス アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160028)を参照してください。  
  
 ジオメトリック パスを使用してオブジェクトを移動することもできますが、使用する、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>オブジェクト。 例については、[、オブジェクト パスに沿って (行列アニメーション) をアニメーション化する](how-to-animate-an-object-along-a-path-matrix-animation.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [アニメーションの概要](animation-overview.md)
- [パス アニメーションに関する「方法」トピック](path-animation-how-to-topics.md)
