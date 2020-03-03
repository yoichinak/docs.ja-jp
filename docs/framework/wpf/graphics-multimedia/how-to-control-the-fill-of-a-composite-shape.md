---
title: '方法: 複合図形の塗りつぶしを制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 89f69d392e8838af99538c759a2f06453e1bcd60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855902"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>方法: 複合図形の塗りつぶしを制御する

または<xref:System.Windows.Media.GeometryGroup> <xref:System.Windows.Media.GeometryGroup.FillRule%2A> のプロパティは、指定された点がジオメトリの一部であるかどうかを判断するために複合図形が使用する"rule"を<xref:System.Windows.Media.PathGeometry>指定します。 には<xref:System.Windows.Media.FillRule> <xref:System.Windows.Media.FillRule.EvenOdd> 、と<xref:System.Windows.Media.FillRule.Nonzero>の2つの有効な値があります。 以下のセクションでは、これら 2 つの規則の使用方法を説明します。

**EvenOdd**このルールでは、そのポイントから任意の方向に無限に伸びる射線を描画し、その射線が交差する特定の図形内のパスセグメントの数をカウントすることによって、その点が塗りつぶし領域内にあるかどうかを判断します。 この数値が偶数の場合は、ポイントは内側にあります。偶数の場合は、ポイントは外側にあります。

たとえば、次の XAML は、をに<xref:System.Windows.Media.GeometryGroup.FillRule%2A> <xref:System.Windows.Media.FillRule.EvenOdd>設定して、一連の同心円リング (ターゲット) から構成される複合図形を作成します。

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]

前の例で作成した図を次に示します。

![色を交互にした一連の同心円リングで構成される円。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)

前の図では、中央と3番目のリングは塗りつぶされていないことに注意してください。 これは、これら 2 つのリングの任意の点から描画された射線が、偶数個のセグメントを通過するためです。 次の図を参照してください。

![円で描画された EvenOdd 光線を示す図。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)

**なら**このルールは、ある点から任意の方向に無限に伸びる射線を描画し、図形のセグメントが射線と交差する場所を調べることによって、パスの塗りつぶし領域にポイントがあるかどうかを判断します。 0 からカウントを開始し、パス セグメントが左から右に射線と交わるたびに 1 を加算し、パス セグメントが右から左に射線と交わるたびに 1 を減算します。 交差のカウント後、結果が 0 の場合は、ポイントは、パスの外側にあります。 それ以外の場合は、内側にあります。

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]

前の例を使用して、 <xref:System.Windows.Media.FillRule.Nonzero>の<xref:System.Windows.Media.GeometryGroup.FillRule%2A>値をにすると、次のような結果が得られます。

![すべて同じ色で塗りつぶされた一連の同心円リングで構成される円。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)

上の図からわかるように、すべてのリングが塗りつぶされます。 これは、すべてのセグメントが同じ方向で、任意の点から描画された射線は 1 つ以上のセグメントと交わり、交差の合計が 0 にならないためです。 たとえば、次の図では、赤の矢印はセグメントが描画される方向を表し、白い矢印は最も内側のリングの点から伸びる任意の射線を表しています。 値 0 から開始し、セグメントは左から右に射線と交わるため、射線が交わるセグメントごとに値 1 が加算されます。

![0以外の FillRule プロパティ値を示す図。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)

ルールの<xref:System.Windows.Media.FillRule.Nonzero>動作をより適切に示すには、さまざまな方向で実行されるセグメントを含むより複雑な図形が必要です。 次の XAML コードでは、前の例と同様の図形を作成します。 <xref:System.Windows.Media.PathGeometry>ただし、で<xref:System.Windows.Media.EllipseGeometry>はなくを使用して作成されます。これは、同心円の同心円を完全に閉じた状態ではなく、4つの同心円円弧を作成します。

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]

前の例で作成した図を次に示します。

![3番目の弧が塗りつぶされていない、一連の同心円リングで構成される円。](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)

中央から 3 番目の円弧が塗りつぶされていないことに注意してください。 この理由を次の図に示します。 この図で、赤い矢印はセグメントが描画されている方向を表しています。 2 つの白い矢印は、"塗りつぶされていない" 領域内の点から外に向かって伸びる、2 本の任意の射線を表しています。 この図からわかるように、指定された射線がパス内でセグメントと交わることによる値の合計は 0 です。 前に定義したように、合計が 0 となるのは、その点がジオメトリの一部でない (塗りつぶしに含まれない) ことを意味し、合計が 0 で*ない*場合 (負の値を含む) は、その点がジオメトリの一部であることを意味しています。

![セグメントが交差する任意の線を示す図。](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)

> [!NOTE]
> の目的では<xref:System.Windows.Media.FillRule>、すべての図形が閉じていると見なされます。 セグメントにすき間がある場合は、架空の線を描画して、そのすき間を閉じます。 上の例では、リングに小さなすき間があります。 この場合、このすき間を通る射線は、別の方向に伸びる射線とは異なる結果を生じると思えるかもしれません。 次に示すのは、これらのギャップの1つと、それを閉じるための "虚数セグメント" (を適用<xref:System.Windows.Media.FillRule>するために描画されるセグメント) を拡大したものです。

![常に閉じられている FillRule セグメントを示す図。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)

## <a name="example"></a>例

## <a name="see-also"></a>関連項目

- [複合図形を作成する](how-to-create-a-composite-shape.md)
- [ジオメトリの概要](geometry-overview.md)
