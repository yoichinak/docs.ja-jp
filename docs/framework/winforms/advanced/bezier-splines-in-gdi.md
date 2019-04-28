---
title: B&#233;ベジエ スプラインを GDI + で
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779277"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;ベジエ スプラインを GDI + で
ベジエ スプラインは、4 つのポイントで指定された曲線: 2 つの終点 (p1 および p2) と 2 つの制御点 (c1 と c2)。 曲線が p1 で始まり p2 で終了します。 曲線が制御点を通過しませんが、制御点は磁石、特定の方向に曲線を取得し、湾曲方法に影響を与えてとして機能します。 次の図は、そのエンドポイントの制御点とベジエ曲線を示します。  
  
 ![ベジエ スプライン](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 曲線は、p1 で開始し、制御ポイント c1 に向かって移動します。 P1 に曲線の接線は、c1 を p1 から描画される直線です。 エンドポイント p2 の接線は、c2 から p2 に描画される直線です。  
  
## <a name="drawing-bzier-splines"></a>ベジエ スプラインを描画  
 インスタンスが必要な本のベジエ スプラインを描画するために、<xref:System.Drawing.Graphics>クラスと<xref:System.Drawing.Pen>します。 インスタンス、<xref:System.Drawing.Graphics>クラスを提供、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッド、および<xref:System.Drawing.Pen>曲線を表示するために使用する線の色、幅などの属性を格納します。 <xref:System.Drawing.Pen>への引数の 1 つとして渡される、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッド。 残りの引数が渡される、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッドは、エンドポイントとの制御点。 次の例では、開始位置 (0, 0) のベジエ スプラインを描画するポイント (40, 20) と (80, 150) を制御し、終了位置 (100, 10)。  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 次の図は、曲線、コントロール ポイント、および 2 つの接線を示します。  
  
 ![ベジエ スプライン](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 ベジエ スプラインは、自動車業界での設計向けもともとサンピエール ベジエによって開発されました。 さまざまな種類のコンピューター支援設計で利用できることがわかっていますので、フォントの輪郭の定義にも使用します。 ベジエ スプラインは、さまざまな図形の一部は、次の図に示しますを生成できます。  
  
 ![パス](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [曲線の作成と描画](constructing-and-drawing-curves.md)
- [方法: 描画の Graphics オブジェクトを作成します。](how-to-create-graphics-objects-for-drawing.md)
- [方法: ペンを作成します。](how-to-create-a-pen.md)
