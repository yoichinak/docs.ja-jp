---
title: マルチメディアの概要
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: d4abf4d9fd324ffbf2737dc686c02e50ca1a8a5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181882"
---
# <a name="multimedia-overview"></a>マルチメディアの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のマルチメディア機能を使用してアプリケーションにオーディオとビデオを統合することで、ユーザー エクスペリエンスを向上させることできます。 このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のマルチメディア機能の概要を説明します。  

<a name="mediaapi"></a>
## <a name="media-api"></a>メディア API  
 <xref:System.Windows.Controls.MediaElement>クラスと<xref:System.Windows.Media.MediaPlayer>クラスは、オーディオまたはビデオコンテンツを表示するために使用されます。 これらのクラスは、対話式またはクロックで制御できます。 これらのクラスは、メディアの再生に使用できる Microsoft Windows メディア プレーヤー 10 コントロールです。 どちらのクラスを使用するかは、シナリオによって決まります。  
  
 <xref:System.Windows.Controls.MediaElement><xref:System.Windows.UIElement>は[Layout](../advanced/layout.md)でサポートされ、多くのコントロールのコンテンツとして使用できます。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でコードとして使用することもできます。 <xref:System.Windows.Media.MediaPlayer>一方、オブジェクト用<xref:System.Windows.Media.Drawing>に設計されており、レイアウトのサポートが不足しています。 を<xref:System.Windows.Media.MediaPlayer>使用してロードされたメディアは、 を<xref:System.Windows.Media.VideoDrawing>使用して表示するか、または<xref:System.Windows.Media.DrawingContext>を使用して直接対話することによってのみ表示できます。 <xref:System.Windows.Media.MediaPlayer>XAML では使用できません。  
  
 描画オブジェクトと描画コンテキストの詳細については、「[描画オブジェクトの概要](drawing-objects-overview.md)」を参照してください。  
  
> [!NOTE]
> アプリケーションでメディアを配布するときに、プロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
<a name="mediaplaybackmodes"></a>
## <a name="media-playback-modes"></a>メディア再生モード  
  
> [!NOTE]
> 両方<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaPlayer>同様のメンバーを持っています。 このセクションのリンクは、クラス<xref:System.Windows.Controls.MediaElement>メンバーを参照します。 特に注記がない限り、<xref:System.Windows.Controls.MediaElement>クラス内にリンクされているメンバーもクラス内<xref:System.Windows.Media.MediaPlayer>で見つけることができます。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのメディアの再生を理解するには、メディアを再生できる複数のモードを理解しておく必要があります。 両方<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaPlayer>2つの異なるメディアモード、独立モードとクロックモードで使用することができます。 メディア モードは、<xref:System.Windows.Controls.MediaElement.Clock%2A>プロパティによって決まります。 の<xref:System.Windows.Controls.MediaElement.Clock%2A>場合`null`、メディア オブジェクトは独立モードになります。 <xref:System.Windows.Controls.MediaElement.Clock%2A>が null 以外の場合、メディア オブジェクトはクロック モードです。 既定では、メディア オブジェクトは Independent モードになっています。  
  
### <a name="independent-mode"></a>Independent モード  
 Independent モードでは、メディア コンテンツがメディアの再生を行います。 Independent モードには、次のオプションがあります。  
  
- メディアは<xref:System.Uri>直接指定できます。  
  
- メディアの再生を直接制御できます。  
  
- メディア<xref:System.Windows.Controls.MediaElement.Position%2A>と<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>プロパティは変更できます。  
  
 メディアは、オブジェクトのプロパティを<xref:System.Windows.Controls.MediaElement>設定するか、<xref:System.Windows.Controls.MediaElement.Source%2A>オブジェクトの<xref:System.Windows.Media.MediaPlayer><xref:System.Windows.Media.MediaPlayer.Open%2A>メソッドを呼び出すことによって読み込まれます。  
  
 Independent モードでメディアの再生を制御するには、メディア オブジェクトの制御メソッドを使用できます。 使用できる制御メソッドは<xref:System.Windows.Controls.MediaElement.Play%2A><xref:System.Windows.Controls.MediaElement.Pause%2A>、 <xref:System.Windows.Controls.MediaElement.Close%2A>、 <xref:System.Windows.Controls.MediaElement.Stop%2A>、および です。 の<xref:System.Windows.Controls.MediaElement>場合、これらのメソッドを使用した対話型コントロールは、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>が<xref:System.Windows.Controls.MediaState.Manual>に設定されている場合にのみ使用できます。 メディア オブジェクトが Clock モードの場合、これらのメソッドは使用できません。  
  
 Independent モードの例については、「[MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)」を参照してください。  
  
