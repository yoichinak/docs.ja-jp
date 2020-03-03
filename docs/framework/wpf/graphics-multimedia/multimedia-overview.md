---
title: マルチメディアの概要
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 42d0d388e859b556d23b7fc81931cd61470ba541
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039795"
---
# <a name="multimedia-overview"></a>マルチメディアの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のマルチメディア機能を使用してアプリケーションにオーディオとビデオを統合することで、ユーザー エクスペリエンスを向上させることできます。 このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のマルチメディア機能の概要を説明します。  

<a name="mediaapi"></a>   
## <a name="media-api"></a>メディア API  
 <xref:System.Windows.Controls.MediaElement> クラスと <xref:System.Windows.Media.MediaPlayer> クラスは、オーディオまたはビデオのコンテンツを表示するために使用されます。 これらのクラスは、対話式またはクロックで制御できます。 これらのクラスは、Microsoft Windows Media Player 10 コントロールでメディアの再生に使用できます。 どちらのクラスを使用するかは、シナリオによって決まります。  
  
 <xref:System.Windows.Controls.MediaElement> は、[レイアウト](../advanced/layout.md)によってサポートされる <xref:System.Windows.UIElement> であり、多くのコントロールのコンテンツとして使用できます。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でコードとして使用することもできます。 一方、<xref:System.Windows.Media.MediaPlayer>は <xref:System.Windows.Media.Drawing> オブジェクト向けに設計されており、レイアウトはサポートされていません。 <xref:System.Windows.Media.MediaPlayer> を使用して読み込まれたメディアを表示するには、<xref:System.Windows.Media.VideoDrawing> を使用するか、<xref:System.Windows.Media.DrawingContext>を直接操作する必要があります。 <xref:System.Windows.Media.MediaPlayer> を XAML で使用することはできません。  
  
 描画オブジェクトと描画コンテキストの詳細については、「[描画オブジェクトの概要](drawing-objects-overview.md)」を参照してください。  
  
> [!NOTE]
> アプリケーションでメディアを配布するときに、プロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>メディア再生モード  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement> と <xref:System.Windows.Media.MediaPlayer> の両方に同様のメンバーがあります。 このセクションのリンクでは、<xref:System.Windows.Controls.MediaElement> クラスのメンバーを参照しています。 特に明記されていない限り、<xref:System.Windows.Controls.MediaElement> クラスのにリンクされたメンバーは、<xref:System.Windows.Media.MediaPlayer> クラスにも存在します。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのメディアの再生を理解するには、メディアを再生できる複数のモードを理解しておく必要があります。 <xref:System.Windows.Controls.MediaElement> と <xref:System.Windows.Media.MediaPlayer> はどちらも、独立モードとクロックモードの2つの異なるメディアモードで使用できます。 メディアモードは、<xref:System.Windows.Controls.MediaElement.Clock%2A> プロパティによって決定されます。 <xref:System.Windows.Controls.MediaElement.Clock%2A> が `null`場合、メディアオブジェクトは独立モードになります。 <xref:System.Windows.Controls.MediaElement.Clock%2A> が null 以外の場合、メディアオブジェクトはクロックモードになります。 既定では、メディア オブジェクトは Independent モードになっています。  
  
### <a name="independent-mode"></a>Independent モード  
 Independent モードでは、メディア コンテンツがメディアの再生を行います。 Independent モードには、次のオプションがあります。  
  
- メディアの <xref:System.Uri> を直接指定することができます。  
  
- メディアの再生を直接制御できます。  
  
- メディアの <xref:System.Windows.Controls.MediaElement.Position%2A> と <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> のプロパティは変更できます。  
  
 <xref:System.Windows.Controls.MediaElement> オブジェクトの <xref:System.Windows.Controls.MediaElement.Source%2A> プロパティを設定するか、<xref:System.Windows.Media.MediaPlayer> オブジェクトの <xref:System.Windows.Media.MediaPlayer.Open%2A> メソッドを呼び出すことによって、メディアが読み込まれます。  
  
 Independent モードでメディアの再生を制御するには、メディア オブジェクトの制御メソッドを使用できます。 使用できるコントロールメソッドは、<xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A>、<xref:System.Windows.Controls.MediaElement.Close%2A>、および <xref:System.Windows.Controls.MediaElement.Stop%2A>です。 <xref:System.Windows.Controls.MediaElement>の場合、これらのメソッドを使用した対話型コントロールは、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> が <xref:System.Windows.Controls.MediaState.Manual>に設定されている場合にのみ使用できます。 メディア オブジェクトが Clock モードの場合、これらのメソッドは使用できません。  
  
 Independent モードの例については、「[MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)」を参照してください。  
  
