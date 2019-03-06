---
title: '方法: 2 次ベジエ曲線を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: 8adb5d0348fe53cecbdabf8ffa3b244fe34831e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363723"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>方法: 2 次ベジエ曲線を作成する
この例では、2 次ベジエ曲線を作成する方法を示します。  2 次ベジエ曲線を作成するには、使用、 <xref:System.Windows.Media.PathGeometry>、 <xref:System.Windows.Media.PathFigure>、および<xref:System.Windows.Media.QuadraticBezierSegment>クラス。  
  
## <a name="example"></a>例  
 次の例では、2 次ベジエ曲線は (300, 100) に (10,100) から描画されます。 曲線は (200, 200) の制御点。  
  
 [xaml]  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、属性構文を使用してパスを記述することができます。  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 [xaml]  
  
 (この属性の構文が実際に作成するメモを<xref:System.Windows.Media.StreamGeometry>の軽量バージョンを<xref:System.Windows.Media.PathGeometry>します。 詳細については、「[パス マークアップ構文](path-markup-syntax.md)」のページを参照してください。)  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、オブジェクト要素構文を使用して、2 次ベジエ曲線を描画することもできます。 次の例は、前の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例と同じです。  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](https://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- [楕円の円弧を作成する](how-to-create-an-elliptical-arc.md)
- [3 次ベジエ曲線を作成する](how-to-create-a-cubic-bezier-curve.md)
