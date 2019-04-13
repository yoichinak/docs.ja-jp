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
ms.openlocfilehash: 268d218097233aee795154226cc6f7c3ce318f5c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313945"
---
# <a name="custom-animations-overview"></a>カスタム アニメーションの概要
このトピックでは、カスタム キー フレームやアニメーション クラスを作成して、またはフレームごとのコールバックを使ってバイパスすることにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション システムを拡張する方法と、それが必要な状況について説明します。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって提供されるさまざまな種類のアニメーションに精通している必要があります。 詳しくは、「From/To/By アニメーションの概要」、「[キー フレーム アニメーションの概要](key-frame-animations-overview.md)」、および「[パス アニメーションの概要](path-animations-overview.md)」をご覧ください。  
  
 アニメーション クラスが継承するので、<xref:System.Windows.Freezable>クラス、知っておくべきで<xref:System.Windows.Freezable>から継承する方法とオブジェクト<xref:System.Windows.Freezable>します。 詳しくは、「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」をご覧ください。  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>アニメーション システムの拡張  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション システムには、使う組み込み機能のレベルに応じて、さまざまな拡張方法があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション エンジンには、次の 3 つの主な機能拡張ポイントがあります。  
  
-   いずれかから継承することによって、カスタム キー フレーム オブジェクトを作成、 *\<型 >* などのキーフレーム クラス<xref:System.Windows.Media.Animation.DoubleKeyFrame>します。 この方法では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション エンジンの組み込み機能のほとんどを使います。  
  
-   継承することによって、独自のアニメーション クラスを作成する<xref:System.Windows.Media.Animation.AnimationTimeline>またはのいずれか、 *\<型 >* AnimationBase クラス。  
  
-   フレームごとのコールバックを使って、フレームごとにアニメーションを生成します。 この方法は、アニメーションおよびタイミング システムを完全にバイパスします。  
  
 次の表では、いくつかのアニメーション システム拡張シナリオについて説明します。  
  