### <a name="clock-mode"></a>Clock モード  
 クロックモードでは、メディア<xref:System.Windows.Media.MediaTimeline>の再生が行われます。 Clock モードには次の特徴があります。  
  
- メディアは<xref:System.Uri>間接的に を介して設定<xref:System.Windows.Media.MediaTimeline>されます。  
  
- メディアの再生は、クロックによって制御できます。 メディア オブジェクトの制御メソッドは使用できません。  
  
- メディアは、オブジェクトの<xref:System.Windows.Media.MediaTimeline><xref:System.Windows.Media.MediaTimeline.Source%2A>プロパティを設定し、タイムラインからクロックを作成し、メディア オブジェクトにクロックを割り当てることによってロードされます。 <xref:System.Windows.Media.MediaTimeline>メディアは、内部が<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Controls.MediaElement>.  
  
 クロックモードでメディアの再生を制御するには<xref:System.Windows.Media.Animation.ClockController>、制御メソッドを使用する必要があります。 A<xref:System.Windows.Media.Animation.ClockController>は の<xref:System.Windows.Media.Animation.ClockController>プロパティから取得<xref:System.Windows.Media.MediaClock>されます。 クロック モードで オブジェクトまたは<xref:System.Windows.Controls.MediaElement><xref:System.Windows.Media.MediaPlayer>オブジェクトのいずれかのコントロール メソッドを使用しようとすると、 が<xref:System.InvalidOperationException>スローされます。  
  
 クロックとタイムラインの詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。  
  
 Clock モードの例については、「[ストーリーボードを使用して MediaElement を制御する](how-to-control-a-mediaelement-by-using-a-storyboard.md)」を参照してください。  
  
