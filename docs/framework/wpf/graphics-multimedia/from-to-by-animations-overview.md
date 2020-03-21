---
title: From-to-By アニメーションの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 135f01823d374b30f8d4d41762d2267a254f98c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186463"
---
# <a name="fromtoby-animations-overview"></a>From/To/By アニメーションの概要
このトピックでは、From/To/By アニメーションを使って依存関係プロパティをアニメーション化する方法を説明します。 From/To/By アニメーションでは、2 つの値の間の遷移が作成されます。  
  
<a name="prereq"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、アニメーション機能について[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]理解している必要があります。 アニメーション機能の概要については、「 アニメーションの[概要](animation-overview.md)」を参照してください。  
  
<a name="whatisanimation"></a>
## <a name="what-is-a-fromtoby-animation"></a>From/To/By アニメーションとは  
 From/To/By アニメーションは、開始値<xref:System.Windows.Media.Animation.AnimationTimeline>と終了値の間の遷移を作成するタイプです。 トランジションの完了にかかる時間は、そのアニメーションの<xref:System.Windows.Media.Animation.Timeline.Duration%2A>によって決まります。  
  
 プロパティに From/To/By アニメーションを適用するには、マークアップと<xref:System.Windows.Media.Animation.Storyboard>コード内で を使用するか、コード<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>内でメソッドを使用します。 また、From/To/By アニメーションを使用して、作成<xref:System.Windows.Media.Animation.AnimationClock>して 1 つ以上のプロパティに適用することもできます。 アニメーションを適用するためのさまざまなメソッドの詳細については、「[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)」を参照してください。  
  
 From/To/By アニメーションは、2 つのターゲット値以外の値を持つことはできません。 3 つ以上のターゲット値を持つアニメーションを必要とする場合は、キー フレーム アニメーションを使います。 キー フレーム アニメーションについては、「キー[フレーム アニメーションの概要](key-frame-animations-overview.md)」を参照してください。  
  