### <a name="clock-mode"></a>Clock モード  
 クロックモードでは、<xref:System.Windows.Media.MediaTimeline> によってメディアの再生が駆動されます。 Clock モードには次の特徴があります。  
  
- メディアの <xref:System.Uri> は、<xref:System.Windows.Media.MediaTimeline>を通じて間接的に設定されます。  
  
- メディアの再生は、クロックによって制御できます。 メディア オブジェクトの制御メソッドは使用できません。  
  
- メディアを読み込むには、<xref:System.Windows.Media.MediaTimeline> オブジェクトの <xref:System.Windows.Media.MediaTimeline.Source%2A> プロパティを設定し、タイムラインからクロックを作成して、メディアオブジェクトに時計を割り当てます。 <xref:System.Windows.Media.Animation.Storyboard> 内の <xref:System.Windows.Media.MediaTimeline> が <xref:System.Windows.Controls.MediaElement>を対象としている場合も、メディアがこの方法で読み込まれます。  
  
 クロックモードでメディアの再生を制御するには、<xref:System.Windows.Media.Animation.ClockController> 制御メソッドを使用する必要があります。 <xref:System.Windows.Media.Animation.ClockController> は、<xref:System.Windows.Media.MediaClock>の <xref:System.Windows.Media.Animation.ClockController> プロパティから取得されます。 クロックモードで <xref:System.Windows.Controls.MediaElement> または <xref:System.Windows.Media.MediaPlayer> のいずれかのオブジェクトの制御メソッドを使用しようとすると、<xref:System.InvalidOperationException> がスローされます。  
  
 クロックとタイムラインの詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。  
  
 Clock モードの例については、「[ストーリーボードを使用して MediaElement を制御する](how-to-control-a-mediaelement-by-using-a-storyboard.md)」を参照してください。  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement クラス  
 アプリケーションにメディアを追加することは、アプリケーションの [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に <xref:System.Windows.Controls.MediaElement> コントロールを追加し、含めるメディアに <xref:System.Uri> を提供するのと同じように簡単です。 Microsoft Windows Media Player 10 でサポートされているすべてのメディアの種類は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]でサポートされています。 次の例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の <xref:System.Windows.Controls.MediaElement> を簡単に使用する方法を示します。  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 このサンプルでは、メディアは、読み込まれるとすぐに自動的に再生されます。 メディアの再生が終了すると、メディアが閉じられ、すべてのメディア リソースが解放されます (ビデオ メモリを含みます)。 これは <xref:System.Windows.Controls.MediaElement> オブジェクトの既定の動作であり、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> プロパティと <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> プロパティによって制御されます。  
  
### <a name="controlling-a-mediaelement"></a>MediaElement の制御  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> プロパティと <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> プロパティは、<xref:System.Windows.FrameworkElement.IsLoaded%2A> が `true` されている場合、または `false`した場合に、<xref:System.Windows.Controls.MediaElement> の動作を制御します。 プロパティ <xref:System.Windows.Controls.MediaState> は、メディアの再生動作に影響を与えるように設定されています。 たとえば、既定の <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> は <xref:System.Windows.Controls.MediaState.Play>、既定の <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> は <xref:System.Windows.Controls.MediaState.Close>です。 これは、<xref:System.Windows.Controls.MediaElement> が読み込まれ、プリロールが完了するとすぐに、メディアの再生が開始されることを意味します。 再生が完了すると、メディアが閉じられ、すべてのメディア リソースが解放されます。  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> と <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> のプロパティは、メディアの再生を制御する唯一の方法ではありません。 クロックモードでは、時計は <xref:System.Windows.Controls.MediaElement> を制御できます。また、対話型コントロールメソッドは、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> が <xref:System.Windows.Controls.MediaState.Manual>されるタイミングを制御します。 <xref:System.Windows.Controls.MediaElement> は、次の優先順位を評価することで、このコンテストを制御対象として処理します。  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. メディアがアンロードされているときに有効です。 これにより、<xref:System.Windows.Media.MediaClock> が <xref:System.Windows.Controls.MediaElement>に関連付けられている場合でも、既定ですべてのメディアリソースが解放されます。  
  
2. <xref:System.Windows.Media.MediaClock>. メディアに <xref:System.Windows.Controls.MediaElement.Clock%2A>がある場合。 メディアがアンロードされると、<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> が <xref:System.Windows.Controls.MediaState.Manual>場合に限り、<xref:System.Windows.Media.MediaClock> が有効になります。 クロックモードは常に、<xref:System.Windows.Controls.MediaElement>の読み込み済みの動作よりも優先されます。  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. メディアが読み込まれているときに有効です。  
  
