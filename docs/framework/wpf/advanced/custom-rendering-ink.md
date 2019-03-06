---
title: カスタム レンダリング インク
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: ce4c2bd48e819541d942c795307df36629ec05b9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362631"
---
# <a name="custom-rendering-ink"></a>カスタム レンダリング インク
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>ストロークのプロパティでは、そのサイズ、色、および図形など、ストロークの外観を指定することができますが、どのような外観のカスタマイズにする時間がある可能性があります<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>を許可します。 エアブラシ、油絵、およびその他の多くの効果の外観でレンダリングすることで、インクの外観をカスタマイズしたい場合もあります。 Windows Presentation Foundation (WPF) により、カスタム実装することでインクをレンダリングするカスタム<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>と<xref:System.Windows.Ink.Stroke>オブジェクト。  
  
 このトピックは、次の内容で構成されています。  
  
-   [アーキテクチャ](#Architecture)  
  
-   [動的なレンダラーの実装](#ImplementingADynamicRenderer)  
  
-   [カスタム ストロークの実装](#ImplementingCustomStrokes)  
  
-   [カスタム InkCanvas の実装](#ImplementingACustomInkCanvas)  
  
-   [まとめ](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>アーキテクチャ  
 インク レンダリングは 2 回発生します。ユーザーがインクを手描き入力サーフェイスに書き込む時と、ストロークが手書き対応のサーフェスに追加された後です。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 、ユーザーは、デジタイザー上でタブレット ペンを移動すると、インクをレンダリングおよび<xref:System.Windows.Ink.Stroke>要素に追加された後に、自身をレンダリングします。  
  
 インクを動的にレンダリングするときに実装する 3 つのクラスがあります。  
  
1.  **DynamicRenderer**:<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> から派生するクラスを実装します。 このクラスは、特殊な<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>ストロークをレンダリングするように描画されます。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>別のスレッドでレンダリングは、アプリケーションのユーザー インターフェイス (UI) スレッドがブロックされている場合でも、インクを収集する手描き入力サーフェスが表示されるようにします。 スレッド処理モデルの詳細については、「[インク スレッド モデル](the-ink-threading-model.md)」を参照してください。 ストロークを動的にレンダリングをカスタマイズするには、オーバーライド、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>メソッド。  
  
2.  **ストローク**:<xref:System.Windows.Ink.Stroke> から派生するクラスを実装します。 このクラスの静的なレンダリングは、<xref:System.Windows.Input.StylusPoint>データに変換された後、<xref:System.Windows.Ink.Stroke>オブジェクト。 上書き、<xref:System.Windows.Ink.Stroke.DrawCore%2A>ストロークの静的なレンダリングはそのことを確認するメソッドが動的レンダリングと一致します。  
  
3.  **InkCanvas:**<xref:System.Windows.Controls.InkCanvas> から派生するクラスを実装します。 カスタマイズされた割り当てる<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>プロパティ。 上書き、<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>メソッドにカスタム ストロークを追加し、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>プロパティ。 これにより、インクの外観に一貫性を確保します。  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>動的なレンダラーの実装  
 ただし、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>クラスは、標準の一部の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、特殊なレンダリングを実行の詳細から派生したカスタマイズされた動的なレンダラーを作成する必要があります、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>をオーバーライドし、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>メソッド。  
  
 次の例で、カスタマイズされた<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>インク線状グラデーション ブラシの効果を描画します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>カスタム ストロークの実装  
 
  <xref:System.Windows.Ink.Stroke> から派生するクラスを実装します。 このクラスはレンダリング<xref:System.Windows.Input.StylusPoint>データに変換された後、<xref:System.Windows.Ink.Stroke>オブジェクト。 上書き、<xref:System.Windows.Ink.Stroke.DrawCore%2A>実際の描画を実行するためにします。  
  
 Stroke クラスを使用してカスタム データを格納できますも、<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>メソッド。 このデータは、保持されるときにストローク データと共に格納されます。  
  
 <xref:System.Windows.Ink.Stroke>クラスは、ヒット テストも実行できます。 独自のヒットをオーバーライドすることでテスト アルゴリズムを実装することも、<xref:System.Windows.Ink.Stroke.HitTest%2A>現在クラスのメソッド。  
  
 次C#例では、カスタム<xref:System.Windows.Ink.Stroke>レンダリング クラス<xref:System.Windows.Input.StylusPoint>を 3d ストロークとしてデータ。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>カスタム InkCanvas の実装  
 カスタマイズされたを使用する最も簡単な方法<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ストロークがから派生したクラスを実装するために、<xref:System.Windows.Controls.InkCanvas>し、これらのクラスを使用します。 <xref:System.Windows.Controls.InkCanvas>が、<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>ユーザーが描画するときにストロークをレンダリングする方法を指定するプロパティ。  
  
 カスタムのストロークをレンダリングする<xref:System.Windows.Controls.InkCanvas>次の操作します。  
  
-   派生するクラスを作成、<xref:System.Windows.Controls.InkCanvas>します。  
  
-   カスタマイズした割り当てる<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>プロパティ。  
  
-   <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> メソッドをオーバーライドします。 このメソッドで、InkCanvas に追加された元のストロークを削除します。 カスタム ストロークを作成し、追加、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>プロパティ、および呼び出しで新しい基底クラス<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>カスタム ストロークを格納しています。  
  
 次C#コード カスタム<xref:System.Windows.Controls.InkCanvas>、カスタマイズされたを使用するクラス<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>カスタム ストロークを収集します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas>は複数のいずれかに<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>します。 複数を追加する<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>オブジェクトを<xref:System.Windows.Controls.InkCanvas>に追加して、<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティ。  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>まとめ  
 インクの外観をカスタマイズするには、独自の派生によって<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、 <xref:System.Windows.Ink.Stroke>、および<xref:System.Windows.Controls.InkCanvas>クラス。 これらのクラスを合わせて、ユーザーがストロークを描画し、その後ストロークが収集される際に、ストロークの外観を一致させます。  
  
## <a name="see-also"></a>関連項目
- [高度なインク処理](advanced-ink-handling.md)
