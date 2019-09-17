---
title: マルチメディアの概要
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 44059fe96a0deeda18f0abd9079100b55be98e77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929618"
---
# <a name="multimedia-overview"></a>マルチメディアの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のマルチメディア機能を使用してアプリケーションにオーディオとビデオを統合することで、ユーザー エクスペリエンスを向上させることできます。 このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のマルチメディア機能の概要を説明します。  

<a name="mediaapi"></a>   
## <a name="media-api"></a>メディア API  
 クラス<xref:System.Windows.Controls.MediaElement> と<xref:System.Windows.Media.MediaPlayer>クラスは、オーディオまたはビデオのコンテンツを表示するために使用されます。 これらのクラスは、対話式またはクロックで制御できます。 これらのクラスは、メディアを再生するために [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 のコントロールで使用できます。 どちらのクラスを使用するかは、シナリオによって決まります。  
  
 <xref:System.Windows.Controls.MediaElement>は、[レイアウト](../advanced/layout.md)でサポートされ、多くのコントロールのコンテンツとして使用できるです。<xref:System.Windows.UIElement> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でコードとして使用することもできます。 <xref:System.Windows.Media.MediaPlayer>一方、はオブジェクト向け<xref:System.Windows.Media.Drawing>に設計されており、レイアウトはサポートされていません。 を使用して<xref:System.Windows.Media.MediaPlayer>読み込ま<xref:System.Windows.Media.DrawingContext>れたメディアを<xref:System.Windows.Media.VideoDrawing>表示するには、またはを直接操作する必要があります。 <xref:System.Windows.Media.MediaPlayer>は XAML では使用できません。  
  
 描画オブジェクトと描画コンテキストの詳細については、「[描画オブジェクトの概要](drawing-objects-overview.md)」を参照してください。  
  
> [!NOTE]
> アプリケーションでメディアを配布するときに、プロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>メディア再生モード  
  
> [!NOTE]
> と<xref:System.Windows.Controls.MediaElement> の<xref:System.Windows.Media.MediaPlayer>両方に同様のメンバーがあります。 このセクションのリンクでは、クラス<xref:System.Windows.Controls.MediaElement>のメンバーを参照しています。 特に明記されていない限り<xref:System.Windows.Controls.MediaElement> 、クラス内のにリンクさ<xref:System.Windows.Media.MediaPlayer>れたメンバーは、クラスでも検索できます。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのメディアの再生を理解するには、メディアを再生できる複数のモードを理解しておく必要があります。 <xref:System.Windows.Controls.MediaElement> と<xref:System.Windows.Media.MediaPlayer>はどちらも、独立モードとクロックモードの2つの異なるメディアモードで使用できます。 メディアモードは、 <xref:System.Windows.Controls.MediaElement.Clock%2A>プロパティによって決定されます。 <xref:System.Windows.Controls.MediaElement.Clock%2A> が`null`の場合、メディアオブジェクトは独立モードになります。 <xref:System.Windows.Controls.MediaElement.Clock%2A>が null 以外の場合、メディアオブジェクトはクロックモードになります。 既定では、メディア オブジェクトは Independent モードになっています。  
  
### <a name="independent-mode"></a>Independent モード  
 Independent モードでは、メディア コンテンツがメディアの再生を行います。 Independent モードには、次のオプションがあります。  
  
- <xref:System.Uri>メディアを直接指定することができます。  
  
- メディアの再生を直接制御できます。  
  
- メディアの<xref:System.Windows.Controls.MediaElement.Position%2A>プロパティ<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>とプロパティは変更できます。  
  
 メディア<xref:System.Windows.Controls.MediaElement>は、オブジェクトの<xref:System.Windows.Controls.MediaElement.Source%2A>プロパティを設定するか、 <xref:System.Windows.Media.MediaPlayer>オブジェクトの<xref:System.Windows.Media.MediaPlayer.Open%2A>メソッドを呼び出すことによって読み込まれます。  
  
 Independent モードでメディアの再生を制御するには、メディア オブジェクトの制御メソッドを使用できます。 使用できるコントロールメソッドは<xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A> <xref:System.Windows.Controls.MediaElement.Close%2A>、、、、 <xref:System.Windows.Controls.MediaElement.Stop%2A>およびです。 では<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>、これらのメソッドを使用した対話型コントロールは、がに設定されている場合にのみ使用できます。 <xref:System.Windows.Controls.MediaElement> メディア オブジェクトが Clock モードの場合、これらのメソッドは使用できません。  
  
 Independent モードの例については、「[MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)」を参照してください。  
  
### <a name="clock-mode"></a>Clock モード  
 クロックモードでは、 <xref:System.Windows.Media.MediaTimeline>メディアの再生がドライブによって再生されます。 Clock モードには次の特徴があります。  
  
- メディアは、を<xref:System.Windows.Media.MediaTimeline>通じて間接的に設定されます。 <xref:System.Uri>  
  
- メディアの再生は、クロックによって制御できます。 メディア オブジェクトの制御メソッドは使用できません。  
  
- メディアを読み込むには、 <xref:System.Windows.Media.MediaTimeline>オブジェクトの<xref:System.Windows.Media.MediaTimeline.Source%2A>プロパティを設定し、タイムラインからクロックを作成して、メディアオブジェクトにクロックを割り当てます。 内のが<xref:System.Windows.Media.MediaTimeline>を<xref:System.Windows.Controls.MediaElement>ターゲットとする場合も、メディアがこの方法で読み込まれます。 <xref:System.Windows.Media.Animation.Storyboard>  
  
 クロックモードでメディアの<xref:System.Windows.Media.Animation.ClockController>再生を制御するには、コントロールメソッドを使用する必要があります。 <xref:System.Windows.Media.Animation.ClockController>は、の<xref:System.Windows.Media.MediaClock>プロパティから取得<xref:System.Windows.Media.Animation.ClockController>されます。 クロックモード<xref:System.Windows.Controls.MediaElement> 中に<xref:System.Windows.Media.MediaPlayer>またはオブジェクトの制御メソッドを使用しようとすると、がスローされます。<xref:System.InvalidOperationException>  
  
 クロックとタイムラインの詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。  
  
 Clock モードの例については、「[ストーリーボードを使用して MediaElement を制御する](how-to-control-a-mediaelement-by-using-a-storyboard.md)」を参照してください。  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement クラス  
 アプリケーションにメディアを追加するのは、 <xref:System.Windows.Controls.MediaElement> [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]アプリケーションのにコントロールを追加し、含めるメディア<xref:System.Uri>にを指定するだけです。 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 でサポートされているすべてのメディアが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でもサポートされます。 次の例は、 <xref:System.Windows.Controls.MediaElement> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]のの簡単な使用方法を示しています。  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 このサンプルでは、メディアは、読み込まれるとすぐに自動的に再生されます。 メディアの再生が終了すると、メディアが閉じられ、すべてのメディア リソースが解放されます (ビデオ メモリを含みます)。 これは<xref:System.Windows.Controls.MediaElement>オブジェクトの既定の動作であり、プロパティ<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>および<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティによって制御されます。  
  
