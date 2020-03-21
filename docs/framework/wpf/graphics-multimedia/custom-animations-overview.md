---
title: カスタム アニメーションの概要
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
ms.openlocfilehash: c5f315992e8ae37bc79602e6986d90e7af591fb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186550"
---
# <a name="custom-animations-overview"></a>カスタム アニメーションの概要
このトピックでは、カスタム キー フレームやアニメーション クラスを作成して、またはフレームごとのコールバックを使ってバイパスすることにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション システムを拡張する方法と、それが必要な状況について説明します。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって提供されるさまざまな種類のアニメーションに精通している必要があります。 詳しくは、「From/To/By アニメーションの概要」、「[キー フレーム アニメーションの概要](key-frame-animations-overview.md)」、および「[パス アニメーションの概要](path-animations-overview.md)」をご覧ください。  
  
 アニメーション クラスは<xref:System.Windows.Freezable>クラスから継承されるため、<xref:System.Windows.Freezable>オブジェクトとから継承する方法について理解しておく必要があります<xref:System.Windows.Freezable>。 詳しくは、「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」をご覧ください。  
  
<a name="extendingtheanimationsystem"></a>
## <a name="extending-the-animation-system"></a>アニメーション システムの拡張  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション システムには、使う組み込み機能のレベルに応じて、さまざまな拡張方法があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション エンジンには、次の 3 つの主な機能拡張ポイントがあります。  
  
- などの<xref:System.Windows.Media.Animation.DoubleKeyFrame> * \<Type>* KeyFrame クラスの 1 つを継承して、カスタム のキー フレーム オブジェクトを作成します。 この方法では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション エンジンの組み込み機能のほとんどを使います。  
  
- * \<AnimationBase*クラスの 1 つ<xref:System.Windows.Media.Animation.AnimationTimeline>または 1 つを継承して独自のアニメーション クラスを作成>。  
  
- フレームごとのコールバックを使って、フレームごとにアニメーションを生成します。 この方法は、アニメーションおよびタイミング システムを完全にバイパスします。  
  
 次の表では、いくつかのアニメーション システム拡張シナリオについて説明します。  
  
