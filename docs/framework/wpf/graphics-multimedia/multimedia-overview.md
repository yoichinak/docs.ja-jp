---
title: マルチメディアの概要
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 66cb28fce9485898711b9029baf8a17dd9b2c011
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340491"
---
# <a name="multimedia-overview"></a>マルチメディアの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のマルチメディア機能を使用してアプリケーションにオーディオとビデオを統合することで、ユーザー エクスペリエンスを向上させることできます。 このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のマルチメディア機能の概要を説明します。  

<a name="mediaapi"></a>   
## <a name="media-api"></a>メディア API  
 <xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaPlayer>クラスを使用すると、オーディオまたはビデオのコンテンツを表示します。 これらのクラスは、対話式またはクロックで制御できます。 これらのクラスは、メディアを再生するために [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 のコントロールで使用できます。 どちらのクラスを使用するかは、シナリオによって決まります。  
  
 <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.UIElement>でサポートされている、[レイアウト](../advanced/layout.md)と多くのコントロールのコンテンツとして使用できます。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でコードとして使用することもできます。 <xref:System.Windows.Media.MediaPlayer>での設計は、その一方で、<xref:System.Windows.Media.Drawing>オブジェクトし、レイアウトはサポートされていません。 使用して読み込まれたメディア、<xref:System.Windows.Media.MediaPlayer>使用して表示することができますのみ、<xref:System.Windows.Media.VideoDrawing>または直接やり取りすることによって、<xref:System.Windows.Media.DrawingContext>します。 <xref:System.Windows.Media.MediaPlayer> XAML では使用できません。  
  
 描画オブジェクトと描画コンテキストの詳細については、「[描画オブジェクトの概要](drawing-objects-overview.md)」を参照してください。  
  
> [!NOTE]
>  アプリケーションでメディアを配布するときに、プロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>メディア再生モード  
  
> [!NOTE]
>  両方<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaPlayer>のようなメンバーが存在します。 このセクションのリンクを参照してください、<xref:System.Windows.Controls.MediaElement>クラスのメンバー。 メンバーがリンクで、具体的には記載されていない場合、<xref:System.Windows.Controls.MediaElement>クラスも記されて、<xref:System.Windows.Media.MediaPlayer>クラス。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのメディアの再生を理解するには、メディアを再生できる複数のモードを理解しておく必要があります。 両方<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaPlayer>2 つの異なるメディア モード、independent モードと clock モードで使用できます。 メディア モードによって決まります、<xref:System.Windows.Controls.MediaElement.Clock%2A>プロパティ。 ときに<xref:System.Windows.Controls.MediaElement.Clock%2A>は`null`、メディア オブジェクトは independent モードにします。 ときに、<xref:System.Windows.Controls.MediaElement.Clock%2A>が null 以外の場合、メディア オブジェクトは clock モードにします。 既定では、メディア オブジェクトは Independent モードになっています。  
  
### <a name="independent-mode"></a>Independent モード  
 Independent モードでは、メディア コンテンツがメディアの再生を行います。 Independent モードには、次のオプションがあります。  
  
-   メディアの<xref:System.Uri>直接指定することができます。  
  
-   メディアの再生を直接制御できます。  
  
-   メディアの<xref:System.Windows.Controls.MediaElement.Position%2A>と<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>プロパティを変更できます。  
  
 いずれかの設定によってメディアが読み込まれる、<xref:System.Windows.Controls.MediaElement>オブジェクトの<xref:System.Windows.Controls.MediaElement.Source%2A>プロパティまたは呼び出すことによって、<xref:System.Windows.Media.MediaPlayer>オブジェクトの<xref:System.Windows.Media.MediaPlayer.Open%2A>メソッド。  
  
 Independent モードでメディアの再生を制御するには、メディア オブジェクトの制御メソッドを使用できます。 使用できる制御メソッドは<xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、 <xref:System.Windows.Controls.MediaElement.Close%2A>、および<xref:System.Windows.Controls.MediaElement.Stop%2A>します。 <xref:System.Windows.Controls.MediaElement>、ときにこれらのメソッドを使用して対話型のコントロールが使用可能なだけ、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>に設定されている<xref:System.Windows.Controls.MediaState.Manual>します。 メディア オブジェクトが Clock モードの場合、これらのメソッドは使用できません。  
  
 Independent モードの例については、「[MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)」を参照してください。  
  
### <a name="clock-mode"></a>Clock モード  
 Clock モードで、<xref:System.Windows.Media.MediaTimeline>ドライブ メディアを再生します。 Clock モードには次の特徴があります。  
  
-   メディアの<xref:System.Uri>を通じて間接的に設定されて、<xref:System.Windows.Media.MediaTimeline>します。  
  
-   メディアの再生は、クロックによって制御できます。 メディア オブジェクトの制御メソッドは使用できません。  
  
-   設定によってメディアが読み込まれて、<xref:System.Windows.Media.MediaTimeline>オブジェクトの<xref:System.Windows.Media.MediaTimeline.Source%2A>プロパティ、タイムラインからクロックを作成して、クロックをメディア オブジェクトに割り当てます。 メディアは、この方法にも読み込まはときに、<xref:System.Windows.Media.MediaTimeline>内で、<xref:System.Windows.Media.Animation.Storyboard>ターゲット、 <xref:System.Windows.Controls.MediaElement>。  
  
 Clock モードでメディアの再生を制御する、<xref:System.Windows.Media.Animation.ClockController>制御メソッドを使用する必要があります。 A<xref:System.Windows.Media.Animation.ClockController>から取得したが、<xref:System.Windows.Media.Animation.ClockController>のプロパティ、<xref:System.Windows.Media.MediaClock>します。 いずれかの制御方法を使用しようとした場合、<xref:System.Windows.Controls.MediaElement>または<xref:System.Windows.Media.MediaPlayer>clock モード中にオブジェクトを<xref:System.InvalidOperationException>がスローされます。  
  
 クロックとタイムラインの詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。  
  
 Clock モードの例については、「[ストーリーボードを使用して MediaElement を制御する](how-to-control-a-mediaelement-by-using-a-storyboard.md)」を参照してください。  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement クラス  
 追加するだけでは、メディアをアプリケーションに追加する、<xref:System.Windows.Controls.MediaElement>コントロールを[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]アプリケーションの提供して、<xref:System.Uri>を含めたいメディアに。 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 でサポートされているすべてのメディアが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でもサポートされます。 次の例は、単純な使用量を<xref:System.Windows.Controls.MediaElement>で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 このサンプルでは、メディアは、読み込まれるとすぐに自動的に再生されます。 メディアの再生が終了すると、メディアが閉じられ、すべてのメディア リソースが解放されます (ビデオ メモリを含みます)。 これは、既定の動作、<xref:System.Windows.Controls.MediaElement>オブジェクトし、によって制御されます、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>と<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティ。  
  
### <a name="controlling-a-mediaelement"></a>MediaElement の制御  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>と<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティの動作を制御、<xref:System.Windows.Controls.MediaElement>とき<xref:System.Windows.FrameworkElement.IsLoaded%2A>は`true`または`false`、それぞれします。 <xref:System.Windows.Controls.MediaState>メディアの再生動作に影響を与えるプロパティを設定します。 既定ではたとえば、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Play>と既定<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Close>します。 こうすることとすぐに、<xref:System.Windows.Controls.MediaElement>が読み込まれると、プリロールが完了したら、メディアの再生が開始されます。 再生が完了すると、メディアが閉じられ、すべてのメディア リソースが解放されます。  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>と<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティは、メディアの再生を制御する唯一の方法ではありません。 Clock モードで、クロックを制御できます、<xref:System.Windows.Controls.MediaElement>対話型の制御メソッドが制御し、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Manual>します。 <xref:System.Windows.Controls.MediaElement> 次の優先順位を評価することによって、この制御の競合を処理します。  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. メディアがアンロードされているときに有効です。 これにより、既定では、すべてのメディア リソースが解放される場合でも、<xref:System.Windows.Media.MediaClock>に関連付けられている、<xref:System.Windows.Controls.MediaElement>します。  
  
2. <xref:System.Windows.Media.MediaClock>. メディアがある場合、<xref:System.Windows.Controls.MediaElement.Clock%2A>します。 メディアが読み込まれる場合、<xref:System.Windows.Media.MediaClock>限り有効になります、<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Manual>します。 Clock モードは、常の読み込み動作をオーバーライド、<xref:System.Windows.Controls.MediaElement>します。  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. メディアが読み込まれているときに有効です。  
  
4. 対話型の制御メソッド。 場合に発生<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Manual>します。 使用できる制御メソッドは<xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、 <xref:System.Windows.Controls.MediaElement.Close%2A>、および<xref:System.Windows.Controls.MediaElement.Stop%2A>します。  
  
### <a name="displaying-a-mediaelement"></a>MediaElement の表示  
 表示する、<xref:System.Windows.Controls.MediaElement>コンテンツをレンダリングする必要があり、必要があります、<xref:System.Windows.FrameworkElement.ActualWidth%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>プロパティは、コンテンツが読み込まれるまでのゼロに設定します。 オーディオのみのコンテンツでは、これらのプロパティは常に 0 です。 ビデオのコンテンツを 1 回、<xref:System.Windows.Controls.MediaElement.MediaOpened>イベントが発生した、<xref:System.Windows.FrameworkElement.ActualWidth%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>読み込まれたメディアのサイズをレポートには。 つまり、メディアが読み込まれるまで、<xref:System.Windows.Controls.MediaElement>で物理領域を占めることはできません、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]しない限り、<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>プロパティを設定します。  
  
 両方の設定、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>にストレッチすると、指定された領域を塗りつぶすメディアにより、プロパティ、<xref:System.Windows.Controls.MediaElement>します。 か、メディアの元の縦横比を保持するために、<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>プロパティが両方ではなくセットする必要があります。 両方の設定、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティが望ましいことができない可能性がある要素の固定サイズで表示するメディアになります。  
  
 要素のサイズが固定されることを避けるために、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、メディアをプリロールすることができます。 これは、設定で、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>いずれかに<xref:System.Windows.Controls.MediaState.Play>または<xref:System.Windows.Controls.MediaState.Pause>します。 <xref:System.Windows.Controls.MediaState.Pause>状態では、メディアはプリロールされ、最初のフレームが表示されます。 <xref:System.Windows.Controls.MediaState.Play>状態では、メディアはプリロールされ、再生を開始します。  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer クラス  
 場所として、<xref:System.Windows.Controls.MediaElement>クラスは、フレームワーク要素、<xref:System.Windows.Media.MediaPlayer>で使用されるクラスは設計されています<xref:System.Windows.Media.Drawing>オブジェクト。 描画オブジェクトは、パフォーマンスを向上するフレームワーク レベルの機能を犠牲にするとき、または必要なときに使用<xref:System.Windows.Freezable>機能します。 <xref:System.Windows.Media.MediaPlayer> アプリケーションでメディア コンテンツを提供しながらこれらの機能を利用できます。 ような<xref:System.Windows.Controls.MediaElement>、<xref:System.Windows.Media.MediaPlayer>独立で使用できるまたは時刻のモードはありませんが、<xref:System.Windows.Controls.MediaElement>オブジェクトのアンロードし、読み込みの状態。 これの再生コントロールの複雑さを軽減、<xref:System.Windows.Media.MediaPlayer>します。  
  
### <a name="controlling-mediaplayer"></a>Media Player の制御  
 <xref:System.Windows.Media.MediaPlayer>はステートレスであるメディアの再生を制御する方法は 2 つです。  
  
1. 対話型の制御メソッド。 Independent モードのときに (`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A>プロパティ)。  
  
2. <xref:System.Windows.Media.MediaClock>. メディアがある場合、<xref:System.Windows.Media.MediaPlayer.Clock%2A>します。  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer の表示  
 技術的には、<xref:System.Windows.Media.MediaPlayer>物理的に表したものがあるないために、表示されることはできません。 ただしでメディアを存在させる使用できますが、<xref:System.Windows.Media.Drawing>を使用して、<xref:System.Windows.Media.VideoDrawing>クラス。 次の例では、使用、<xref:System.Windows.Media.VideoDrawing>メディアを表示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 参照してください、 [Drawing オブジェクトの概要](drawing-objects-overview.md)の詳細については<xref:System.Windows.Media.Drawing>オブジェクト。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.DrawingGroup>
- [レイアウト](../advanced/layout.md)
- [方法のトピック](audio-and-video-how-to-topics.md)
