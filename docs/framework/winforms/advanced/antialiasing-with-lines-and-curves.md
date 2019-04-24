---
title: 直線と曲線のアンチエイリアシング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: cbc9033f18f1ab255862c8f8e2891aa9b68cf8d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078499"
---
# <a name="antialiasing-with-lines-and-curves"></a>直線と曲線のアンチエイリアシング
使用すると[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]直線を描画する開始点と、直線の終了点を提供するが、行の個々 のピクセルについての情報を提供する必要はありません。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 特定のディスプレイ デバイスに、行を表示するにどのピクセルはオンにする、ディスプレイ ドライバー ソフトウェアと連携して動作します。  
  
## <a name="aliasing"></a>エイリアス  
 点 (16, 10) に (4, 2) のポイントから移動する直接赤色の線を検討してください。 座標システムでは、左上隅の原点とメジャーの単位がピクセルであることを想定しています。 また、x 軸が下、右、y 軸を指しているとします。 次の図は、マルチカラーの背景色で描画される赤色の線の拡大表示を示します。  
  
 ![行のアンチエイリアシングなし](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 行を表示するために使用される赤いピクセルは不透明です。 行には、部分的に透明なピクセルがありません。 この種類の行のレンダリングは、行ぎざぎざに表示し、行では、階段のようにします。 階段に 1 行を表すには、この手法はエイリアスと呼ばれる階段には、理論上の線のエイリアスです。  
  
## <a name="antialiasing"></a>アンチエイリアシング  
 行を表示するためのより高度な手法では、部分的に透明なピクセルと不透明なピクセルを使用する必要があります。 ピクセルが、純粋な赤に設定または red と背景の色のブレンドを閉じる方法によっては行にします。 この種類の表示では、アンチエイリアシングは呼び出され、人間の目がより滑らかなとして認識する行になります。 次の図は、アンチ エイリアス処理された行を生成するためにバック グラウンドで特定のピクセルをブレンドする方法を示します。  
  
 ![アンチエイリアシング線](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 アンチエイリアシング、平滑化とも呼ばれるは、曲線にも適用できます。 次の図は、平滑化された楕円の拡大表示を示します。  
  
 ![アンチエイリアシング曲線](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 次の図は、アンチエイリアシングなしで 1 回 1 回のアンチエイリアシングを使用して、実際のサイズで同じ省略記号ボタンを示します。  
  
 ![アンチエイリアシング例](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 直線と曲線のアンチエイリアシングの使用を描画するには、インスタンスを作成、<xref:System.Drawing.Graphics>クラスし、設定、<xref:System.Drawing.Graphics.SmoothingMode%2A>プロパティを<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>または<xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>します。 描画方法の 1 つを同じに呼び出す<xref:System.Drawing.Graphics>クラス。  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [方法: テキストのアンチエイリアシングを使用します。](how-to-use-antialiasing-with-text.md)
