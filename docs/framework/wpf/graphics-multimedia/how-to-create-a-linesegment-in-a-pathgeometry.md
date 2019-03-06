---
title: '方法: PathGeometry で LineSegment を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: a6862ab02c288f9cfd1fac4a8c22079b0cf91016
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356183"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a>方法: PathGeometry で LineSegment を作成する
この例では、線分を作成する方法を示します。 直線セグメントを作成するには、使用、 <xref:System.Windows.Media.PathGeometry>、 <xref:System.Windows.Media.PathFigure>、および<xref:System.Windows.Media.LineSegment>クラス。  
  
## <a name="example"></a>例  
 次の例では、描画、<xref:System.Windows.Media.LineSegment>から (10, 50) を (200, 70)。 次の図は、その結果<xref:System.Windows.Media.LineSegment>; 座標系を表示するグリッドの背景色が追加されました。  
  
 ![PathFigure 内の LineSegment](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment")  
(10,50) から (200,70) まで描画された LineSegment  
  
 [xaml]  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、属性構文を使用してパスを記述できます。  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1"    
  Data="M 10,50 L 200,70" />  
```  
  
 [xaml]  
  
 (この属性の構文が実際に作成するメモを<xref:System.Windows.Media.StreamGeometry>の軽量バージョンを<xref:System.Windows.Media.PathGeometry>します。 詳細については、「[パス マークアップ構文](path-markup-syntax.md)」のページを参照してください。)  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、オブジェクト要素構文を使用して線分を描画することもできます。 次の例は、前の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例と同じです。  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1">  
  <Path.Data>  
    <PathGeometry>  
      <PathFigure StartPoint="10,50">  
        <LineSegment Point="200,70" />  
      </PathFigure>  
    </PathGeometry>  
  </Path.Data>  
</Path>  
```  
  
```csharp  
PathFigure myPathFigure = new PathFigure();  
myPathFigure.StartPoint = new Point(10, 50);  
  
LineSegment myLineSegment = new LineSegment();  
myLineSegment.Point = new Point(200, 70);  
  
PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();  
myPathSegmentCollection.Add(myLineSegment);  
  
myPathFigure.Segments = myPathSegmentCollection;  
  
PathFigureCollection myPathFigureCollection = new PathFigureCollection();  
myPathFigureCollection.Add(myPathFigure);  
  
PathGeometry myPathGeometry = new PathGeometry();  
myPathGeometry.Figures = myPathFigureCollection;  
  
Path myPath = new Path();  
myPath.Stroke = Brushes.Black;  
myPath.StrokeThickness = 1;  
myPath.Data = myPathGeometry;  
```  
  
```vb  
Dim myPathFigure As New PathFigure()  
            myPathFigure.StartPoint = New Point(10, 50)  
  
            Dim myLineSegment As New LineSegment()  
            myLineSegment.Point = New Point(200, 70)  
  
            Dim myPathSegmentCollection As New PathSegmentCollection()  
            myPathSegmentCollection.Add(myLineSegment)  
  
            myPathFigure.Segments = myPathSegmentCollection  
  
            Dim myPathFigureCollection As New PathFigureCollection()  
            myPathFigureCollection.Add(myPathFigure)  
  
            Dim myPathGeometry As New PathGeometry()  
            myPathGeometry.Figures = myPathFigureCollection  
  
            Dim myPath As New Path()  
            myPath.Stroke = Brushes.Black  
            myPath.StrokeThickness = 1  
            myPath.Data = myPathGeometry  
```  
  
 この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](https://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [ジオメトリの概要](geometry-overview.md)