|目的...|使う方法|  
|-------------------------|-----------------------|  
|対応する*\<* 型を持つ型の値間の補間をカスタマイズするキー フレームを使用してアニメーション>|カスタム キー フレームを作成します。 詳しくは、「[カスタム キー フレームを作成する](#createacustomkeyframe)」セクションをご覧ください。|  
|対応する*\<タイプ>* アニメーションを持つ型の値間の補間だけでなく、カスタマイズします。|アニメーション化する型に対応する*\<Type>* AnimationBase クラスから継承するカスタム アニメーション クラスを作成します。 詳しくは、「[カスタム アニメーション クラスを作成する](#createacustomanimationtype)」セクションをご覧ください。|  
|対応する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーションがない型をアニメーション化する|を<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>使用するか、 から<xref:System.Windows.Media.Animation.AnimationTimeline>継承するクラスを作成します。 詳しくは、「[カスタム アニメーション クラスを作成する](#createacustomanimationtype)」セクションをご覧ください。|  
|フレームごとに計算され、最後のオブジェクト相互作用セットに基づく値のある、複数のオブジェクトをアニメーション化する|フレームごとのコールバックを使います。 詳しくは、「[フレームごとのコールバックを使用する](#useperframecallback)」セクションをご覧ください。|  
  
<a name="createacustomkeyframe"></a>
## <a name="create-a-custom-key-frame"></a>カスタム キー フレームを作成する  
 カスタム キー フレーム クラスの作成は、アニメーション システムを拡張する最も簡単な方法です。 キー フレーム アニメーションに対して異なる補間方法が必要なときは、このアプローチを使います。  「[キー フレーム アニメーションの概要](key-frame-animations-overview.md)」で説明されているように、キー フレーム アニメーションはキー フレーム オブジェクトを使って出力値を生成します。 各キー フレーム オブジェクトは 3 つの機能を実行します。  
  
- プロパティを使用してターゲット値<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>を指定します。  
  
- プロパティを使用して、その値に到達する時刻を<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>指定します。  
  
- InterpolateValueCore メソッドを実装することで、前のキー フレームの値とそれ自体の値の間を補間します。  
  
 **実装の説明**  
  
 *\<型>* キー フレーム抽象クラスから派生し、メソッドを実装します。 InterpolateValueCore メソッドは、キー フレームの現在の値を返します。 2 つのパラメーターとして、前のキー フレームの値と、0 から 1 の範囲の進行状況の値を受け取ります。 進行状況が 0 の場合は、キー フレームが開始したばかりであることを示し、値 1 はキー フレームが完了したばかりで、<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>そのプロパティで指定された値を返す必要があることを示します。  
  
 Type>KeyFrame クラスは<xref:System.Windows.Freezable>クラスから継承するため、クラスの<xref:System.Windows.Freezable.CreateInstanceCore%2A>新しいインスタンスを返すためにコアもオーバーライドする必要があります。 * \< * クラスが依存関係プロパティを使ってデータを保存しない場合、または作成の後で追加の初期化が必要な場合は、他のメソッドのオーバーライドが必要な場合があります。詳しくは、「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」をご覧ください。  
  
 カスタム*\<タイプ>* キーフレーム アニメーションを作成したら、その*種類の\<* アニメーションを使用してキー フレーム>種類で使用できます。  
  
<a name="createacustomanimationtype"></a>
## <a name="create-a-custom-animation-class"></a>カスタム アニメーション クラスを作成する  
 独自のアニメーション型を作成すると、オブジェクトをアニメーション化する方法をいっそう細かく制御できます。 独自のアニメーション タイプを作成するには、<xref:System.Windows.Media.Animation.AnimationTimeline>クラスまたは*\<Type>* AnimationBase クラスから派生させる方法の 2 つがあります。 アニメーション>*\<型*または*\<型>* から派生するキーフレーム クラスを使用して推奨されません。  
  
### <a name="derive-from-typeanimationbase"></a>\<Type>AnimationBase から派生する  
 Type>AnimationBase クラスから派生する方法は、新しいアニメーション タイプを作成する最も簡単な方法です。 * \< * この方法は、対応する*\<Type>* AnimationBase クラスが既に存在するタイプの新しいアニメーションを作成する場合に使用します。  
  
 **実装の説明**  
  
 型>アニメーション クラスから派生し、メソッドを実装します。 * \< * GetCurrentValueCore メソッドは、アニメーションの現在の値を返します。 このパラメーターには、推奨開始値、推奨終了値、および<xref:System.Windows.Media.Animation.AnimationClock>アニメーションの進行状況を決定するために使用する の 3 つのパラメーターが必要です。  
  
 Type>AnimationBase クラスは<xref:System.Windows.Freezable>クラスから継承するため、クラスの<xref:System.Windows.Freezable.CreateInstanceCore%2A>新しいインスタンスを返すためにコアもオーバーライドする必要があります。 * \< * クラスが依存関係プロパティを使ってデータを保存しない場合、または作成の後で追加の初期化が必要な場合は、他のメソッドのオーバーライドが必要な場合があります。詳しくは、「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」をご覧ください。  
  
 詳細については、アニメーション化する*\<型の型>* AnimationBase クラスの GetCurrentValueCore メソッドのドキュメントを参照してください。 例については、「[Custom Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)」(カスタム アニメーションのサンプル) をご覧ください。  
  
 **代替アプローチ**  
  
 アニメーション値の補間方法を変更するだけの場合は*\<、Type>* KeyFrame クラスのいずれかから派生することを検討してください。 作成するキー フレームは、対応する*\<型>* アニメーション使用キーフレームで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用できます。  
  
### <a name="derive-from-animationtimeline"></a>AnimationTimeline から派生する  
 一致する<xref:System.Windows.Media.Animation.AnimationTimeline>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーションがない型のアニメーションを作成する場合、または厳密に型指定されていないアニメーションを作成する場合は、クラスから派生します。  
  
 **実装の説明**  
  
 クラスから派生<xref:System.Windows.Media.Animation.AnimationTimeline>し、次のメンバーをオーバーライドします。  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A>– 新しいクラスが具象型の場合<xref:System.Windows.Freezable.CreateInstanceCore%2A>、クラスの新しいインスタンスを返すためにオーバーライドする必要があります。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>– アニメーションの現在の値を返す場合は、このメソッドをオーバーライドします。 このパラメータには、デフォルトの起点値、デフォルトの終点値、および<xref:System.Windows.Media.Animation.AnimationClock>. アニメーションの<xref:System.Windows.Media.Animation.AnimationClock>現在の時間または進行状況を取得するには、 を使用します。 既定の開始値と終了値を使うかどうかを選択できます。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>–<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>このプロパティをオーバーライドして、メソッドで指定された既定の宛先値をアニメーションで使用するかどうかを示します。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>– アニメーションが生成する出力<xref:System.Type>を示すには、このプロパティをオーバーライドします。  
  
 クラスが依存関係プロパティを使ってデータを保存しない場合、または作成の後で追加の初期化が必要な場合は、他のメソッドのオーバーライドが必要な場合があります。詳しくは、「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」をご覧ください。  
  
 推奨される ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーションによって使われる) パラダイムは、2 つの継承レベルを使うことです。  
  
1. から<xref:System.Windows.Media.Animation.AnimationTimeline>派生した抽象*\<型>* AnimationBase クラスを作成します。 このクラスはメソッドを<xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>オーバーライドする必要があります。 また、新しい抽象メソッド GetCurrentValueCore を導入し、<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>既定の発生元の値と既定の送信先の値パラメーターの型を検証するようにオーバーライドしてから、GetCurrentValueCore を呼び出します。  
  
2. 新しい<xref:System.Windows.Freezable.CreateInstanceCore%2A><xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>*\<Type>* AnimationBase クラスから継承する別のクラスを作成し、メソッド、導入した GetCurrentValueCore メソッド、およびプロパティをオーバーライドします。  
  
 **代替アプローチ**  
  
 対応する From/To/By アニメーションまたはキー フレーム アニメーションがない型をアニメーション化する場合は、 を<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>使用することを検討してください。 型が弱いため、任意の<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>種類の値をアニメーション化できます。 この方法の欠点は、離散<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>補間のみをサポートしていることです。  
  
<a name="useperframecallback"></a>
## <a name="use-per-frame-callback"></a>フレームごとのコールバックを使用する  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション システムを完全にバイパスする必要があるときは、この方法を使います。 この方法の 1 つのシナリオは、各アニメーション ステップでオブジェクトの最後の一連のやり取りに基づいてアニメーション化されるオブジェクトの新しい向きまたは位置を再計算する必要がある物理アニメーションです。  
  
 **実装の説明**  
  
 この概要で説明されている他の方法とは異なり、フレームごとのコールバックを使うために、カスタム アニメーション クラスまたはカスタム キー フレーム クラスを作成する必要はありません。  
  
 代わりに、アニメーション化する<xref:System.Windows.Media.CompositionTarget.Rendering>オブジェクトを含むオブジェクトのイベントに登録します。 このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がビジュアル ツリーの永続化されたレンダリング データを構成ツリーにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。  
  
 イベント ハンドラーでは、アニメーション効果に必要なあらゆる計算を実行し、これらの値を使用してアニメーション化するオブジェクトのプロパティを設定します。  
  
 現在のフレームのプレゼンテーション時間を取得するには、この<xref:System.EventArgs>イベントに関連付けられた をとして<xref:System.Windows.Media.RenderingEventArgs>キャストして、現在<xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>のフレームのレンダリング時間を取得するために使用できるプロパティを提供します。  
  
 詳しくは、<xref:System.Windows.Media.CompositionTarget.Rendering> のページをご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [パス アニメーションの概要](path-animations-overview.md)
- [アニメーションの概要](animation-overview.md)
- [アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)
- [カスタム アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
