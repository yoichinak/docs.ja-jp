---
title: インク入力コントロールの作成
ms.date: 03/30/2017
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
ms.openlocfilehash: 329bad9d5e0fa24f66fbd63def4936cb047e62e3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378068"
---
# <a name="creating-an-ink-input-control"></a>インク入力コントロールの作成
できるカスタム コントロールを動的に作成し、静的にインクを描画します。 つまり、ユーザーが"flow"、タブレット ペンからおよびインクをその後に表示を追加するコントロールに、クリップボードから貼り付ける、タブレット ペンを使用していずれか、またはファイルから読み込まれたを表示するインク ストロークを描画するインクをレンダリングします。 インクを動的にレンダリングするコントロールを使用する必要があります、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>します。 静的にインクをレンダリングするには、スタイラス イベント メソッドをオーバーライドする必要があります (<xref:System.Windows.UIElement.OnStylusDown%2A>、 <xref:System.Windows.UIElement.OnStylusMove%2A>、および<xref:System.Windows.UIElement.OnStylusUp%2A>) を収集する<xref:System.Windows.Input.StylusPoint>データ、ストロークの作成に追加して、 <xref:System.Windows.Controls.InkPresenter> (このコントロールでインクを描画)。  
  
 このトピックは、次の内容で構成されています。  
  
-   [方法: スタイラス ポイントのデータを収集し、インク ストロークを作成します。](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [方法: マウスからの入力を受け入れるように、コントロールを有効にします。](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [これをまとめる](#PuttingItTogether)  
  
-   [追加のプラグインと DynamicRenderers を使用してください。](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [まとめ](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>方法: スタイラス ポイントのデータを収集し、インク ストロークを作成します。  
 ストロークを収集し、インクを管理するコントロールを作成するには、次の。  
  
1.  クラスを派生<xref:System.Windows.Controls.Control>から派生したクラスのいずれかまたは<xref:System.Windows.Controls.Control>など<xref:System.Windows.Controls.Label>します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  追加、<xref:System.Windows.Controls.InkPresenter>にクラスを設定し、<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティを新しい<xref:System.Windows.Controls.InkPresenter>します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  アタッチ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>の<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.Controls.InkPresenter>呼び出すことによって、<xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>メソッドを追加し、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクション。 これにより、<xref:System.Windows.Controls.InkPresenter>スタイラス ポイントのデータがコントロールによって収集されたインクを表示します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  <xref:System.Windows.UIElement.OnStylusDown%2A> メソッドをオーバーライドします。  このメソッドでの呼び出しでスタイラスのキャプチャ<xref:System.Windows.Input.Stylus.Capture%2A>します。 スタイラスをキャプチャすることで、コントロールが受信を続けるには<xref:System.Windows.UIElement.StylusMove>と<xref:System.Windows.UIElement.StylusUp>スタイラスがコントロールの境界から出た場合でもイベント。 これはありませんが、優れたユーザー エクスペリエンスのほとんどの場合に必要な厳密には必須です。 新規作成<xref:System.Windows.Input.StylusPointCollection>を収集する<xref:System.Windows.Input.StylusPoint>データ。 最後に、最初のセットを追加<xref:System.Windows.Input.StylusPoint>データを<xref:System.Windows.Input.StylusPointCollection>します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  上書き、<xref:System.Windows.UIElement.OnStylusMove%2A>メソッドを追加し、<xref:System.Windows.Input.StylusPoint>データを<xref:System.Windows.Input.StylusPointCollection>先ほど作成したオブジェクト。  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  上書き、<xref:System.Windows.UIElement.OnStylusUp%2A>メソッドされ、新しい作成<xref:System.Windows.Ink.Stroke>で、<xref:System.Windows.Input.StylusPointCollection>データ。 新しい追加<xref:System.Windows.Ink.Stroke>に作成した、<xref:System.Windows.Controls.InkPresenter.Strokes%2A>のコレクション、<xref:System.Windows.Controls.InkPresenter>およびスタイラスのキャプチャをリリースします。  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>方法: マウスからの入力を受け入れるように、コントロールを有効にします。  
 場合は、実行、およびマウスを使用して、入力デバイスとしてアプリケーションに前のコントロールを追加、ストロークは保持されませんが表示されます。 永続化するには、ストロークの入力デバイスとして、マウスを使用する場合、次の操作を行います。  
  
1.  上書き、<xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A>され、新しい作成<xref:System.Windows.Input.StylusPointCollection>イベントが発生したときに、マウスの位置を取得し、作成、<xref:System.Windows.Input.StylusPoint>ポイント データを使用して、追加、<xref:System.Windows.Input.StylusPoint>を<xref:System.Windows.Input.StylusPointCollection>します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  <xref:System.Windows.UIElement.OnMouseMove%2A> メソッドをオーバーライドします。 イベントが発生したときに、マウスの位置を取得し、作成、<xref:System.Windows.Input.StylusPoint>ポイント データを使用します。  追加、<xref:System.Windows.Input.StylusPoint>を<xref:System.Windows.Input.StylusPointCollection>先ほど作成したオブジェクト。  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> メソッドをオーバーライドします。  新規作成<xref:System.Windows.Ink.Stroke>で、<xref:System.Windows.Input.StylusPointCollection>データ、追加、新しい<xref:System.Windows.Ink.Stroke>に作成した、<xref:System.Windows.Controls.InkPresenter.Strokes%2A>のコレクション、<xref:System.Windows.Controls.InkPresenter>します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>これをまとめる  
 次の例では、ユーザーは、マウスやペンのいずれかで使用する場合は、インクを収集するカスタム コントロールです。  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>追加のプラグインと DynamicRenderers を使用してください。  
 カスタム コントロール、InkCanvas のようなカスタムを持つことができます<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>および追加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>オブジェクト。 これらを追加、<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクション。 順序、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>内のオブジェクト、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>レンダリングされるときに、インクの外観に影響します。 あるとします、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>と呼ばれる`dynamicRenderer`およびカスタム<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>と呼ばれる`translatePlugin`タブレット ペンのインクのオフセットです。 場合`translatePlugin`最初<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>で、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>と`dynamicRenderer`、2 つ目は、ユーザーは、ペンを移動すると、「フロー」インクが相殺されます。 場合`dynamicRenderer`が最初に、および`translatePlugin`インクいないユーザーはペンを持ち上げるまでがオフセットされるは、次に、します。  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>まとめ  
 収集し、スタイラス イベント メソッドをオーバーライドすることで、インクをレンダリングするコントロールを作成することができます。 独自のコントロールを作成すると、派生独自<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラス、および挿入しに<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>、デジタル インクの考えられるあらゆる動作を実装することができます。 アクセスがある、<xref:System.Windows.Input.StylusPoint>ほどデータの生成をカスタマイズする機会を与える<xref:System.Windows.Input.Stylus>入力し、それをアプリケーションに適したとして画面にレンダリングします。 このような低レベルのアクセス権があるため、<xref:System.Windows.Input.StylusPoint>データ、インクのコレクションを実装して、アプリケーションの最適なパフォーマンスでレンダリングします。  
  
## <a name="see-also"></a>関連項目
- [高度なインク処理](advanced-ink-handling.md)
- [アクセスして、ペン入力を操作します。](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
