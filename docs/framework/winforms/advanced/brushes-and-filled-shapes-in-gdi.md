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
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912229"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+ でのブラシと塗りつぶされた図形
四角形や楕円などの閉じた図形は、アウトラインと内部で構成されます。 輪郭がペンで描画され、内部にブラシが挿入されます。 Gdi + <xref:System.Drawing.SolidBrush>には<xref:System.Drawing.Drawing2D.HatchBrush> <xref:System.Drawing.Drawing2D.PathGradientBrush>、 <xref:System.Drawing.TextureBrush>閉じられた図形の内部を埋めるために、、、、、およびのブラシクラスがいくつ<xref:System.Drawing.Drawing2D.LinearGradientBrush>か用意されています。 これらのクラスはすべて、 <xref:System.Drawing.Brush>クラスから継承されます。 次の図は、単色ブラシで塗りつぶされた四角形と、ハッチブラシで塗りつぶされた楕円を示しています。  
  
 ![塗りつぶさ]れた図形(./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>ソリッドブラシ  
 閉じた図形を塗りつぶすには、 <xref:System.Drawing.Graphics>クラスのインスタンス<xref:System.Drawing.Brush>とが必要です。 <xref:System.Drawing.Graphics>クラスのインスタンスは、 <xref:System.Drawing.Graphics.FillRectangle%2A>や<xref:System.Drawing.Graphics.FillEllipse%2A>などのメソッドを提供し<xref:System.Drawing.Brush> 、色やパターンなどの塗りつぶしの属性を格納します。 は、引数の1つとして fill メソッドに渡されます。<xref:System.Drawing.Brush> 次のコード例では、楕円に純色を赤で塗りつぶす方法を示します。  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> 前の例では、ブラシは型<xref:System.Drawing.SolidBrush>であり、から<xref:System.Drawing.Brush>継承されます。  
  
## <a name="hatch-brushes"></a>ハッチブラシ  
 ハッチブラシを使用して図形を塗りつぶす場合は、前景色、背景色、およびハッチスタイルを指定します。 前景色は陰影の色です。  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 GDI + は、50を超えるハッチスタイルを提供します。次の図<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal> <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>に示す3つのスタイルは、、 <xref:System.Drawing.Drawing2D.HatchStyle.Cross>、およびです。  
  
 ![塗りつぶさ]れた図形(./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>テクスチャブラシ  
 テクスチャブラシを使用すると、ビットマップに格納されているパターンで図形を塗りつぶすことができます。 たとえば、次の画像がという名前`MyTexture.bmp`のディスクファイルに格納されているとします。  
  
 ![塗りつぶさ]れた図形(./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 次のコード例では、に`MyTexture.bmp`格納されている画像を繰り返して楕円に入力する方法を示します。  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 次の図は、塗りつぶされた楕円を示しています。  
  
 ![塗りつぶさ]れた図形(./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>グラデーションブラシ  
 GDI + には、線形とパスという2種類のグラデーションブラシが用意されています。 線状グラデーションブラシを使用すると、図形を水平方向、垂直方向、または対角線方向に移動するときに徐々に変化する色で図形を塗りつぶすことができます。 次のコード例は、楕円の左端から右端に移動したときに青から緑に変化する水平グラデーションブラシを使用して楕円に塗りつぶす方法を示しています。  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 次の図は、塗りつぶされた楕円を示しています。  
  
 ![塗りつぶさ]れた図形(./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 パスグラデーションブラシは、図形の中心から端に向かって移動するときに色を変更するように構成できます。  
  
 ![塗りつぶさ]れた図形(./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 パスグラデーションブラシは非常に柔軟です。 次の図の三角形の塗りつぶしに使用されるグラデーションブラシは、中央の赤から頂点の3つの異なる色のそれぞれに徐々に変化します。  
  
 ![塗りつぶさ]れた図形(./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [方法: Windows フォームで塗りつぶされた四角形を描画する](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [方法: Windows フォームで塗りつぶされた楕円を描画する](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