<a name="mediaelement"></a>
## <a name="mediaelement-class"></a>MediaElement クラス  
 アプリケーションにメディアを追加する方法は、アプリケーション<xref:System.Windows.Controls.MediaElement>[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]にコントロールを追加し、含めるメディアに<xref:System.Uri>を提供するのと同じくらい簡単です。 でサポートされているすべてのメディアの種類をサポートしています[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。 次の例は、 の簡単な<xref:System.Windows.Controls.MediaElement>使用方法[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を示しています。  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 このサンプルでは、メディアは、読み込まれるとすぐに自動的に再生されます。 メディアの再生が終了すると、メディアが閉じられ、すべてのメディア リソースが解放されます (ビデオ メモリを含みます)。 これは<xref:System.Windows.Controls.MediaElement>、オブジェクトの既定の動作であり、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>プロパティ<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>によって制御されます。  
  
### <a name="controlling-a-mediaelement"></a>MediaElement の制御  
 プロパティ<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>と<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティは、 が<xref:System.Windows.Controls.MediaElement><xref:System.Windows.FrameworkElement.IsLoaded%2A>または`true``false`の動作をそれぞれ制御します。 この<xref:System.Windows.Controls.MediaState>プロパティは、メディアの再生動作に影響を与える設定です。 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>たとえば、デフォルト<xref:System.Windows.Controls.MediaState.Play>は<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A><xref:System.Windows.Controls.MediaState.Close>です。 これは、ロード<xref:System.Windows.Controls.MediaElement>されてプリロールが完了するとすぐにメディアの再生が開始されることを意味します。 再生が完了すると、メディアが閉じられ、すべてのメディア リソースが解放されます。  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>と プロパティは、メディアの再生を制御する唯一の方法<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>ではありません。 クロック モードでは、クロックが制御でき<xref:System.Windows.Controls.MediaElement>、対話式の制御メソッドは、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>が<xref:System.Windows.Controls.MediaState.Manual>を制御できます。 <xref:System.Windows.Controls.MediaElement>以下の優先順位を評価することにより、この競争の制御を処理します。  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. メディアがアンロードされているときに有効です。 これにより、 が に関連付けられている場合でも、すべてのメディア<xref:System.Windows.Media.MediaClock>リソースが既定<xref:System.Windows.Controls.MediaElement>で解放されます。  
  
2. <xref:System.Windows.Media.MediaClock>. メディアに<xref:System.Windows.Controls.MediaElement.Clock%2A>. メディアがアンロードされると、 が<xref:System.Windows.Media.MediaClock>の場合に限り、 <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>が有効になります。 クロック モードは常に、 の読<xref:System.Windows.Controls.MediaElement>み込まれた動作をオーバーライドします。  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. メディアが読み込まれているときに有効です。  
  
4. 対話型の制御メソッド。 の場合<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>は、<xref:System.Windows.Controls.MediaState.Manual>が所定の位置に配置されます。 使用できる制御メソッドは<xref:System.Windows.Controls.MediaElement.Play%2A><xref:System.Windows.Controls.MediaElement.Pause%2A>、 <xref:System.Windows.Controls.MediaElement.Close%2A>、 <xref:System.Windows.Controls.MediaElement.Stop%2A>、および です。  
  
### <a name="displaying-a-mediaelement"></a>MediaElement の表示  
 を<xref:System.Windows.Controls.MediaElement>表示するには、レンダリングするコンテンツが必要であり、コンテンツが読<xref:System.Windows.FrameworkElement.ActualWidth%2A>み<xref:System.Windows.FrameworkElement.ActualHeight%2A>込まれるまで、そのとプロパティは 0 に設定されます。 オーディオのみのコンテンツでは、これらのプロパティは常に 0 です。 ビデオ コンテンツの<xref:System.Windows.Controls.MediaElement.MediaOpened>場合、イベントが発生<xref:System.Windows.FrameworkElement.ActualWidth%2A>すると、読<xref:System.Windows.FrameworkElement.ActualHeight%2A>み込まれたメディアのサイズがレポートされます。 つまり、メディアがロード<xref:System.Windows.Controls.MediaElement>されるまで、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>プロパティが設定されていない限り、 の物理領域は使用されません。  
  
 プロパティと<xref:System.Windows.FrameworkElement.Width%2A>プロパティ<xref:System.Windows.FrameworkElement.Height%2A>の両方を設定すると、メディアが伸びて、 に<xref:System.Windows.Controls.MediaElement>指定された領域に収まりきります。 メディアの元の縦横比を維持するには、<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>プロパティを両方設定する必要がありますが、両方は設定しないでください。 プロパティと<xref:System.Windows.FrameworkElement.Width%2A>プロパティ<xref:System.Windows.FrameworkElement.Height%2A>の両方を設定すると、メディアは、望ましくない可能性がある固定要素サイズで表示されます。  
  
 要素のサイズが固定されることを避けるために、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、メディアをプリロールすることができます。 これは、 または のいずれかに<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A><xref:System.Windows.Controls.MediaState.Play>設定することによって行<xref:System.Windows.Controls.MediaState.Pause>われます。 <xref:System.Windows.Controls.MediaState.Pause>状態では、メディアがプリロールされ、最初のフレームが表示されます。 状態では<xref:System.Windows.Controls.MediaState.Play>、メディアがプリロールされ、再生を開始します。  
  
<a name="mediaplayer"></a>
## <a name="mediaplayer-class"></a>MediaPlayer クラス  
 クラスが<xref:System.Windows.Controls.MediaElement>フレームワーク要素である場合、<xref:System.Windows.Media.MediaPlayer>クラスはオブジェクトで<xref:System.Windows.Media.Drawing>使用するように設計されています。 描画オブジェクトは、フレームワーク レベルの機能を犠牲にしてパフォーマンスを向上させたり、<xref:System.Windows.Freezable>機能が必要な場合に使用します。 <xref:System.Windows.Media.MediaPlayer>を使用すると、アプリケーションでメディア コンテンツを提供しながら、これらの機能を利用できます。 Like <xref:System.Windows.Controls.MediaElement><xref:System.Windows.Media.MediaPlayer>は独立モードまたはクロック モードで使用できますが、<xref:System.Windows.Controls.MediaElement>オブジェクトのアンロード状態とロード済み状態はありません。 これにより、 の再生制御の複雑<xref:System.Windows.Media.MediaPlayer>さが軽減されます。  
  
### <a name="controlling-mediaplayer"></a>Media Player の制御  
 ステート<xref:System.Windows.Media.MediaPlayer>レスであるため、メディアの再生を制御する方法は 2 つしかありません。  
  
1. 対話型の制御メソッド。 独立モード (プロパティ)`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A>の場合に配置されます。  
  
2. <xref:System.Windows.Media.MediaClock>. メディアに<xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer の表示  
 技術的には、<xref:System.Windows.Media.MediaPlayer>物理的な表現がないため、表示できません。 ただし、<xref:System.Windows.Media.Drawing><xref:System.Windows.Media.VideoDrawing>クラスを使用してメディアを表示するために使用できます。 次の例では、 を<xref:System.Windows.Media.VideoDrawing>使用してメディアを表示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 オブジェクトの詳細については、「[図面オブジェクトの概要](drawing-objects-overview.md)」を参照してください。 <xref:System.Windows.Media.Drawing>  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.DrawingGroup>
- [レイアウト](../advanced/layout.md)
- [ハウツートピック](audio-and-video-how-to-topics.md)
