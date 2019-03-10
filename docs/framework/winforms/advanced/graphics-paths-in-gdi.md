---
title: GDI+ でのグラフィックス パス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: b6f0ebd500aa3503c0c0d473ebe21a61f4438862
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720424"
---
# <a name="graphics-paths-in-gdi"></a>GDI+ でのグラフィックス パス
パスは、線、四角形、および単純な曲線を組み合わせることで形成されます。 メッセージの取り消し、[ベクター グラフィックスの概要](vector-graphics-overview.md)基本ビルディング ブロックを次に図を描画するために最も便利なことがわかっています。  
  
-   線  
  
-   四角形  
  
-   省略記号  
  
-   円弧  
  
-   多角形  
  
-   カーディナル スプライン  
  
-   ベジエ スプライン  
  
 GDI + で、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトでは、これらの構成要素のシーケンスを 1 つの単位に収集できます。 1 回の呼び出しで線、四角形、多角形、および曲線のシーケンス全体を描画することができますし、<xref:System.Drawing.Graphics.DrawPath%2A>のメソッド、<xref:System.Drawing.Graphics>クラス。 次の図には、行、円弧、本のベジエ スプライン、カーディナル スプラインを組み合わせることにより作成されたパスが表示されます。  
  
 ![パス](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>パスを使用します。  
 <xref:System.Drawing.Drawing2D.GraphicsPath>クラスが描画される項目のシーケンスを作成するために、次のメソッドを提供します: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (のカーディナル スプライン)、および<xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>します。 これらの各メソッドはオーバー ロードされます。つまり、各メソッドは、さまざまなパラメーター リストをサポートします。 例では、1 つのバリエーション、<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>メソッドは、4 つの整数と別のバリエーションを受け取る、<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>メソッドが受け取る 2 つ<xref:System.Drawing.Point>オブジェクト。  
  
 線、四角形、およびベジエ スプラインをパスに追加するためのメソッドを 1 つの呼び出しパスに複数の項目を追加する複数形のコンパニオン メソッドがある: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>、および<xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>します。 また、<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>と<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>メソッド コンパニオンのメソッドがある<xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A>と<xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>パスに閉じた曲線または円を追加します。  
  
 パスを描画するためにする必要があります、<xref:System.Drawing.Graphics>オブジェクト、<xref:System.Drawing.Pen>オブジェクト、および<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトを提供、<xref:System.Drawing.Graphics.DrawPath%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、パスを表示するために使用する線の色、幅などの属性を格納します。 <xref:System.Drawing.Drawing2D.GraphicsPath>の直線と曲線のパスを構成するシーケンスを格納するオブジェクト。 <xref:System.Drawing.Pen>オブジェクトと<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトが引数として渡される、<xref:System.Drawing.Graphics.DrawPath%2A>メソッド。 次の例では、パスは、行、楕円、および本のベジエ スプラインを描画します。  
  
 [!code-csharp[LinesCurvesAndShapes#101](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 次の図には、パスが表示されます。  
  
 ![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 パスに線、四角形、および曲線を追加するだけでは、パスにパスを追加できます。 これにより、大規模で複雑なパスを形成する既存のパスを結合することができます。  
  
 [!code-csharp[LinesCurvesAndShapes#102](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 パスに追加できるその他の 2 つの項目がある: 文字列と円グラフ。 円、楕円の内部の一部です。 次の例では、円弧、カーディナル スプライン、文字列、および円からパスを作成します。  
  
 [!code-csharp[LinesCurvesAndShapes#103](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 次の図には、パスが表示されます。 パスに接続されている; がないことに注意してください。円弧をカーディナル スプラインを文字列、および円グラフは区切られます。  
  
 ![パス](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [方法: 描画の Graphics オブジェクトを作成します。](how-to-create-graphics-objects-for-drawing.md)
- [パスの作成および描画](constructing-and-drawing-paths.md)
