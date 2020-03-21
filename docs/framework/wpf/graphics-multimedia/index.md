---
title: グラフィックスとマルチメディア
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: 8636afcc5b63b71dc729812a7f3eb4945ba49494
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112038"
---
# <a name="graphics-and-multimedia"></a>グラフィックスとマルチメディア

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、マルチ メディア、ベクター グラフィックス、アニメーション、コンテンツ構成のサポートが提供されるので、開発者はユーザーの関心を引くユーザー インターフェイスやコンテンツを簡単に開発できます。 Visual Studio を使用すると、ベクター グラフィックスまたは複雑なアニメーションを作成し、メディアをアプリケーションに統合できます。

このトピックでは、アプリケーションにグラフィックス、画面切り替え効果、サウンド、ビデオを追加できるようにする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のグラフィックス、アニメーション、メディア機能を紹介します。

> [!NOTE]
> Windows サービスで WPF 型を使用するのは避けることを強くお勧めします。 Windows サービスで WPF 型を使用しようとした場合、サービスが期待どおりに動作しないことがあります。

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 のグラフィックスとマルチメディアの新機能

グラフィックスとアニメーションに関するいくつかの変更点があります。

- レイアウトの丸め

  オブジェクトの端が 1 ピクセル デバイスの中間に位置する場合、DPI に依存しないグラフィックス システムでは、端がぼやけたり半透明になったりするなどのレンダリング アーティファクトが発生することがあります。 以前のバージョンの WPF には、このような場合の処理に役立つピクセル スナップが含まれていました。 Silverlight 2 では、端がピクセル境界全体に位置するように要素を移動する別の方法としてレイアウトの丸めが導入されました。 WPF では、添付プロパティを使用<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>したレイアウトの<xref:System.Windows.FrameworkElement>丸め処理がサポートされるようになりました。

- キャッシュ済みコンポジション

  new<xref:System.Windows.Media.BitmapCache>と<xref:System.Windows.Media.BitmapCacheBrush>クラスを使用すると、ビジュアル ツリーの複雑な部分をビットマップとしてキャッシュし、レンダリング時間を大幅に短縮できます。 ビットマップは、マウス クリックなどのユーザー入力に引き続き応答し、その他の要素上にブラシのように描画できます。

- Pixel Shader 3 のサポート

  WPF 4 は、WPF <xref:System.Windows.Media.Effects.ShaderEffect> 3.5 SP1 で導入されたサポートの上に構築され、アプリケーションは、ピクセル シェーダー (PS) バージョン 3.0 を使用して効果を書き込むことができます。 PS 3.0 のシェーダー モデルは PS 2.0 より洗練されており、サポートされているハードウェア上でより多くのエフェクトを使用できます。

- イージング関数

  イージング関数を使用してアニメーションを強化し、アニメーションの動作をより細かく制御できます。 たとえば、アニメーションに を<xref:System.Windows.Media.Animation.ElasticEase>適用して、アニメーションにスプリング動作を与えることができます。 詳細については、名前空間のイージング型を<xref:System.Windows.Media.Animation>参照してください。

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>グラフィックスとレンダリング

WPF には、高品質の 2D グラフィックスのサポートが含まれています。 ブラシ、ジオメトリ、イメージ、図形、変換などの機能が用意されています。 詳しくは、「[グラフィックス](graphics.md)」をご覧ください。 グラフィカル要素のレンダリングは、クラスに<xref:System.Windows.Media.Visual>基づいています。 画面のビジュアル オブジェクトの構造は、ビジュアル ツリーで表されます。 詳しくは、「[WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)」をご覧ください。

### <a name="2d-shapes"></a>2D 形状

WPF には、次の図に示す四角形や楕円など、一般的に使用されるベクター描画の 2D 図形のライブラリが用意されています。

