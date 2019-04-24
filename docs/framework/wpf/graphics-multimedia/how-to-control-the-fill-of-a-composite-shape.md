---
title: '方法: 複合図形の塗りつぶしを制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 0ba07d8979a2910ce4ec775493e38c714240f642
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427475"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>方法: 複合図形の塗りつぶしを制御する
<xref:System.Windows.Media.GeometryGroup.FillRule%2A>のプロパティを<xref:System.Windows.Media.GeometryGroup>または<xref:System.Windows.Media.PathGeometry>、複合図形を使用して、指定された点がジオメトリの一部であるかどうかを確認する「規則」を指定します。 2 つの値がある<xref:System.Windows.Media.FillRule>:<xref:System.Windows.Media.FillRule.EvenOdd>と<xref:System.Windows.Media.FillRule.Nonzero>します。 以下のセクションでは、これら 2 つの規則の使用方法を説明します。  
  
 **EvenOdd:** このルールは、その時点から任意の方向に無限に伸びる射線を描画し、その光線が交差する特定の図形のパス セグメントの数をカウントして、ポイントが塗りつぶし領域内がかどうかを判断します。 この数値が偶数の場合は、ポイントは内側にあります。偶数の場合は、ポイントは外側にあります。  
  
 たとえば、次の XAML での一連の同心リング (ターゲット) から成る複合図形を作成します.、<xref:System.Windows.Media.GeometryGroup.FillRule%2A>設定<xref:System.Windows.Media.FillRule.EvenOdd>します。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 前の例で作成した図を次に示します。  
  
 ![色を交互に一連の同心リングから成る円です。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)  
  
 前の図では、中央と 3 番目のリングが塗りつぶされていないことに注意してください。 これは、これら 2 つのリングの任意の点から描画された射線が、偶数個のセグメントを通過するためです。 次の図を参照してください。  
  
 ![円の中で描画 EvenOdd 光線を示す図。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)  
  
 **0 以外の場合。** このルールは、その時点から任意の方向に無限に伸びる射線を描画し、図形のセグメントが光線と交差する場所を調べることによって、ポイントが、パスの塗りつぶし領域内がかどうかを判断します。 0 からカウントを開始し、パス セグメントが左から右に射線と交わるたびに 1 を加算し、パス セグメントが右から左に射線と交わるたびに 1 を減算します。 交差のカウント後、結果が 0 の場合は、ポイントは、パスの外側にあります。 それ以外の場合は、内側にあります。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 前の例の値を使用して<xref:System.Windows.Media.FillRule.Nonzero>の<xref:System.Windows.Media.GeometryGroup.FillRule%2A>結果として、次の図を示します。  
  
 ![構成のシリーズ同心リングすべて同じ色で塗りつぶされた円です。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)  
  
 上の図からわかるように、すべてのリングが塗りつぶされます。 これは、すべてのセグメントが同じ方向で、任意の点から描画された射線は 1 つ以上のセグメントと交わり、交差の合計が 0 にならないためです。 たとえば、次の図に赤の矢印はセグメントが描画される方向を表すし、白い矢印は、最も内側のリング内のポイントから任意の射線を表します。 値 0 から開始し、セグメントは左から右に射線と交わるため、射線が交わるセグメントごとに値 1 が加算されます。  
  
 ![0 以外と等しい FillRule プロパティ値を示す図。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)  
  
 動作をわかりやすく示すために<xref:System.Windows.Media.FillRule.Nonzero>規則セグメントがさまざまな方向で実行されているより複雑な図形が必要です。 次の XAML コードで作成する点を除いて前の例と類似した図形を作成、<xref:System.Windows.Media.PathGeometry>ではなく、<xref:System.Windows.Media.EllipseGeometry>同心円を完全に終了ではなく 4 つの同心の円弧を作成します。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 前の例で作成した図を次に示します。  
  
 ![3 番目の円弧が塗りつぶされていないと色を交互に一連の同心リングから成る円です。](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)  
  
 中央から 3 番目の円弧が塗りつぶされていないことに注意してください。 次の図は、これが理由を示しています。 この図で、赤い矢印はセグメントが描画されている方向を表しています。 2 つの白い矢印は、"塗りつぶされていない" 領域内の点から外に向かって伸びる、2 本の任意の射線を表しています。 この図からわかるように、指定された射線がパス内でセグメントと交わることによる値の合計は 0 です。 前に定義したように、合計が 0 となるのは、その点がジオメトリの一部でない (塗りつぶしに含まれない) ことを意味し、合計が 0 で*ない*場合 (負の値を含む) は、その点がジオメトリの一部であることを意味しています。  
  
 ![任意の光線交差セグメントを示す図。](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)  
  
 **注:** 目的で<xref:System.Windows.Media.FillRule>、すべての図形が終了と見なされます。 セグメントにすき間がある場合は、架空の線を描画して、そのすき間を閉じます。 上の例では、リングに小さなすき間があります。 この場合、このすき間を通る射線は、別の方向に伸びる射線とは異なる結果を生じると思えるかもしれません。 このようなギャップと「架空のセグメント」のいずれかを拡大した図を次に示します (適用するために描画されるセグメント、 <xref:System.Windows.Media.FillRule>) そのすき間を閉じる。  
  
 ![常に閉じている FillRule セグメントを示す図。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)  
  
## <a name="example"></a>例  
  
## <a name="see-also"></a>関連項目

- [複合図形を作成する](how-to-create-a-composite-shape.md)
- [ジオメトリの概要](geometry-overview.md)
