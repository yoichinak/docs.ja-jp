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
ms.openlocfilehash: 394318488b0afb8e043389e0abc3f51dce8604c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186292"
---
# <a name="creating-an-ink-input-control"></a>インク入力コントロールの作成
インクを動的および静的にレンダリングするカスタム コントロールを作成できます。 つまり、ユーザーがストロークを描画すると、インクがタブレット ペンから "フロー" したように見え、コントロールに追加された後にインクを表示します。(タブレット ペンを使用して、クリップボードから貼り付けるか、またはファイルから読み込む)。 インクを動的にレンダリングするには、コントロールで<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. インクを静的にレンダリングするには、スタイラス イベント メソッド (<xref:System.Windows.UIElement.OnStylusDown%2A> <xref:System.Windows.UIElement.OnStylusMove%2A>、、<xref:System.Windows.UIElement.OnStylusUp%2A>および )<xref:System.Windows.Input.StylusPoint>をオーバーライドしてデータを収集し、ストローク<xref:System.Windows.Controls.InkPresenter>を作成し、 に追加する必要があります (コントロールにインクをレンダリングします)。  
  
 このトピックは、次の内容で構成されています。  
  
- [方法 : スタイラス ポイント データを収集し、インク ストロークを作成する](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [方法 : コントロールがマウスからの入力を受け入れるようにする](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [まとめる](#PuttingItTogether)  
  
- [追加のプラグインとダイナミックレンダラーの使用](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [結論](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>方法 : スタイラス ポイント データを収集し、インク ストロークを作成する  
 インク ストロークを収集および管理するコントロールを作成するには、次の操作を行います。  
  
1. から<xref:System.Windows.Controls.Control>クラスを派生させるか<xref:System.Windows.Controls.Control>、 などの<xref:System.Windows.Controls.Label>派生クラスの 1 つ。  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. クラスに<xref:System.Windows.Controls.InkPresenter>を追加し、プロパティ<xref:System.Windows.Controls.ContentControl.Content%2A>を新しい<xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. メソッドを<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呼<xref:System.Windows.Controls.InkPresenter>び出<xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>して に の をアタッチし<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、<xref:System.Windows.UIElement.StylusPlugIns%2A>をコレクションに追加します。 これにより、<xref:System.Windows.Controls.InkPresenter>スタイラス ポイント データがコントロールによって収集されたとおりにインクを表示できます。  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. <xref:System.Windows.UIElement.OnStylusDown%2A> メソッドをオーバーライドします。  このメソッドでは、スタイラスを呼び出しで<xref:System.Windows.Input.Stylus.Capture%2A>キャプチャします。 スタイラスをキャプチャすることで、スタイラスがコントロールの境界から<xref:System.Windows.UIElement.StylusMove>離<xref:System.Windows.UIElement.StylusUp>れた場合でも、コントロールは引き続きイベントを受け取ります。 これは厳密には必須ではありませんが、ほとんどの場合、優れたユーザー エクスペリエンスを実現するために必要です。 データを収集<xref:System.Windows.Input.StylusPointCollection><xref:System.Windows.Input.StylusPoint>する新しいを作成します。 最後に、データの<xref:System.Windows.Input.StylusPoint>初期セットを に<xref:System.Windows.Input.StylusPointCollection>追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. メソッドを<xref:System.Windows.UIElement.OnStylusMove%2A>オーバーライドし、先<xref:System.Windows.Input.StylusPoint>ほど作成した<xref:System.Windows.Input.StylusPointCollection>オブジェクトにデータを追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. メソッドを<xref:System.Windows.UIElement.OnStylusUp%2A>オーバーライドし、データを<xref:System.Windows.Ink.Stroke>使用して<xref:System.Windows.Input.StylusPointCollection>新しいメソッドを作成します。 スタイラス<xref:System.Windows.Ink.Stroke>キャプチャの<xref:System.Windows.Controls.InkPresenter.Strokes%2A>コレクションに作成した<xref:System.Windows.Controls.InkPresenter>新しいを追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>方法 : コントロールがマウスからの入力を受け入れるようにする  
 上記のコントロールをアプリケーションに追加し、それを実行し、マウスを入力デバイスとして使用すると、ストロークが保持されないことに気付きます。 入力デバイスとしてマウスが使用されているときにストロークを保持するには、次の操作を行います。  
  
1. をオーバーライド<xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A>して<xref:System.Windows.Input.StylusPointCollection>新しいを作成 イベントが発生したときにマウスの位置を取得し、ポイント<xref:System.Windows.Input.StylusPoint>データを使用して を<xref:System.Windows.Input.StylusPoint>作成し<xref:System.Windows.Input.StylusPointCollection>、 に を追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. <xref:System.Windows.UIElement.OnMouseMove%2A> メソッドをオーバーライドします。 イベントが発生したときのマウスの位置を取得し、ポイント<xref:System.Windows.Input.StylusPoint>データを使用してを作成します。  前<xref:System.Windows.Input.StylusPoint>に作成した<xref:System.Windows.Input.StylusPointCollection>オブジェクトに を追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> メソッドをオーバーライドします。  データを使用<xref:System.Windows.Ink.Stroke>して<xref:System.Windows.Input.StylusPointCollection>新しいを作成し、作成<xref:System.Windows.Ink.Stroke>した新しいを<xref:System.Windows.Controls.InkPresenter.Strokes%2A>のコレクション<xref:System.Windows.Controls.InkPresenter>に追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>
## <a name="putting-it-together"></a>まとめる  
 次の例は、ユーザーがマウスまたはペンを使用したときにインクを収集するカスタム コントロールです。  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>追加のプラグインとダイナミックレンダラーの使用  
 InkCanvas と同様に、カスタム コントロールにも<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>カスタム<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>オブジェクトや追加オブジェクトを含めることができます。 これらをコレクションに<xref:System.Windows.UIElement.StylusPlugIns%2A>追加します。 内のオブジェクトの<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>順序は、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>レンダリング時のインクの外観に影響します。 タブレット ペンから<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>インク`dynamicRenderer`をオフセットする<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>呼`translatePlugin`び出しと、呼び出されたカスタムを持っているとします。 が`translatePlugin`の最初<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>の<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>場合、2`dynamicRenderer`番目のインクは、ユーザーがペンを移動すると"フロー"するインクがオフセットされます。 最初`dynamicRenderer`の場合、2`translatePlugin`番目の場合、ユーザーがペンを持ち上げるまでインクはオフセットされません。  
  
<a name="AdvancedInkHandling_Conclusion"></a>
## <a name="conclusion"></a>まとめ  
 スタイラス イベント メソッドをオーバーライドしてインクを収集およびレンダリングするコントロールを作成できます。 独自のコントロールを作成し、独自<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>のクラスを派生させ、 に<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>挿入することで、デジタル インクで想像できるあらゆる動作を実装できます。 生成された<xref:System.Windows.Input.StylusPoint>データにアクセスして、アプリケーションに合わせて入力をカスタマイズ<xref:System.Windows.Input.Stylus>して画面に表示できます。 <xref:System.Windows.Input.StylusPoint>データへの低レベルのアクセスが可能なため、インク コレクションを実装し、アプリケーションに最適なパフォーマンスでレンダリングできます。  
  
## <a name="see-also"></a>関連項目

- [高度なインク処理](advanced-ink-handling.md)
- [ペン入力へのアクセスと操作](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