![楕円と四角形を示す図。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

これらの組み込みの WPF シェイプは単なる図形ではなく、キーボードやマウス入力を含む、最も一般的なコントロールから期待される多くの機能を実装するプログラミング可能な要素です。 要素をクリックして発生したイベントを<xref:System.Windows.UIElement.MouseUp>処理する方法を次<xref:System.Windows.Shapes.Ellipse>の例に示します。

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

上記の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップとコードビハインドの出力を次の図に示します。

![「楕円をクリックしました」 というメッセージ ボックス](./media/index/messagebox-text-output.png)

詳しくは、「 [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)」をご覧ください。 入門用のサンプルについては、「[Shape 要素のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)」をご覧ください。

### <a name="2d-geometries"></a>2D ジオメトリ

WPF が提供する 2D 図形が十分でない場合は、WPF のサポートを使用して独自のジオメトリとパスを作成できます。 次の図は、図形を描画ブラシとして作成し、他の WPF 要素をクリップするためにジオメトリを使用する方法を示しています。

![ジオメトリを使用して図形を作成する方法を示すスクリーンショット。](./media/index/use-geometries-create-shapes.png)

詳細については、「[ジオメトリの概要」を](geometry-overview.md)参照してください。 入門用のサンプルについては、「[ジオメトリのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)」をご覧ください。

### <a name="2d-effects"></a>2D エフェクト

WPF には、さまざまな効果を作成するために使用できる 2D クラスのライブラリが用意されています。 WPF の 2D レンダリング機能は、グラデーション[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、ビットマップ、描画、およびビデオを持つ要素を描画する機能を提供します。回転、スケーリング、およびスキューを使用して操作できます。 次の図は、WPF ブラシを使用して実現できる多くの効果の例を示しています。

![さまざまな WPF のブラシとペイント要素を示す図。](./media/index/brushes-paint-elements.png)

詳細については、「 [WPF ブラシの概要](wpf-brushes-overview.md)」を参照してください。 入門用のサンプルについては、「[ブラシのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)」をご覧ください。

<a name="rendering"></a>

## <a name="3d-rendering"></a>3D レンダリング

WPF には、より魅力的なレイアウト、およびデータの視覚化を作成するために、WPF[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]で 2D グラフィックス サポートと統合する一連の 3D レンダリング機能が用意されています。 スペクトルの一方の端で、WPF では、次の図に示す 3D 図形のサーフェスに 2D イメージをレンダリングできます。

![異なるテクスチャを持つ 3D 図形を示すサンプルのスクリーンショット。](./media/index/visual-three-dimensional-shape.png)

詳細については[、「3D グラフィックスの概要](3-d-graphics-overview.md)」を参照してください。 入門サンプルについては[、「3D ソリッドのサンプル](https://go.microsoft.com/fwlink/?LinkID=159964)」を参照してください。

<a name="animation"></a>

## <a name="animation"></a>アニメーション

アニメーションを使用すると、コントロールや要素を拡大、振動、回転、フェードさせることができ、魅力的なページ遷移なども作成できです。 WPF ではほとんどのプロパティをアニメーション化できるため、ほとんどの WPF オブジェクトをアニメーション化できるだけでなく、WPF を使用して作成したカスタム オブジェクトをアニメーション化することもできます。

![アニメーション キューブのスクリーンショット。](./media/index/animate-custom-objects.png)

詳細については、「アニメーションの[概要](animation-overview.md)」を参照してください。 入門用のサンプルについては、「[アニメーション サンプル ギャラリー](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)」をご覧ください。

<a name="media"></a>

## <a name="media"></a>メディア

イメージ、ビデオ、オーディオは、情報とユーザー エクスペリエンスを伝えるメディア リッチな手段です。

### <a name="images"></a>イメージ

アイコン、背景、アニメーションのパーツを含むイメージは、ほとんどのアプリケーションの中核です。 イメージを頻繁に使用する必要があるため、WPF ではさまざまな方法でイメージを操作する機能が公開されています。 その方法の 1 つを次の図に示します。

![スタイリングサンプルスクリーンショット](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

詳細については、「[イメージングの概要」を](imaging-overview.md)参照してください。

### <a name="video-and-audio"></a>ビデオとオーディオ

WPF のグラフィックス機能の中核となる機能は、ビデオやオーディオを含むマルチメディアの操作をネイティブサポートすることです。 次の例では、メディア プレーヤーをアプリケーションに挿入する方法を示しています。

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>は、ビデオとオーディオの両方を再生でき、カスタムの UI を簡単に作成できるほど拡張できます。

詳しくは、「[マルチメディアの概要](multimedia-overview.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [アニメーションおよびタイミングに関する「方法」トピック](animation-and-timing-how-to-topics.md)
- [3D グラフィックスの概要](3-d-graphics-overview.md)
- [マルチメディアの概要](multimedia-overview.md)
