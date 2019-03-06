---
title: '方法: 楕円の円弧を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: bb4b4d99aab9daef70f446af176bb462b0661d54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354350"
---
# <a name="how-to-create-an-elliptical-arc"></a>方法: 楕円の円弧を作成する
この例では、楕円の円弧を描画する方法を示します。楕円の円弧を作成するには、使用、 <xref:System.Windows.Media.PathGeometry>、 <xref:System.Windows.Media.PathFigure>、および<xref:System.Windows.Media.ArcSegment>クラス。  
  
## <a name="example"></a>例  
 次の例では、楕円の円弧は (200, 100) に (10,100) から描画されます。 円弧が、 <xref:System.Windows.Media.ArcSegment.Size%2A> 50 で 100 デバイス非依存のピクセルの<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>、45 度の<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>の設定`true`、および<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>の<xref:System.Windows.Media.SweepDirection.Counterclockwise>。  
  
 [xaml]  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、属性構文を使用してパスを記述することができます。  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 (この属性の構文が実際に作成するメモを<xref:System.Windows.Media.StreamGeometry>の軽量バージョンを<xref:System.Windows.Media.PathGeometry>します。 詳細については、「[パス マークアップ構文](path-markup-syntax.md)」のページを参照してください。)  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、明示的にオブジェクトのタグを使用して、楕円の円弧を描画することもできます。 次に、上記に相当[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 この例は、さらに大きなサンプルの一部です。 サンプル全体については、次を参照してください。、[ジオメトリのサンプル](https://go.microsoft.com/fwlink/?LinkID=159989)します。  
  
## <a name="see-also"></a>関連項目
- [2 次ベジエ曲線を作成する](how-to-create-a-quadratic-bezier-curve.md)
- [3 次ベジエ曲線を作成する](how-to-create-a-cubic-bezier-curve.md)