<a name="animation_types"></a>
## <a name="fromtoby-animation-types"></a>From/To/By アニメーションの種類  
 アニメーションはプロパティ値を生成するため、プロパティの型ごとに異なるアニメーションの種類があります。 を受け取るプロパティ (要素<xref:System.Double>の<xref:System.Windows.FrameworkElement.Width%2A>プロパティなど) をアニメーション化するには、値を生成<xref:System.Double>するアニメーションを使用します。 をとるプロパティをアニメーション化するには<xref:System.Windows.Point>、値を生成<xref:System.Windows.Point>するアニメーションを使用します。  
  
 From/To/By アニメーション クラスは<xref:System.Windows.Media.Animation>名前空間に属し、次の命名規則を使用します。  
  
 *\<タイプ>*`Animation`  
  
 [*\<タイプ>* は、クラスがアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次の From/To/By アニメーション クラスが用意されています。  
  
|プロパティの種類|対応する From/To/By アニメーションのクラス|  
|-------------------|------------------------------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>
## <a name="target-values"></a>ターゲット値  
 From/To/By アニメーションでは、2 つのターゲット値の間の遷移が作成されます。 一般的には、開始値 (<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティを使用して設定) と終了値 (プロパティを使用して設定)<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>を指定します。 ただし、開始値、終了値、またはオフセット値のみを指定することもできます。 これらの場合、アニメーションは不足しているターゲット値をアニメーション化するプロパティから取得します。 次の一覧では、アニメーションのターゲット値を指定する方法について説明します。  
  
- **開始値**  
  
     アニメーションの<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>開始値を明示的に指定する場合は、このプロパティを使用します。 プロパティは、単独<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>で使用することも、 または<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>または プロパティと一緒に使用することもできます。 プロパティのみを指定すると<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、アニメーションはその値からアニメーション化されたプロパティの基本値に遷移します。  
  
- **終了値**  
  
     アニメーションの終了値を指定するには、アニメーションのプロパティ<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>を使用します。 プロパティを単独で<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>使用する場合、アニメーションはアニメーション化されているプロパティまたは同じプロパティに適用される別のアニメーションの出力から開始値を取得します。 プロパティとプロパティを<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>使用して、アニメーション<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>の開始値と終了値を明示的に指定できます。  
  
- **オフセット値**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>このプロパティを使用すると、アニメーションの開始値または終了値を明示的に指定するのではなく、オフセットを指定できます。 アニメーション<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>のプロパティは、アニメーションの継続時間に対する値の変更量によって指定されます。 プロパティは、単独<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>で使用することも、プロパティと<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>共に使用することもできます。 プロパティのみを指定した<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>場合、アニメーションは、プロパティの基本値または別のアニメーションの出力にオフセット値を追加します。  
  
<a name="examples"></a>
## <a name="using-fromtoby-values"></a>From/To/By 値の使用  
 以下のセクションでは、 、 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティを一緒に使用する方法、または個別に使用する方法について説明します。  
  
 このセクションの例では、それぞれ<xref:System.Windows.Media.Animation.DoubleAnimation>From/To/By アニメーションの一種である を使用して、高さ<xref:System.Windows.FrameworkElement.Width%2A>10<xref:System.Windows.Shapes.Rectangle>デバイスの独立ピクセルと幅 100 のデバイス独立ピクセルのプロパティをアニメーション化します。  
  
 各例では<xref:System.Windows.Media.Animation.DoubleAnimation>、すべての From/To/By アニメーションの From、To、By の各プロパティを使用しますが、同じ動作をします。 これらの各例では<xref:System.Windows.Media.Animation.Storyboard>を使用していますが、From/To/By アニメーションは他の方法で使用できます。 詳細については、「プロパティ[アニメーションのテクニックの概要」を](property-animation-techniques-overview.md)参照してください。  
  
### <a name="fromto"></a>From/To  
 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>値<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>と 値を同時に設定すると、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>アニメーションはプロパティで指定された値から<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティで指定された値に進みます。  
  
 次の使用例は、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation>を 50 に<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>設定し、そのプロパティを 300 に設定します。 その結果、のが<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Shapes.Rectangle>50から300までアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>ターゲット  
 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティだけを設定すると、アニメーション化されたプロパティの基本値、または同じプロパティに既に適用された合成アニメーションの出力からプロパティで指定された値までアニメーションが進行します<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>。  
  
 (「アニメーションの作成」とは、ハンド<xref:System.Windows.Media.Animation.ClockState.Active>オフ<xref:System.Windows.Media.Animation.ClockState.Filling>動作を使用<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>して現在のアニメーションが適用されたときに有効な同じプロパティに以前に適用されたまたはアニメーションのことです。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>のプロパティだけを<xref:System.Windows.Media.Animation.DoubleAnimation>300 に設定します。 開始値が指定されていないため、 では<xref:System.Windows.Media.Animation.DoubleAnimation>、<xref:System.Windows.FrameworkElement.Width%2A>プロパティの基本値 (100) を開始値として使用します。 <xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>アニメーションは、100 からアニメーションのターゲット値である 300 にアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>別  
 アニメーションの<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティだけを設定すると、アニメーション化されているプロパティの基本値から、または構成アニメーションの出力から、その値とプロパティで指定された値の合計にアニメーションが進行します<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>のプロパティだけを<xref:System.Windows.Media.Animation.DoubleAnimation>300 に設定します。 この例では開始値を指定しないため、 では<xref:System.Windows.Media.Animation.DoubleAnimation>、<xref:System.Windows.FrameworkElement.Width%2A>プロパティの基本値である 100 を開始値として使用します。 終了値は、アニメーションの<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>値である 300 を開始値 100: 400 に加算することによって決定されます。 その結果、のが<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Shapes.Rectangle>100から400にアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 アニメーションの プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティを設定すると、アニメーションは<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティで指定された値から、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティの合計で指定された値に進みます。  
  
 次の使用例は、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation>を 50 に<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>設定し、そのプロパティを 300 に設定します。 終了値は、アニメーションの<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>値である 300 を開始値 50: 350 に加算することによって決定されます。 その結果、のが<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Shapes.Rectangle>50から350にアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>ソース  
 アニメーションの<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>値だけを指定すると、アニメーションは<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティで指定された値から、アニメーション化されているプロパティの基本値、または構成アニメーションの出力に進みます。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>の<xref:System.Windows.Media.Animation.DoubleAnimation>プロパティだけを 50 に設定します。 終了値が指定されていないため、 は<xref:System.Windows.Media.Animation.DoubleAnimation><xref:System.Windows.FrameworkElement.Width%2A>プロパティの基本値である 100 を終了値として使用します。 のは、50 からプロパティの基本値 100 にアニメーション化されます<xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle>  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 アニメーションの プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>と プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>の両方を設定した場合<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>、プロパティは無視されます。  
  
<a name="otheranimationtypes"></a>
## <a name="other-animation-types"></a>他のアニメーションの種類  
 From/To/By アニメーションは、アニメーションの唯一の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]タイプではありません: キー フレーム アニメーションとパス アニメーションも提供します。  
  
- キー フレーム アニメーションは、キー フレームを使って記述されている任意の数の目標値に沿ってアニメーション化します。 詳細については、「 キー[フレーム アニメーションの概要](key-frame-animations-overview.md)」を参照してください。  
  
- パス アニメーションは、 から出力値<xref:System.Windows.Media.PathGeometry>を生成します。 詳細については、「[パス アニメーションの概要](path-animations-overview.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、独自のカスタム アニメーションの種類を作成することもできます。 詳細については、「 カスタム[アニメーションの概要](custom-animations-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [アニメーションの概要](animation-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [パス アニメーションの概要](path-animations-overview.md)
- [カスタム アニメーションの概要](custom-animations-overview.md)
- [アニメーションのターゲット値 (From、To、および By) のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
