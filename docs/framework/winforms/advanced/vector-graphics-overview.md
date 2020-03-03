---
title: ベクター グラフィックスの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: 64bec47a186b08298a49c6f188795d1b51d234eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505242"
---
# <a name="vector-graphics-overview"></a>ベクター グラフィックスの概要
GDI +、座標系の線、四角形、およびその他の図形を描画します。 さまざまな座標系から選択できますが、既定の座標系では、左上隅の原点が、x 軸が右と下向きの y 軸を参照します。 既定の座標系内のメジャーの単位は、ピクセルです。  
  
## <a name="the-building-blocks-of-gdi"></a>GDI + の構成要素  
 ![ベクター グラフィックス](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 コンピューター モニターでは、図の要素 (ピクセル) と呼ばれる点の四角形の配列での表示を作成します。 1 つのモニターの画面に表示されるピクセルの数が異なり、ユーザーが、個々 のモニターに表示されるピクセルの数をある程度の構成することができます通常します。  
  
 ![ベクター グラフィックス](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 を使用する GDI + 線、四角形、または曲線を描画するときに、描画される項目に関する特定のキー情報を提供します。 たとえば、2 つのポイントを提供することで、行を指定することができ、ポイントを高さ、幅を提供し、四角形を指定することができます。 GDI + ディスプレイ ドライバー ソフトウェアは、線、四角形、または曲線の表示にするピクセルをオンにするかを判断すると連携して動作します。 次の図は、点 (12, 8) (4, 2) のポイントから行を表示するのになっている (ピクセル) を示します。  
  
 ![ベクター グラフィックス](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 時間の経過と共に一部の基本的な構成要素が最も便利な 2 次元の画像を作成するために実績のあります。 GDI + ですべてサポートされていますが、これらのビルディング ブロックは、次の一覧で与えられます。  
  
- 線  
  
- 四角形  
  
- 省略記号  
  
- 円弧  
  
- 多角形  
  
- カーディナル スプライン  
  
- ベジエ スプライン  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>グラフィックス オブジェクトを使用した描画メソッド  
 <xref:System.Drawing.Graphics> GDI + でクラスには前の一覧に項目を描画するための次のメソッド: <xref:System.Drawing.Graphics.DrawLine%2A>、 <xref:System.Drawing.Graphics.DrawRectangle%2A>、 <xref:System.Drawing.Graphics.DrawEllipse%2A>、 <xref:System.Drawing.Graphics.DrawPolygon%2A>、 <xref:System.Drawing.Graphics.DrawArc%2A>、 <xref:System.Drawing.Graphics.DrawCurve%2A> (のカーディナル スプライン)、および<xref:System.Drawing.Graphics.DrawBezier%2A>. これらの各メソッドはオーバー ロードされます。つまり、各メソッドは、さまざまなパラメーター リストをサポートします。 例では、1 つのバリエーション、<xref:System.Drawing.Graphics.DrawLine%2A>メソッドは受信、<xref:System.Drawing.Pen>オブジェクトと別のバリエーションの中に、4 つの整数、<xref:System.Drawing.Graphics.DrawLine%2A>メソッドは受信、<xref:System.Drawing.Pen>オブジェクトと 2 つ<xref:System.Drawing.Point>オブジェクト。  
  
 線、四角形、およびベジエ スプラインを描画するためのメソッドがある 1 回の呼び出しで複数の項目を描画する複数形のコンパニオン メソッド: <xref:System.Drawing.Graphics.DrawLines%2A>、 <xref:System.Drawing.Graphics.DrawRectangles%2A>、および<xref:System.Drawing.Graphics.DrawBeziers%2A>します。 また、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッドには、コンパニオン メソッド<xref:System.Drawing.Graphics.DrawClosedCurve%2A>終了、開始する曲線の終了点を接続することで曲線をポイントします。  
  
 すべての描画メソッドの<xref:System.Drawing.Graphics>クラスと連携して動作を<xref:System.Drawing.Pen>オブジェクト。 を何も描画するには、少なくとも 2 つのオブジェクトを作成する必要があります:、<xref:System.Drawing.Graphics>オブジェクトと<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Pen>オブジェクトが描画される項目の色、線の幅などの属性を格納します。 <xref:System.Drawing.Pen>オブジェクトが引数の 1 つとして描画メソッドに渡されます。 例では、1 つのバリエーション、<xref:System.Drawing.Graphics.DrawLine%2A>メソッドは受信、<xref:System.Drawing.Pen>オブジェクトと、幅が 100、高さを 50 との左上隅を四角形を描画する次の例で示すように 4 つの整数 (20, 10)。  
  
 [!code-csharp[LinesCurvesAndShapes#11](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [方法: 描画の Graphics オブジェクトを作成します。](how-to-create-graphics-objects-for-drawing.md)
