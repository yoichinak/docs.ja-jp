---
title: GDI+ でのブラシと塗りつぶされた図形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 683b5966f993ac3a69c8bf7c1233b6df3d65e19a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115311"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+ でのブラシと塗りつぶされた図形
四角形や楕円など、閉じた形状は、概要を説明し、内部で構成されます。 アウトラインの描画に使用するペンとブラシを使用して、内部が塗りつぶされます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 閉じた図形の内側を塗りつぶすときのいくつかのブラシのクラスを提供します。 <xref:System.Drawing.SolidBrush>、 <xref:System.Drawing.Drawing2D.HatchBrush>、 <xref:System.Drawing.TextureBrush>、 <xref:System.Drawing.Drawing2D.LinearGradientBrush>、および<xref:System.Drawing.Drawing2D.PathGradientBrush>します。 継承するすべてのクラス、<xref:System.Drawing.Brush>クラス。 次の図は、ソリッド ブラシで塗りつぶした四角形に見えるハッチ ブラシで塗りつぶした楕円を示しています。  
  
 ![塗りつぶされた図形](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>単色ブラシ  
 閉じた図形を塗りつぶすには、インスタンスの必要があります、<xref:System.Drawing.Graphics>クラスと<xref:System.Drawing.Brush>します。 インスタンス、<xref:System.Drawing.Graphics>クラスには、メソッドなど<xref:System.Drawing.Graphics.FillRectangle%2A>と<xref:System.Drawing.Graphics.FillEllipse%2A>、および<xref:System.Drawing.Brush>塗りつぶし、色やパターンなどの属性を格納します。 <xref:System.Drawing.Brush> Fill メソッドを引数として渡されます。 次のコード例では、純色の赤で楕円を塗りつぶす方法を示します。  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  前の例では、ブラシは、型の<xref:System.Drawing.SolidBrush>から継承される<xref:System.Drawing.Brush>します。  
  
## <a name="hatch-brushes"></a>ハッチ ブラシ  
 ハッチ ブラシを使用して図形を塗りつぶすときに、前景色、背景色、および陰影のスタイルを指定します。 前景の色はの陰影の色です。  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 50 を超えるハッチ スタイルを提供します。次の図に示すように 3 つのスタイルが<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>、 <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>、および<xref:System.Drawing.Drawing2D.HatchStyle.Cross>します。  
  
 ![塗りつぶされた図形](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>テクスチャ ブラシ  
 テクスチャ ブラシでは、ビットマップに格納されているパターンで図形を塗りつぶすことができます。 たとえば、次の図がという名前のディスク ファイルに格納されている`MyTexture.bmp`します。  
  
 ![図形を塗り分け](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 次のコード例に格納されている画像を繰り返すことによって楕円の塗りつぶし方法を示しています。`MyTexture.bmp`します。  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 次の図は、塗りつぶされた楕円を示します。  
  
 ![図形を塗り分け](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>グラデーション ブラシ  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] グラデーション ブラシの 2 種類があります。 線形とパス。 線状グラデーション ブラシを使用して、縦、横、図形の間で移動すると、段階的にまたは斜めに変更を色で図形を塗りつぶすことができます。 次のコード例では、楕円の左端から右端に移動すると、青から緑に変更する水平方向のグラデーション ブラシで楕円を塗りつぶす方法を示します。  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 次の図は、塗りつぶされた楕円を示します。  
  
 ![図形を塗り分け](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 端に図形の中心から移動すると、色を変更するのには、パスのグラデーション ブラシを構成できます。  
  
 ![図形を塗り分け](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 パス グラデーション ブラシはとても柔軟です。 次の図の変更が中央の赤から段階的に各頂点で 3 つの異なる色に三角形の塗りつぶしに使用するグラデーションのブラシ。  
  
 ![図形を塗り分け](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [方法: Windows フォームに塗りつぶした四角形を描画します。](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [方法: Windows フォームに塗りつぶした楕円を描画します。](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
