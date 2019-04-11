---
title: Graphics オブジェクトの状態の管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: 8fc92bf84def50bed54a054ae634a8a08c8835c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212454"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Graphics オブジェクトの状態の管理
<xref:System.Drawing.Graphics>クラスは、の中核[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]します。 取得するものを描画する、<xref:System.Drawing.Graphics>オブジェクトでそのプロパティを設定し、そのメソッドを呼び出す<xref:System.Drawing.Graphics.DrawLine%2A>、 <xref:System.Drawing.Graphics.DrawImage%2A>、<xref:System.Drawing.Graphics.DrawString%2A>など)。  
  
 次の例では、<xref:System.Drawing.Graphics.DrawRectangle%2A>のメソッドを<xref:System.Drawing.Graphics>オブジェクト。 渡される最初の引数、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッドは、<xref:System.Drawing.Pen>オブジェクト。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a>グラフィックスの状態  
 A<xref:System.Drawing.Graphics>オブジェクトによる描画メソッドは、の提供がなど複数の<xref:System.Drawing.Graphics.DrawLine%2A>と<xref:System.Drawing.Graphics.DrawRectangle%2A>します。 A<xref:System.Drawing.Graphics>オブジェクトでは、グラフィックスの状態は、次のカテゴリに分類できますも保持されます。  
  
-   品質の設定  
  
-   変換  
  
-   クリッピング領域  
  
### <a name="quality-settings"></a>品質の設定  
 A<xref:System.Drawing.Graphics>オブジェクトが描画されるアイテムの品質に影響を与えるいくつかのプロパティ。 たとえば、設定、<xref:System.Drawing.Graphics.TextRenderingHint%2A>プロパティをテキストに適用されます (ある場合) のアンチエイリアシングの種類を指定します。 品質に影響を与える他のプロパティは<xref:System.Drawing.Graphics.SmoothingMode%2A>、 <xref:System.Drawing.Graphics.CompositingMode%2A>、 <xref:System.Drawing.Graphics.CompositingQuality%2A>、および<xref:System.Drawing.Graphics.InterpolationMode%2A>します。  
  
 次の例は、スムージング モードを設定する 2 つの楕円を描画<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>、平滑化のモードを設定するもう 1 つ<xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a>変換  
 A<xref:System.Drawing.Graphics>オブジェクトをで描画されるすべての項目に適用される 2 つの変換 (世界と ページ) を保持する<xref:System.Drawing.Graphics>オブジェクト。 ワールド変換では、任意のアフィン変換を格納できます。 アフィン変換には、拡大縮小、回転、反転、傾斜、および変換が含まれます。 スケーリングの単位 (たとえば、インチをピクセル単位) を変更して、ページの変換を使用できます。 詳細については、次を参照してください。[座標系と変換](coordinate-systems-and-transformations.md)します。  
  
 次の例の世界とページの変換の設定、<xref:System.Drawing.Graphics>オブジェクト。 ワールド変換は、30 度回転に設定されます。 ページの変換を設定すると、2 番目の座標が渡されるように<xref:System.Drawing.Graphics.DrawEllipse%2A>ピクセルではなくミリメートル単位として扱われます。 コードは、同じ 2 つの呼び出し、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッド。 ワールド変換は、最初に適用される<xref:System.Drawing.Graphics.DrawEllipse%2A>、2 つ目に呼び出し、および (世界と ページ) の両方の変換が適用<xref:System.Drawing.Graphics.DrawEllipse%2A>呼び出します。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 次の図は、2 つの省略記号を示します。 30 度の回転は (クライアント領域の左上隅) 座標系の原点を基点、楕円の中心でないことに注意してください。 1 のペンの幅が 2 番目の楕円の 1 ピクセルの最初の楕円および 1 ミリメートルを意味することに注意してください。  
  
 ![2 つの楕円を図解: 回転とペンの幅。](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>クリッピング領域  
 A<xref:System.Drawing.Graphics>オブジェクトをで描画されるすべての項目に適用されるクリッピング領域を保持する<xref:System.Drawing.Graphics>オブジェクト。 クリッピング領域を設定するには、呼び出すことによって、<xref:System.Drawing.Graphics.SetClip%2A>メソッド。  
  
 次の例では、2 つの四角形の和集合を形成して十字型の領域を作成します。 クリッピング領域としてそのリージョンが指定されている、<xref:System.Drawing.Graphics>オブジェクト。 コードは、クリッピング領域の内部に制限されている 2 つの行を描画します。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 次の図は、クリップされた行を示しています。  
  
 ![制限されたクリップ領域を示す図。](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>関連項目

- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [入れ子になっているグラフィックス コンテナーの使用](using-nested-graphics-containers.md)
