---
title: GDI+ でのペン、直線、および四角形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 84752773c0b56d9684dc31620d463d4ddccf9dad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641392"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>GDI+ でのペン、直線、および四角形
使用して線を描画するために[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]を作成する必要がある、<xref:System.Drawing.Graphics>オブジェクトと<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトが実際には、描画を実行するメソッドを提供し、<xref:System.Drawing.Pen>オブジェクトが線の色、幅、およびスタイルなどの属性を格納します。  
  
## <a name="drawing-a-line"></a>直線を描画します。  
 線を描画するために呼び出す、<xref:System.Drawing.Graphics.DrawLine%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。 <xref:System.Drawing.Pen>オブジェクトが渡される引数の 1 つとして、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド。 次の例は、点 (12, 6) (4, 2) のポイントから線を描画します。  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> オーバー ロードされたメソッド、<xref:System.Drawing.Graphics>クラスの引数を指定することがいくつかの方法があるようにします。 2 つの構築など<xref:System.Drawing.Point>オブジェクトとパス、<xref:System.Drawing.Point>オブジェクトへの引数として、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド。  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>ペンを作成  
 特定の属性を指定するには、構築するときに、<xref:System.Drawing.Pen>オブジェクト。 たとえば、1 つ`Pen`コンス トラクターでは、色と幅を指定できます。 次の例では、幅が 2 から青い線を描画します (0, 0) に (60, 30)。  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>破線とライン キャップ  
 <xref:System.Drawing.Pen>オブジェクトのプロパティをなど、公開も<xref:System.Drawing.Pen.DashStyle%2A>行の機能の指定を行えます。 次の例から破線を描画します (100, 50) に (300, 80)。  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 プロパティを使用することができます、<xref:System.Drawing.Pen>行の多くの属性を設定するオブジェクト。 <xref:System.Drawing.Pen.StartCap%2A>と<xref:System.Drawing.Pen.EndCap%2A>プロパティは、線の端の外観を指定。 end は、フラット、正方形、丸められた、三角形、またはカスタムの形状。 <xref:System.Drawing.Pen.LineJoin%2A>プロパティかどうか接続されている行はマイター (鋭い角の結合)、傾斜、丸め、またはクリップを指定できます。 次の図は、さまざまな上限と結合スタイルを使用して行を示します。  
  
 ![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>四角形の描画  
 四角形を描画[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]線を描画に似ています。 四角形を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクトと<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトを提供、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトが線の幅と色などの属性を格納します。 <xref:System.Drawing.Pen>オブジェクトが渡される引数の 1 つとして、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッド。 次の例で、左上隅を四角形を描画します (100, 50)、80、幅と高さ 40。  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> オーバー ロードされたメソッド、<xref:System.Drawing.Graphics>クラスの引数を指定することがいくつかの方法があるようにします。 たとえば、構築、<xref:System.Drawing.Rectangle>オブジェクトを渡します、<xref:System.Drawing.Rectangle>オブジェクトを<xref:System.Drawing.Graphics.DrawRectangle%2A>を引数としてメソッド。  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A<xref:System.Drawing.Rectangle>オブジェクトがメソッドとプロパティを操作すると、四角形に関する情報を収集します。 たとえば、<xref:System.Drawing.Rectangle.Inflate%2A>と<xref:System.Drawing.Rectangle.Offset%2A>メソッドは、四角形の位置とサイズを変更します。 <xref:System.Drawing.Rectangle.IntersectsWith%2A>メソッドに指示するかどうか、四角形と交差する別の四角形を指定し、<xref:System.Drawing.Rectangle.Contains%2A>メソッドは、指定された点が四角形の内側がかどうかを示します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [方法: ペンを作成します。](how-to-create-a-pen.md)
- [方法: Windows フォームに直線を描画します。](how-to-draw-a-line-on-a-windows-form.md)
- [方法: 形状のアウトラインを描画します。](how-to-draw-an-outlined-shape.md)