|目的...|使う方法|  
|-------------------------|-----------------------|  
|対応する *\<Type>* AnimationUsingKeyFrames がある型の値の間の補間をカスタマイズする|カスタム キー フレームを作成します。 詳しくは、「[カスタム キー フレームを作成する](#createacustomkeyframe)」セクションをご覧ください。|  
|対応する *\<Type>* Animation がある型の値の間の補間以外の部分もカスタマイズする|アニメーション化する型に対応する *\<Type>* AnimationBase クラスを継承するカスタム アニメーション クラスを作成します。 詳しくは、「[カスタム アニメーション クラスを作成する](#createacustomanimationtype)」セクションをご覧ください。|  
|対応する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーションがない型をアニメーション化する|使用して、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>から継承するクラスを作成または<xref:System.Windows.Media.Animation.AnimationTimeline>します。 詳しくは、「[カスタム アニメーション クラスを作成する](#createacustomanimationtype)」セクションをご覧ください。|  
|フレームごとに計算され、最後のオブジェクト相互作用セットに基づく値のある、複数のオブジェクトをアニメーション化する|フレームごとのコールバックを使います。 詳しくは、「[フレームごとのコールバックを使用する](#useperframecallback)」セクションをご覧ください。|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>カスタム キー フレームを作成する  
 カスタム キー フレーム クラスの作成は、アニメーション システムを拡張する最も簡単な方法です。 キー フレーム アニメーションに対して異なる補間方法が必要なときは、このアプローチを使います。  「[キー フレーム アニメーションの概要](key-frame-animations-overview.md)」で説明されているように、キー フレーム アニメーションはキー フレーム オブジェクトを使って出力値を生成します。 各キー フレーム オブジェクトは 3 つの機能を実行します。  
  
-   使用してターゲット値を指定します。 その<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>プロパティ。  
  
-   これでその値に到達するを使用して時間を指定します、<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>プロパティ。  
  
-   InterpolateValueCore メソッドを実装することで、前のキー フレームの値とそれ自体の値の間を補間します。  
  
 **実装の説明**  
  
 *\<Type>* KeyFrame 抽象クラスから派生して、InterpolateValueCore メソッドを実装します。 InterpolateValueCore メソッドは、キー フレームの現在の値を返します。 2 つのパラメーターとして、前のキー フレームの値と、0 から 1 の範囲の進行状況の値を受け取ります。 0 の進行状況は、キー フレームが開始され、値 1 には、キー フレームが完了したと、によって指定された値を返す必要がありますを示すことを示します。 その<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>プロパティ。  
  
 *\<型 >* キーフレーム クラスから継承、<xref:System.Windows.Freezable>クラスもオーバーライドする必要あります<xref:System.Windows.Freezable.CreateInstanceCore%2A>core クラスの新しいインスタンスを返します。 クラスが依存関係プロパティを使ってデータを保存しない場合、または作成の後で追加の初期化が必要な場合は、他のメソッドのオーバーライドが必要な場合があります。詳しくは、「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」をご覧ください。  
  
 カスタム *\<Type>* KeyFrame アニメーションを作成した後は、その型の *\<Type>* AnimationUsingKeyFrames でそれを使うことができます。  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>カスタム アニメーション クラスを作成する  
 独自のアニメーション型を作成すると、オブジェクトをアニメーション化する方法をいっそう細かく制御できます。 独自のアニメーションの種類を作成する 2 つの推奨される方法があります: から派生させることができます、<xref:System.Windows.Media.Animation.AnimationTimeline>クラスまたは*\<型 >* AnimationBase クラス。 *\<Type>* Animation クラスまたは *\<Type>* AnimationUsingKeyFrames クラスからの派生は推奨されません。  
  
### <a name="derive-from-typeanimationbase"></a>\<Type>AnimationBase から派生する  
 *\<Type>* AnimationBase クラスからの派生は、新しいアニメーション型を作成する最も簡単な方法です。 対応する *\<Type>* AnimationBase クラスが既にある型の新しいアニメーションを作成する場合は、この方法を使います。  
  
 **実装の説明**  
  
 *\<Type>* Animation から派生して、GetCurrentValueCore メソッドを実装します。 GetCurrentValueCore メソッドは、アニメーションの現在の値を返します。 次の 3 つのパラメーターを受け取ります: 推奨される開始値、推奨される終了値、および<xref:System.Windows.Media.Animation.AnimationClock>アニメーションの進行状況を判断するために使用します。  
  
 *\<型 >* AnimationBase クラスから継承、<xref:System.Windows.Freezable>クラスもオーバーライドする必要あります<xref:System.Windows.Freezable.CreateInstanceCore%2A>core クラスの新しいインスタンスを返します。 クラスが依存関係プロパティを使ってデータを保存しない場合、または作成の後で追加の初期化が必要な場合は、他のメソッドのオーバーライドが必要な場合があります。詳しくは、「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」をご覧ください。  
  
 詳しくは、アニメーション化する型の *\<Type>* AnimationBase クラスの GetCurrentValueCore メソッドのドキュメントをご覧ください。 例については、「[Custom Animation Sample](https://go.microsoft.com/fwlink/?LinkID=159981)」(カスタム アニメーションのサンプル) をご覧ください。  
  
 **別の方法**  
  
 アニメーション値を補間する方法を変更したいだけの場合は、いずれかの *\<Type>* KeyFrame クラスからの派生を検討します。 作成したキー フレームを、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって提供される対応する *\<Type>* AnimationUsingKeyFrames で使うことができます。  
  
### <a name="derive-from-animationtimeline"></a>AnimationTimeline から派生する  
 派生、<xref:System.Windows.Media.Animation.AnimationTimeline>クラスを一致するまだ持たない型のアニメーションを作成するときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーション、または厳密に型指定されていないアニメーションを作成します。  
  
 **実装の説明**  
  
 派生、<xref:System.Windows.Media.Animation.AnimationTimeline>クラスし、次のメンバーをオーバーライドします。  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A> – オーバーライドする必要があります新しいクラスが具象の場合、<xref:System.Windows.Freezable.CreateInstanceCore%2A>クラスの新しいインスタンスを返します。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – アニメーションの現在の値を返すには、このメソッドをオーバーライドします。 3 つのパラメーターを受け取ります。 既定値は配信元、変換先の既定値では、および<xref:System.Windows.Media.Animation.AnimationClock>。 使用して、<xref:System.Windows.Media.Animation.AnimationClock>を現在の時刻またはアニメーションの進行状況を取得します。 既定の開始値と終了値を使うかどうかを選択できます。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – アニメーションがで指定された既定の終了値を使用するかどうかを指定するには、このプロパティのオーバーライド、<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>メソッド。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – かを示すには、このプロパティのオーバーライド、<xref:System.Type>出力のアニメーションが生成されます。  
  
 クラスが依存関係プロパティを使ってデータを保存しない場合、または作成の後で追加の初期化が必要な場合は、他のメソッドのオーバーライドが必要な場合があります。詳しくは、「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」をご覧ください。  
  
 推奨される ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーションによって使われる) パラダイムは、2 つの継承レベルを使うことです。  
  
1. 作成する抽象*\<型 >* AnimationBase クラスから派生した<xref:System.Windows.Media.Animation.AnimationTimeline>します。 このクラスをオーバーライドする必要があります、<xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>メソッド。 また新しい抽象メソッド GetCurrentValueCore を導入し、オーバーライドする必要があります<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>GetCurrentValueCore を呼び出すし、既定の配信元の値と既定の宛先値パラメーターの型を検証します。  
  
2. 継承する別のクラスを作成から、新しい*\<型 >* AnimationBase クラスをオーバーライドし、<xref:System.Windows.Freezable.CreateInstanceCore%2A>メソッド、導入した GetCurrentValueCore メソッド、<xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>プロパティ。  
  
 **別の方法**  
  
 対応するによって/アニメーションまたはキー フレーム アニメーションを持たない型をアニメーション化する場合は、使用を検討して、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>します。 これは弱い型付けであるため、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>あらゆる種類の値をアニメーション化することができます。 このアプローチの欠点は<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>離散補間のみをサポートします。  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>フレームごとのコールバックを使用する  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション システムを完全にバイパスする必要があるときは、この方法を使います。 この方法の 1 つのシナリオは、各アニメーション ステップでオブジェクトの最後の一連のやり取りに基づいてアニメーション化されるオブジェクトの新しい向きまたは位置を再計算する必要がある物理アニメーションです。  
  
 **実装の説明**  
  
 この概要で説明されている他の方法とは異なり、フレームごとのコールバックを使うために、カスタム アニメーション クラスまたはカスタム キー フレーム クラスを作成する必要はありません。  
  
 代わりに、登録、<xref:System.Windows.Media.CompositionTarget.Rendering>をアニメーション化するオブジェクトを含むオブジェクトのイベント。 このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がビジュアル ツリーの永続化されたレンダリング データを構成ツリーにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。  
  
 イベント ハンドラーでは、アニメーション効果に必要なあらゆる計算を実行し、これらの値を使用してアニメーション化するオブジェクトのプロパティを設定します。  
  
 現在のフレームの表現時間を取得する、<xref:System.EventArgs>これに関連付けられているイベントとしてキャストできます<xref:System.Windows.Media.RenderingEventArgs>、提供、<xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>現在のフレームを取得するのに使用できるプロパティの表示時間。  
  
 詳細については、次を参照してください。、<xref:System.Windows.Media.CompositionTarget.Rendering>ページ。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [パス アニメーションの概要](path-animations-overview.md)
- [アニメーションの概要](animation-overview.md)
- [アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)
- [カスタム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=159981)
