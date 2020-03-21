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
ms.openlocfilehash: 0ceb831057a9a92aa7319d2004f04d7cf5ac820e
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111830"
---
# <a name="custom-rendering-ink"></a>カスタム レンダリング インク
ストローク<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>のプロパティを使用すると、ストロークのサイズ、色、形状などの外観を指定できますが、許可を超えて<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>外観をカスタマイズする必要がある場合があります。 エアブラシ、油絵、およびその他の多くの効果の外観でレンダリングすることで、インクの外観をカスタマイズしたい場合もあります。 Windows プレゼンテーションファンデーション (WPF) では、カスタムおよび<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer><xref:System.Windows.Ink.Stroke>オブジェクトを実装することで、インクをカスタム レンダリングできます。  
  
 このトピックは、次の内容で構成されています。  
  
- [アーキテクチャ](#Architecture)  
  
- [動的なレンダラーの実装](#ImplementingADynamicRenderer)  
  
- [カスタム ストロークの実装](#ImplementingCustomStrokes)  
  
- [カスタム InkCanvas の実装](#ImplementingACustomInkCanvas)  
  
- [結論](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Architecture  
 インク レンダリングは 2 回発生します。ユーザーがインクを手描き入力サーフェイスに書き込む時と、ストロークが手書き対応のサーフェスに追加された後です。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ユーザーがデジタイザー上でタブレット ペンを移動するとインクが<xref:System.Windows.Ink.Stroke>レンダリングされ、要素に追加されるとインクが描画されます。  
  
 インクを動的にレンダリングするときに実装する 3 つのクラスがあります。  
  
1. **動的レンダリング**: から派生するクラスを実装<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>します。 このクラスは、描画時<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>にストロークをレンダリングする特殊なクラスです。 は<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、別のスレッドでレンダリングを行うので、アプリケーションのユーザー インターフェイス (UI) スレッドがブロックされている場合でもインクを収集するように見えるインク サーフェスです。 スレッド処理モデルの詳細については、「[インク スレッド モデル](the-ink-threading-model.md)」を参照してください。 ストロークの動的レンダリングをカスタマイズするには、メソッドを<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>オーバーライドします。  
  
2. **ストローク**: から派生するクラスを<xref:System.Windows.Ink.Stroke>実装します。 このクラスは、オブジェクトに変換された後<xref:System.Windows.Input.StylusPoint>のデータの静的なレンダリングを<xref:System.Windows.Ink.Stroke>行います。 ストロークの<xref:System.Windows.Ink.Stroke.DrawCore%2A>静的レンダリングが動的レンダリングと一致するようにメソッドをオーバーライドします。  
  
3. **インクキャンバス:** から<xref:System.Windows.Controls.InkCanvas>派生するクラスを実装します。 カスタマイズした<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>プロパティを<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>割り当てます。 メソッドを<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>オーバーライドし、プロパティにカスタム ストローク<xref:System.Windows.Controls.InkCanvas.Strokes%2A>を追加します。 これにより、インクの外観に一貫性を確保します。  
  
<a name="ImplementingADynamicRenderer"></a>
## <a name="implementing-a-dynamic-renderer"></a>動的なレンダラーの実装  
 クラスは の標準部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ですが、より特殊なレンダリングを実行するには、 メソッドから派生<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>し、メソッドをオーバーライドするカスタマイズされた動的レンダラーを<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>作成する必要があります。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>  
  
 線形グラデーション ブラシ効果を使用して<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>インクを描画するカスタマイズされた例を次に示します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>
## <a name="implementing-custom-strokes"></a>カスタム ストロークの実装  
 <xref:System.Windows.Ink.Stroke> から派生するクラスを実装します。 このクラスは、オブジェクトに<xref:System.Windows.Input.StylusPoint>変換された後にデータをレンダリングします<xref:System.Windows.Ink.Stroke>。 実際の<xref:System.Windows.Ink.Stroke.DrawCore%2A>描画を行うには、クラスをオーバーライドします。  
  
 Stroke クラスは、メソッドを使用してカスタム<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>データを格納することもできます。 このデータは、保持されるときにストローク データと共に格納されます。  
  
 また<xref:System.Windows.Ink.Stroke>、このクラスはヒット テストを実行することもできます。 また、現在のクラスのメソッドをオーバーライドして、独自の<xref:System.Windows.Ink.Stroke.HitTest%2A>ヒット テスト アルゴリズムを実装することもできます。  
  
 次の C# コードは、<xref:System.Windows.Ink.Stroke>データを 3D ストロークとしてレンダリングする<xref:System.Windows.Input.StylusPoint>カスタム クラスを示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>
## <a name="implementing-a-custom-inkcanvas"></a>カスタム InkCanvas の実装  
 カスタマイズおよび<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ストロークを使用する最も簡単な方法は、これらのクラスから<xref:System.Windows.Controls.InkCanvas>派生して使用するクラスを実装することです。 には<xref:System.Windows.Controls.InkCanvas>、<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>ユーザーが描画するときにストロークをレンダリングする方法を指定するプロパティがあります。  
  
 カスタム レンダー ストロークを<xref:System.Windows.Controls.InkCanvas>次の操作にします。  
  
- から派生するクラスを作成します<xref:System.Windows.Controls.InkCanvas>。  
  
- カスタマイズした<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>プロパティを<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>割り当てます。  
  
- <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> メソッドをオーバーライドします。 このメソッドで、InkCanvas に追加された元のストロークを削除します。 次に、カスタム ストロークを作成し、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>プロパティに追加し、カスタム ストロークを含<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>む新しい基本クラスを呼び出します。  
  
 次の C# コードは、<xref:System.Windows.Controls.InkCanvas>カスタマイズされた<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ストロークを使用してカスタム ストロークを収集するカスタム クラスを示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 複数<xref:System.Windows.Controls.InkCanvas>の<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を持つことができます。 プロパティに追加することで<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、複数の<xref:System.Windows.Controls.InkCanvas>オブジェクトを<xref:System.Windows.UIElement.StylusPlugIns%2A>に追加できます。  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>まとめ  
 インクの外観は、独自<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>の 、 、<xref:System.Windows.Ink.Stroke>および<xref:System.Windows.Controls.InkCanvas>クラスを派生させることによってカスタマイズできます。 これらのクラスを合わせて、ユーザーがストロークを描画し、その後ストロークが収集される際に、ストロークの外観を一致させます。  
  
## <a name="see-also"></a>関連項目

- [高度なインク処理](advanced-ink-handling.md)
