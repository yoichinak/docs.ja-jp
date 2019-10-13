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
ms.openlocfilehash: be8dcfce44347e8099e8cfa693bcee341514de2b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291442"
---
# <a name="graphics-and-multimedia"></a>グラフィックスとマルチメディア

<a name="introduction"></a>
 @ no__t を使用すると、マルチメディア、ベクターグラフィックス、アニメーション、およびコンテンツコンポジションがサポートされるため、開発者は興味深いユーザーインターフェイスやコンテンツを簡単に作成できます。 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を使用して、ベクター グラフィックスや複雑なアニメーションを作成し、メディアをアプリケーションに統合できます。

このトピックでは、アプリケーションにグラフィックス、画面切り替え効果、サウンド、ビデオを追加できるようにする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のグラフィックス、アニメーション、メディア機能を紹介します。

> [!NOTE]
> Windows サービスで WPF 型を使用するのは避けることを強くお勧めします。 Windows サービスで WPF 型を使用しようとした場合、サービスが期待どおりに動作しないことがあります。

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 のグラフィックスとマルチメディアの新機能

グラフィックスとアニメーションに関するいくつかの変更点があります。

- レイアウトの丸め

  オブジェクトの端が 1 ピクセル デバイスの中間に位置する場合、DPI に依存しないグラフィックス システムでは、端がぼやけたり半透明になったりするなどのレンダリング アーティファクトが発生することがあります。 以前のバージョンの WPF には、このような場合の処理に役立つピクセル スナップが含まれていました。 Silverlight 2 では、端がピクセル境界全体に位置するように要素を移動する別の方法としてレイアウトの丸めが導入されました。 WPF では、<xref:System.Windows.FrameworkElement> の <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> 添付プロパティを使用したレイアウト丸めがサポートされるようになりました。

- キャッシュ済みコンポジション

  新しい <xref:System.Windows.Media.BitmapCache> および <xref:System.Windows.Media.BitmapCacheBrush> クラスを使用すると、ビジュアルツリーの複雑な部分をビットマップとしてキャッシュし、レンダリング時間を大幅に短縮することができます。 ビットマップは、マウス クリックなどのユーザー入力に引き続き応答し、その他の要素上にブラシのように描画できます。

- Pixel Shader 3 のサポート

  Wpf 4 は、WPF 3.5 SP1 で導入された @no__t 0 サポートの上に構築されます。これは、アプリケーションがピクセルシェーダー (PS) バージョン3.0 を使用して効果を書き込むことができるようにするためです。 PS 3.0 のシェーダー モデルは PS 2.0 より洗練されており、サポートされているハードウェア上でより多くのエフェクトを使用できます。

- イージング関数

  イージング関数を使用してアニメーションを強化し、アニメーションの動作をより細かく制御できます。 たとえば、アニメーションに @no__t 0 を適用して、アニメーションに springy の動作を与えることができます。 詳細については、「<xref:System.Windows.Media.Animation> 名前空間のイージング型」を参照してください。

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>グラフィックスとレンダリング

WPF では、高品質な 2-D グラフィックがサポートされます。 ブラシ、ジオメトリ、イメージ、図形、変換などの機能が用意されています。 詳しくは、「[グラフィックス](graphics.md)」をご覧ください。 グラフィカル要素のレンダリングは、@no__t 0 のクラスに基づいています。 画面のビジュアル オブジェクトの構造は、ビジュアル ツリーで表されます。 詳しくは、「[WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)」をご覧ください。

### <a name="2-d-shapes"></a>2-D 図形

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、次の図に示すように、一般的に使用されるベクター描画の2-d 図形 (四角形や楕円など) のライブラリを提供します。