### <a name="controlling-a-mediaelement"></a>MediaElement の制御  
 <xref:System.Windows.FrameworkElement.IsLoaded%2A> <xref:System.Windows.Controls.MediaElement>プロパティ<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>とプロパティは`true` 、がまた`false`はである場合のの動作を制御します。 <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState>プロパティは、メディアの再生動作に影響を与えるように設定されています。 たとえば、既定<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>値は<xref:System.Windows.Controls.MediaState.Play>で、既定値<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Close>です。 これは、 <xref:System.Windows.Controls.MediaElement>が読み込まれ、プリロールが完了するとすぐに、メディアの再生が開始されることを意味します。 再生が完了すると、メディアが閉じられ、すべてのメディア リソースが解放されます。  
  
 プロパティ<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> と<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティは、メディアの再生を制御する唯一の方法ではありません。 クロックモードでは、時計はを制御<xref:System.Windows.Controls.MediaElement>できます。また、がの<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>場合は、 <xref:System.Windows.Controls.MediaState.Manual>対話型のコントロールメソッドによって制御されます。 <xref:System.Windows.Controls.MediaElement>は、次の優先順位を評価することで、このコンテストを制御対象として処理します。  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>。 メディアがアンロードされているときに有効です。 これにより、 <xref:System.Windows.Media.MediaClock>がに関連付けら<xref:System.Windows.Controls.MediaElement>れている場合でも、既定ですべてのメディアリソースが解放されます。  
  
2. <xref:System.Windows.Media.MediaClock>。 メディアにがある<xref:System.Windows.Controls.MediaElement.Clock%2A>場合に適用されます。 メディアがアンロード<xref:System.Windows.Media.MediaClock>されると、 <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>が<xref:System.Windows.Controls.MediaState.Manual>である限り、が有効になります。 クロックモードは、 <xref:System.Windows.Controls.MediaElement>常にの読み込み済みの動作よりも優先されます。  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>。 メディアが読み込まれているときに有効です。  
  
