---
title: -のアニメーションの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 9708a4d06e8a2aa65fb4d3bb959f4699237a2bc6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762398"
---
# <a name="fromtoby-animations-overview"></a>From/To/By アニメーションの概要
このトピックでは、From/To/By アニメーションを使って依存関係プロパティをアニメーション化する方法を説明します。 From/To/By アニメーションでは、2 つの値の間の遷移が作成されます。  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するのには理解しておく[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーション機能。 アニメーションの機能の概要については、次を参照してください。、[アニメーションの概要](animation-overview.md)します。  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>From/To/By アニメーションとは  
 From/に/By をアニメーションの種類は、<xref:System.Windows.Media.Animation.AnimationTimeline>開始値および終了値の間の遷移を作成します。 移行が完了するまで時間が続く、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>アニメーションの。  
  
 適用する、From/を/を使用してプロパティにアニメーションを<xref:System.Windows.Media.Animation.Storyboard>マークアップとコード、またはを使用して、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>コード内のメソッド。 作成する From/To/By アニメーションを使用することも、<xref:System.Windows.Media.Animation.AnimationClock>を 1 つまたは複数のプロパティに適用します。 アニメーションを適用するためのさまざまなメソッドの詳細については、「[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)」を参照してください。  
  
 From/To/By アニメーションは、2 つのターゲット値以外の値を持つことはできません。 3 つ以上のターゲット値を持つアニメーションを必要とする場合は、キー フレーム アニメーションを使います。 キー フレーム アニメーションには、[キー フレーム アニメーションの概要](key-frame-animations-overview.md)します。  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>From/To/By アニメーションの種類  
 アニメーションはプロパティ値を生成するため、プロパティの型ごとに異なるアニメーションの種類があります。 受け取るプロパティをアニメーション化する、<xref:System.Double>など、 <xref:System.Windows.FrameworkElement.Width%2A> 、要素のプロパティを生成するアニメーションを使用して、<xref:System.Double>値。 受け取るプロパティをアニメーション化する、<xref:System.Windows.Point>を生成するアニメーションを使用して、<xref:System.Windows.Point>値、という具合です。  
  
 属しているによって/アニメーション クラス、<xref:System.Windows.Media.Animation>名前空間と、次の名前付け規則。  
  
 *\<Type>* `Animation`  
  
 ここで、*\<Type>* は、クラスがアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次の From/To/By アニメーション クラスが用意されています。  
  
|プロパティの型|対応する From/To/By アニメーションのクラス|  
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
 From/To/By アニメーションでは、2 つのターゲット値の間の遷移が作成されます。 開始値を指定するが一般的 (を使用して設定、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ) と終了値 (を使用して設定、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ)。 ただし、開始値、終了値、またはオフセット値のみを指定することもできます。 これらの場合、アニメーションは不足しているターゲット値をアニメーション化するプロパティから取得します。 次の一覧では、アニメーションのターゲット値を指定する方法について説明します。  
  
- **開始値**  
  
     使用して、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ アニメーションの開始値を明示的に指定する場合。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ自体は、または、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>または<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ。 のみを指定する場合、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティをアニメーション化されたプロパティの基本値に、その値からアニメーション遷移します。  
  
- **終了値**  
  
     アニメーションの終了値を指定するには、次のように使用します。 その<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ。 使用する場合、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ自体で、アニメーションは開始値の同じプロパティに適用される別のアニメーションの出力から、またはアニメーション化されているプロパティから。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティと共に、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティを明示的に開始および終了のアニメーションの値を指定します。  
  
- **オフセット値**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティでは、代わりに、明示的な開始時刻またはアニメーションの終了値のオフセットを指定することができます。 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーションのプロパティがどの程度のアニメーションによって、その期間にわたって値を変更します。 を指定します。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ自体または、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ。 のみを指定する場合、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ、アニメーションをプロパティの基本値または別のアニメーションの出力にオフセット値を追加します。  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>From/To/By 値の使用  
 次のセクションでは、使用方法を説明します、 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ単独でまたは組み合わせています。  
  
 例では、このセクションの各使用、 <xref:System.Windows.Media.Animation.DoubleAnimation>、アニメーションの種類、/、アニメーション化するのには、<xref:System.Windows.FrameworkElement.Width%2A>のプロパティを<xref:System.Windows.Shapes.Rectangle>つまり 10 デバイス非依存ピクセル高と 100 デバイス非依存ピクセル幅。  
  
 各例では、 <xref:System.Windows.Media.Animation.DoubleAnimation>、およびすべて From/に/でのプロパティによってアニメーション動作は同じです。 これらの例を使用しますが、 <xref:System.Windows.Media.Animation.Storyboard>、他の方法で、/アニメーションを使用することができます。 詳細については、次を参照してください。[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)します。  
  
### <a name="fromto"></a>From/To  
 設定すると、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>で指定されている値からアニメーションを同時に、値、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティで指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ。  
  
 次の例のセット、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>のプロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation>を 50 とその<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティを 300 にします。 結果として、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>が 50 から 300 にアニメーション化します。  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>目的  
 設定した場合だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティにアニメーションによって指定される値を同じプロパティに適用していた構成アニメーションの出力から、またはアニメーションのプロパティの基本値から、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ。  
  
 (「構成アニメーション」を指す、<xref:System.Windows.Media.Animation.ClockState.Active>または<xref:System.Windows.Media.Animation.ClockState.Filling>以前を使用して現在のアニメーションが適用されたときに有効なままである同じプロパティに適用するアニメーション、<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>ハンドオフ動作します)。  
  
 次の例の設定だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>のプロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation>を 300 にします。 開始値が指定されていないため、<xref:System.Windows.Media.Animation.DoubleAnimation>の基本値 (100) を使用して、<xref:System.Windows.FrameworkElement.Width%2A>開始値としてプロパティ。 <xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>が 100 からアニメーションのターゲット値 300 にアニメーション化します。  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>By  
 設定した場合だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーションのプロパティをアニメーション化されているプロパティの基本値または値で指定された値の合計に構成アニメーションの出力から、アニメーション、 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ。  
  
 次の例の設定だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>のプロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation>を 300 にします。 例は、開始値を指定していないため、<xref:System.Windows.Media.Animation.DoubleAnimation>の基本値を使用して、<xref:System.Windows.FrameworkElement.Width%2A>プロパティ、100、開始値として。 終了値が追加することで決定され、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーションの開始値、100 の 300 の値。400. 結果として、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>が 100 から 400 にアニメーション化します。  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 設定すると、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーションのプロパティ で指定されている値からアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティの合計で指定されている値を<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ。  
  
 次の例のセット、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>のプロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation>を 50 とその<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティを 300 にします。 終了値が追加することで決定され、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーションの開始値、50 の 300 の値。350. 結果として、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>が 50 から 350 にアニメーション化します。  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>From  
 だけ指定する、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>アニメーションの値、アニメーションで指定されている値から、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ、または構成アニメーションの出力にアニメーション化されているプロパティの基本値にします。  
  
 次の例の設定だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>のプロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation>を 50。 終了値が指定されていないため、<xref:System.Windows.Media.Animation.DoubleAnimation>の基本値を使用して、<xref:System.Windows.FrameworkElement.Width%2A>プロパティ、100、終了値として。 <xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>が 50 からの基本値をアニメーション化、<xref:System.Windows.FrameworkElement.Width%2A>プロパティ、100 です。  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 両方を設定する場合、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>、アニメーションのプロパティを<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティは無視されます。  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>他のアニメーションの種類  
 /アニメーションがない唯一の種類のアニメーションを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供: キー フレーム アニメーションとパス アニメーションも用意されています。  
  
- キー フレーム アニメーションは、キー フレームを使って記述されている任意の数の目標値に沿ってアニメーション化します。 詳細については、次を参照してください。、[キー フレーム アニメーションの概要](key-frame-animations-overview.md)します。  
  
- パス アニメーションからの出力値を生成する、<xref:System.Windows.Media.PathGeometry>します。 詳細については、次を参照してください。、[パス アニメーションの概要](path-animations-overview.md)します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、独自のカスタム アニメーションの種類を作成することもできます。 詳細については、次を参照してください。、[カスタム アニメーションの概要](custom-animations-overview.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [アニメーションの概要](animation-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [パス アニメーションの概要](path-animations-overview.md)
- [カスタム アニメーションの概要](custom-animations-overview.md)
- [アニメーションのターゲット値 (From、To、および By) のサンプル](https://go.microsoft.com/fwlink/?LinkID=159988)