![楕円と四角形を示す図。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

これらの固有の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 図形は単なる図形ではなく、一般的なコントロールに期待されるキーボード入力やマウス入力などの機能の多くを実装するプログラミング可能な要素です。 次の例は、<xref:System.Windows.Shapes.Ellipse> 要素をクリックすることによって発生する @no__t 0 イベントを処理する方法を示しています。

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

!["楕円をクリックしました" というメッセージボックスが表示されます。](./media/index/messagebox-text-output.png)

詳しくは、「 [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)」をご覧ください。 入門用のサンプルについては、「[Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)」をご覧ください。

### <a name="2-d-geometries"></a>2-D ジオメトリ

によって提供される2-d 図形では不十分な場合は、ジオメトリとパスに対して [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のサポートを使用して、独自の @no__t を作成できます。 ジオメトリを使用して図形を描画ブラシとして作成し、他の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素をクリップする方法を次の図に示します。

![図形を作成するためにジオメトリを使用する方法を示すスクリーンショット。](./media/index/use-geometries-create-shapes.png)

詳しくは、「[ジオメトリの概要](geometry-overview.md)」をご覧ください。 入門用のサンプルについては、「[ジオメトリのサンプル](https://go.microsoft.com/fwlink/?LinkID=159989)」をご覧ください。

### <a name="2-d-effects"></a>2-D 効果

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、さまざまな効果を作成するために使用できる2-d クラスのライブラリが用意されています。 @No__t-0 の2-d レンダリング機能を使用すると、グラデーション、ビットマップ、描画、およびビデオを含む [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を描画できます。回転、拡大縮小、傾斜を使用してそれらを操作します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ブラシを使用して実現できる多くの効果の例を次の図に示します。

![さまざまな WPF ブラシと描画要素を示す図。](./media/index/brushes-paint-elements.png)

詳しくは、「 [WPF のブラシの概要](wpf-brushes-overview.md)」をご覧ください。 入門用のサンプルについては、「[ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)」をご覧ください。

<a name="rendering"></a>

## <a name="3-d-rendering"></a>3-D レンダリング

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の2-d グラフィックスサポートと統合する3-d レンダリング機能のセットを提供します。これにより、より魅力的なレイアウト、@no__t 2、データビジュアライゼーションを作成できます。 次の図に示すように、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用すると、3-d 図形の表面に2-d イメージをレンダリングできます。

![異なるテクスチャを持つ3-d 図形を示すサンプルのスクリーンショット。](./media/index/visual-three-dimensional-shape.png)

詳しくは、「 [3-D グラフィックスの概要](3-d-graphics-overview.md)」をご覧ください。 入門用のサンプルについては、「[3-D ソリッドのサンプル](https://go.microsoft.com/fwlink/?LinkID=159964)」をご覧ください。

<a name="animation"></a>

## <a name="animation"></a>アニメーション

アニメーションを使用すると、コントロールや要素を拡大、振動、回転、フェードさせることができ、魅力的なページ遷移なども作成できです。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ではほとんどのプロパティをアニメーション化できるため、ほとんどの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] オブジェクトをアニメーション化できるだけでなく、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用して作成するカスタム オブジェクトをアニメーション化することもできます。

![アニメーションキューブのスクリーンショット。](./media/index/animate-custom-objects.png)

詳しくは、「 [アニメーションの概要](animation-overview.md)」をご覧ください。 入門用のサンプルについては、「[アニメーション サンプル ギャラリー](https://go.microsoft.com/fwlink/?LinkID=159969)」をご覧ください。

<a name="media"></a>

## <a name="media"></a>メディア

イメージ、ビデオ、オーディオは、情報とユーザー エクスペリエンスを伝えるメディア リッチな手段です。

### <a name="images"></a>画像

アイコン、背景、アニメーションのパーツを含むイメージは、ほとんどのアプリケーションの中核です。 イメージは頻繁に使用する必要があるため、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ではさまざまな方法でイメージを処理する機能を公開しています。 その方法の 1 つを次の図に示します。

![スタイルのサンプルスクリーンショット](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

詳しくは、「 [イメージングの概要](imaging-overview.md)」をご覧ください。

### <a name="video-and-audio"></a>ビデオとオーディオ

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のグラフィックス機能の中核となる機能は、ビデオやオーディオを含むマルチメディアの処理をネイティブにサポートすることです。 次の例では、メディア プレーヤーをアプリケーションに挿入する方法を示しています。

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement> はビデオとオーディオの両方を再生できるので、カスタム Ui を簡単に作成できるように拡張できます。

詳しくは、「[マルチメディアの概要](multimedia-overview.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [アニメーションとタイミングに関する「方法」トピック](animation-and-timing-how-to-topics.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)
- [マルチメディアの概要](multimedia-overview.md)