4. 対話型の制御メソッド。 がの場合<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Manual>、その場で。 使用できるコントロールメソッドは<xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A> <xref:System.Windows.Controls.MediaElement.Close%2A>、、、、 <xref:System.Windows.Controls.MediaElement.Stop%2A>およびです。  
  
### <a name="displaying-a-mediaelement"></a>MediaElement の表示  
 を表示する<xref:System.Windows.Controls.MediaElement>には、表示するコンテンツが必要です。 <xref:System.Windows.FrameworkElement.ActualWidth%2A>また、 <xref:System.Windows.FrameworkElement.ActualHeight%2A>コンテンツが読み込まれるまで、プロパティとプロパティが0に設定されます。 オーディオのみのコンテンツでは、これらのプロパティは常に 0 です。 ビデオコンテンツの場合、 <xref:System.Windows.Controls.MediaElement.MediaOpened>イベントが<xref:System.Windows.FrameworkElement.ActualWidth%2A>発生すると<xref:System.Windows.FrameworkElement.ActualHeight%2A> 、読み込まれたメディアのサイズがレポートされます。 つまり、 <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.FrameworkElement.Width%2A>また[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] は<xref:System.Windows.FrameworkElement.Height%2A>プロパティが設定されていない限り、は、メディアが読み込まれるまでの物理的な領域を占有しません。  
  
 プロパティとプロパティ<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.FrameworkElement.Height%2A>両方を設定すると、 <xref:System.Windows.Controls.MediaElement>メディアがによって拡大され、の領域がいっぱいになります。 メディアの元の縦横比を維持するには<xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> 、プロパティとプロパティのどちらか一方を設定する必要があります。 プロパティとプロパティ<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.FrameworkElement.Height%2A>両方を設定すると、メディアが固定の要素サイズで表示され、望ましくない場合があります。  
  
 要素のサイズが固定されることを避けるために、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、メディアをプリロールすることができます。 これを行うには、 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>を<xref:System.Windows.Controls.MediaState.Play>または<xref:System.Windows.Controls.MediaState.Pause>に設定します。 <xref:System.Windows.Controls.MediaState.Pause>状態では、メディアがプリロールされ、最初のフレームが表示されます。 <xref:System.Windows.Controls.MediaState.Play>状態では、メディアがプリロールされ、再生が開始されます。  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer クラス  
 <xref:System.Windows.Controls.MediaElement>クラスがフレームワーク要素の場合<xref:System.Windows.Media.MediaPlayer> 、クラスはオブジェクトで<xref:System.Windows.Media.Drawing>使用するように設計されています。 Drawing オブジェクトは、フレームワークレベルの機能を犠牲にしてパフォーマンスを向上させること<xref:System.Windows.Freezable>ができる場合や、機能が必要な場合に使用します。 <xref:System.Windows.Media.MediaPlayer>を使用すると、アプリケーションでメディアコンテンツを提供しながら、これらの機能を利用できます。 と<xref:System.Windows.Controls.MediaElement>同様<xref:System.Windows.Media.MediaPlayer>に、は独立モードまたはクロックモードで使用できます<xref:System.Windows.Controls.MediaElement>が、オブジェクトのアンロード状態と読み込み状態はありません。 これにより、 <xref:System.Windows.Media.MediaPlayer>の再生制御の複雑さが軽減されます。  
  
### <a name="controlling-mediaplayer"></a>Media Player の制御  
 は<xref:System.Windows.Media.MediaPlayer>ステートレスであるため、メディアの再生を制御する方法は2つだけです。  
  
1. 対話型の制御メソッド。 独立モード (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A>プロパティ) の場合。  
  
2. <xref:System.Windows.Media.MediaClock>。 メディアにがある<xref:System.Windows.Media.MediaPlayer.Clock%2A>場合に適用されます。  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer の表示  
 技術的には<xref:System.Windows.Media.MediaPlayer> 、物理的な表現がないため、を表示できません。 ただし、 <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.VideoDrawing>クラスを使用してでメディアを表示するために使用できます。 次の例は、を<xref:System.Windows.Media.VideoDrawing>使用してメディアを表示する方法を示しています。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <xref:System.Windows.Media.Drawing>オブジェクトの詳細については、「 [Drawing オブジェクトの概要](drawing-objects-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.DrawingGroup>
- [レイアウト](../advanced/layout.md)
- [方法トピック](audio-and-video-how-to-topics.md)