4. 対話型の制御メソッド。 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> が <xref:System.Windows.Controls.MediaState.Manual>場合。 使用できるコントロールメソッドは、<xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A>、<xref:System.Windows.Controls.MediaElement.Close%2A>、および <xref:System.Windows.Controls.MediaElement.Stop%2A>です。  
  
### <a name="displaying-a-mediaelement"></a>MediaElement の表示  
 <xref:System.Windows.Controls.MediaElement> を表示するには、表示するコンテンツが必要です。また、コンテンツが読み込まれるまで、<xref:System.Windows.FrameworkElement.ActualWidth%2A> と <xref:System.Windows.FrameworkElement.ActualHeight%2A> プロパティは0に設定されます。 オーディオのみのコンテンツでは、これらのプロパティは常に 0 です。 ビデオコンテンツの場合、<xref:System.Windows.Controls.MediaElement.MediaOpened> イベントが発生すると <xref:System.Windows.FrameworkElement.ActualWidth%2A> と <xref:System.Windows.FrameworkElement.ActualHeight%2A> が読み込まれたメディアのサイズを報告します。 つまり、メディアが読み込まれるまで、<xref:System.Windows.Controls.MediaElement> は、<xref:System.Windows.FrameworkElement.Width%2A> または <xref:System.Windows.FrameworkElement.Height%2A> プロパティが設定されていない限り、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 内の物理的な領域を占有しません。  
  
 <xref:System.Windows.FrameworkElement.Width%2A> と <xref:System.Windows.FrameworkElement.Height%2A> の両方のプロパティを設定すると、メディアが拡張されて、<xref:System.Windows.Controls.MediaElement>用に指定された領域がいっぱいになります。 メディアの元の縦横比を維持するには、<xref:System.Windows.FrameworkElement.Width%2A> または <xref:System.Windows.FrameworkElement.Height%2A> のいずれかのプロパティを設定する必要がありますが、両方を設定することはできません。 <xref:System.Windows.FrameworkElement.Width%2A> と <xref:System.Windows.FrameworkElement.Height%2A> の両方のプロパティを設定すると、メディアが固定の要素サイズで表示され、望ましくない場合があります。  
  
 要素のサイズが固定されることを避けるために、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、メディアをプリロールすることができます。 これを行うには、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> を <xref:System.Windows.Controls.MediaState.Play> または <xref:System.Windows.Controls.MediaState.Pause>に設定します。 <xref:System.Windows.Controls.MediaState.Pause> の状態では、メディアがプリロールされ、最初のフレームが表示されます。 <xref:System.Windows.Controls.MediaState.Play> の状態では、メディアがプリロールされ、再生が開始されます。  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer クラス  
 <xref:System.Windows.Controls.MediaElement> クラスがフレームワーク要素の場合、<xref:System.Windows.Media.MediaPlayer> クラスは <xref:System.Windows.Media.Drawing> オブジェクトで使用するように設計されています。 描画オブジェクトは、フレームワークレベルの機能を犠牲にしてパフォーマンスを向上させることができる場合や <xref:System.Windows.Freezable> 機能が必要な場合に使用します。 <xref:System.Windows.Media.MediaPlayer> を使用すると、アプリケーションでメディアコンテンツを提供しながら、これらの機能を利用できます。 <xref:System.Windows.Controls.MediaElement>と同様に、<xref:System.Windows.Media.MediaPlayer> は独立モードまたはクロックモードで使用できますが、<xref:System.Windows.Controls.MediaElement> オブジェクトのアンロード状態と読み込み状態はありません。 これにより、<xref:System.Windows.Media.MediaPlayer>の再生制御の複雑さが軽減されます。  
  
### <a name="controlling-mediaplayer"></a>Media Player の制御  
 <xref:System.Windows.Media.MediaPlayer> はステートレスであるため、メディアの再生を制御する方法は2つしかありません。  
  
1. 対話型の制御メソッド。 独立モード (`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A> プロパティ) の場合。  
  
2. <xref:System.Windows.Media.MediaClock>. メディアに <xref:System.Windows.Media.MediaPlayer.Clock%2A>がある場合。  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer の表示  
 技術的には、物理的な表現がないため、<xref:System.Windows.Media.MediaPlayer> を表示できません。 ただし、<xref:System.Windows.Media.VideoDrawing> クラスを使用して <xref:System.Windows.Media.Drawing> でメディアを表示するために使用できます。 次の例では、<xref:System.Windows.Media.VideoDrawing> を使用してメディアを表示する方法を示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <xref:System.Windows.Media.Drawing> オブジェクトの詳細については、「 [Drawing オブジェクトの概要](drawing-objects-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.DrawingGroup>
- [レイアウト](../advanced/layout.md)
- [方法トピック](audio-and-video-how-to-topics.md)
