---
title: GDI+ でのカーディナル スプライン
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
ms.openlocfilehash: 4588f6f606f0f479aeae1d143f23175ec4be32a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779133"
---
# <a name="cardinal-splines-in-gdi"></a>GDI+ でのカーディナル スプライン
カーディナル スプラインは、大きな曲線を形成に参加している個々 の曲線のシーケンスです。 スプラインは、ポイントおよびテンション パラメーターの配列を指定します。 カーディナル スプラインは、配列内の各ポイントをスムーズに通過します。曲線のテンションの急激な変化やがあります。 次の図は、一連のポイントと、セット内の各ポイントを通過するカーディナル スプラインを示します。  
  
 ![カーディナル スプライン](./media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>物理や数学スプライン  
 物理スプラインとは木材やその他の柔軟なマテリアルのシンです。 数学的なスプラインの登場によって、前に、デザイナーは、曲線を描画するために物理スプラインを使用します。 デザイナーを枚の用紙にスプラインを配置し、点の特定のセットを固定します。 デザイナーは、曲線をペンや鉛筆とスプラインに沿って描画することで作成し、でした。 点の特定のセットには、さまざまな物理スプラインのプロパティに応じて、曲線を起動できませんでした。 たとえば、曲げに対する抵抗力が強いスプラインが生成されますより非常に柔軟にスプライン曲線は異なります。  
  
 数学的なスプライン数式は、柔軟な棒プロパティに基づくはため、数学的なスプラインによって生成された曲線は物理的なスプラインによって生成された 1 回の曲線に似ています。 物理スプラインな点の特定のセットを別の曲線が生成されますと同様テンション パラメーターの値が異なる数学スプラインはポイントの指定されたセット内のさまざまな曲線を生成します。 次の図は、同じ点のセットを通過する 4 つのカーディナル スプラインを示します。 各スプラインのテンションが表示されます。 0 のテンションは曲線ポイント間の最短の方法 (直線) を実行するように強制無限の物理的な対立に対応します。 テンション 1 の値は、スプライン曲げの合計が最低のパスを実行することができます、物理ありませんテンションに対応します。 張力値が 1 より大きい、曲線のように動作、圧縮された春経路が長くなってにプッシュします。  
  
 ![カーディナル スプライン](./media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 前の図の 4 つのスプラインは、開始位置に、同じ接線を共有します。 タンジェントとは、開始点と曲線に沿って次の点を結ぶ線です。 同様に、終了位置で共有正接とは、終了位置から、曲線上の以前の時点に描画される直線。  
  
 カーディナル スプラインを描画するために、インスタンスの必要があります、<xref:System.Drawing.Graphics>クラス、<xref:System.Drawing.Pen>と配列の<xref:System.Drawing.Point>オブジェクトのインスタンス、<xref:System.Drawing.Graphics>クラスを提供します、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッドで、スプラインを描画するには、および<xref:System.Drawing.Pen>線の幅と色など、スプラインの属性を格納します。 配列<xref:System.Drawing.Point>オブジェクトが曲線を通過するポイントを格納します。 次のコード例は、含まれている地点を通過するカーディナル スプラインを描画する方法を示しています。`myPointArray`します。 3 番目のパラメーターは、テンションです。  
  
 [!code-csharp[LinesCurvesAndShapes#31](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>関連項目

- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [曲線の作成と描画](constructing-and-drawing-curves.md)
