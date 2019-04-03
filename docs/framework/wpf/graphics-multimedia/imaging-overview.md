---
title: イメージングの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
ms.openlocfilehash: 45214b5f0e6827c36f87a4d45592ff0989c9a877
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890811"
---
# <a name="imaging-overview"></a>イメージングの概要
このトピックでは、[!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)] の概要を説明します。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 表示、変換、および画像の書式を設定することができます。  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>WPF Imaging Component  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 内のイメージング機能が大幅に強化[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]します。 ビットマップの表示や一般的なコントロールでのイメージの使用などのイメージング機能は、これまでは [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] または [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] ライブラリに頼っていました。 これらの [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] は、基本的なイメージング機能を提供しますが、コーデックの拡張機能や高品質なイメージのサポートなどの機能が不足しています。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 場合の欠点を克服するために設計されていますが[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]と[!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)]の新しいセットを提供し、[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]を表示し、アプリケーション内でイメージを使用します。  
  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)][!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] にアクセスする方法は 2 つあります (マネージド コンポーネントとアンマネージド コンポーネント)。 アンマネージ コンポーネントは、次の機能を提供します。  
  
-   新規または独自のイメージ形式の機能拡張モデル。  
  
-   [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)]、[!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)]、[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]、[!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)]、[!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)]、[!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]、アイコン (.ico) を含むネイティブ イメージ形式のパフォーマンスとセキュリティの向上。  
  
-   チャネルあたり最大 8 ビットのビット深度の高いイメージ データの保存 (ピクセルあたり 32 ビット)。  
  
-   非破壊的なイメージのスケーリング、クロップ、および回転。  
  
-   単純化されたカラー管理。  
  
-   ファイル内での専用メタデータのサポート。  
  
-   マネージド コンポーネントは、アンマネージド インフラストラクチャを利用して、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、アニメーション、グラフィックスなどの他の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 機能とイメージをシームレスに統合します。 マネージ コンポーネントの利点も活用、Windows Presentation Foundation (WPF) イメージング コーデック機能拡張モデルにより、新しいイメージ形式の自動認識[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーション。  
  
 ほとんどのマネージ[!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)][!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]内に存在、<xref:System.Windows.Media.Imaging?displayProperty=nameWithType>名前空間など、いくつかの重要な型が<xref:System.Windows.Media.ImageBrush>と<xref:System.Windows.Media.ImageDrawing>内に存在、<xref:System.Windows.Media?displayProperty=nameWithType>名前空間と<xref:System.Windows.Controls.Image>に存在します。<xref:System.Windows.Controls?displayProperty=nameWithType>名前空間。  
  
 このトピックでは、マネージド コンポーネントに関する追加情報について説明します。 アンマネージ [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] の詳細については、[アンマネージ WPF Imaging Component](/windows/desktop/wic/-wic-lh) に関するドキュメントを参照してください。  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF イメージ形式  
 コーデックは、特定のメディア形式をデコードまたはエンコードするために使用されます。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 用のコーデックが含まれています[!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)]、 [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]、 [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]、 [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]、 [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)]、 [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]、および ICON イメージ形式。 アプリケーションは、これらのコーデックを使用して、対応するイメージ形式をデコードでき、ICON を除くイメージ形式をエンコードできます。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> 重要なクラスは、デコードおよびイメージのエンコードに使用されます。 それは、[!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] パイプラインの基本ビルディング ブロックであり、ピクセルの単一の定数セットを特定のサイズと解像度で表現します。 A<xref:System.Windows.Media.Imaging.BitmapSource>複数フレーム イメージの個々 のフレームまたはに対して実行された変換の結果であることができます、<xref:System.Windows.Media.Imaging.BitmapSource>します。 使用される主要クラスの多くの親である[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]などイメージング<xref:System.Windows.Media.Imaging.BitmapFrame>します。  
  
 A<xref:System.Windows.Media.Imaging.BitmapFrame>イメージ形式の実際のビットマップ データを格納するために使用します。 多くのイメージ形式は、1 つのみサポート<xref:System.Windows.Media.Imaging.BitmapFrame>ですなどの書式[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]と[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]イメージごとの複数のフレームをサポートします。 フレームは、デコーダーによって入力データとして使用され、イメージ ファイルを作成するためにエンコーダーに渡されます。  
  
 例を次に示す方法、<xref:System.Windows.Media.Imaging.BitmapFrame>から作成された、<xref:System.Windows.Media.Imaging.BitmapSource>に追加し、[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]イメージ。  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>イメージ形式のデコード  
 イメージのデコードは、イメージ形式をシステムで使用できるイメージ データに変換する操作です。 変換したイメージ データを使用して、表示、処理、または別の形式へのエンコードを実行できます。 デコーダーの選択は、イメージ形式に基づきます。 コーデックの選択は、特定のデコーダーを指定しない限り、自動的に行われます。 自動デコード操作については、「[WPF でのイメージの表示](#_displayingimages)」セクションの例を参照してください。 アンマネージ [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] インターフェイスを使用して開発し、システムに登録したカスタム形式デコーダーは、デコーダーの選択に自動的に追加されます。 これにより、カスタム形式を [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションに自動的に表示することができます。  
  
 次の例では、ビットマップ デコーダーを使用した [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] 形式のイメージのデコード操作を示します。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>イメージ形式のエンコード  
 イメージのエンコードは、イメージ データを特定のイメージ形式に変換する操作です。 エンコードされたイメージ データを使用して、新しいイメージ ファイルを作成できます。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 上記で説明したイメージ形式の各エンコーダーを提供します。  
  
 次の例は、エンコーダーを使用して新しく作成されたビットマップ イメージを保存する操作を示しています。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>WPF でのイメージの表示  
 Windows Presentation Foundation (WPF) アプリケーションでイメージを表示するいくつかの方法はあります。 使用してイメージを表示することができます、 <xref:System.Windows.Controls.Image> visual を使用して描画コントロール、<xref:System.Windows.Media.ImageBrush>を使用して描画または、<xref:System.Windows.Media.ImageDrawing>します。  
  
### <a name="using-the-image-control"></a>イメージ コントロールの使用  
 <xref:System.Windows.Controls.Image> フレームワーク要素とアプリケーションでイメージを表示する主な方法です。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、 <xref:System.Windows.Controls.Image> ; 属性構文またはプロパティの構文の 2 つの方法で使用できます。 次の例は、属性構文とプロパティ タグ構文の両方を使用して、幅 200 ピクセルのイメージをレンダリングする方法を示しています。 属性構文とプロパティ構文の詳細については、「[依存関係プロパティの概要](../advanced/dependency-properties-overview.md)」を参照してください。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 多くの例を使用して、<xref:System.Windows.Media.Imaging.BitmapImage>イメージ ファイルを参照するオブジェクト。 <xref:System.Windows.Media.Imaging.BitmapImage> 特殊な<xref:System.Windows.Media.Imaging.BitmapSource>用に最適化された[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]としてイメージを表示する簡単な方法であり、読み込み、<xref:System.Windows.Controls.Image.Source%2A>の<xref:System.Windows.Controls.Image>コントロール。  
  
 次の例は、コードを使用して幅 200 ピクセルのイメージをレンダリングする方法を示しています。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> 実装して、<xref:System.ComponentModel.ISupportInitialize>インターフェイスに複数のプロパティの初期化を最適化します。 プロパティの変更は、オブジェクトの初期化中にのみ実行できます。 呼び出す<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>をその初期化が開始された通知と<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>初期化が完了を通知します。 初期化の完了後は、プロパティの変更は無視されます。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>イメージの回転、変換、およびクロップ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プロパティを使用してイメージを変換することができます<xref:System.Windows.Media.Imaging.BitmapImage>または追加を使用して<xref:System.Windows.Media.Imaging.BitmapSource>などのオブジェクト<xref:System.Windows.Media.Imaging.CroppedBitmap>または<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>します。 これらのイメージの変換では、イメージの拡大縮小、回転、ピクセル形式の変更、またはクロップを行うことができます。  
  
 使用してイメージの回転を実行、<xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A>プロパティの<xref:System.Windows.Media.Imaging.BitmapImage>します。 回転は、90 ° 単位でのみ実行できます。 次の例では、イメージが 90 ° 回転します。  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 グレースケールの実行など、イメージを別のピクセル形式に変換を使用して<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>します。 次の例では、イメージに変換されます<xref:System.Windows.Media.PixelFormats.Gray4%2A>します。  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 か、イメージをトリミングするには、<xref:System.Windows.UIElement.Clip%2A>プロパティの<xref:System.Windows.Controls.Image>または<xref:System.Windows.Media.Imaging.CroppedBitmap>ことができます。 通常、必要がある場合、イメージの部分を表示する<xref:System.Windows.UIElement.Clip%2A>使用する必要があります。 エンコードして、トリミングされたイメージを保存する必要がある場合、<xref:System.Windows.Media.Imaging.CroppedBitmap>使用する必要があります。 次の例では、イメージがクリップのプロパティを使用して、<xref:System.Windows.Media.EllipseGeometry>します。  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>イメージの引き伸ばし  
 <xref:System.Windows.Controls.Image.Stretch%2A>プロパティは、イメージを拡大して、コンテナーを入力する方法を制御します。 <xref:System.Windows.Controls.Image.Stretch%2A>プロパティによって定義された、次の値では、<xref:System.Windows.Media.Stretch>列挙体。  
  
-   <xref:System.Windows.Media.Stretch.None>:イメージが出力領域に引き伸ばされません。 イメージが出力領域よりも大きい場合は、出力領域に収まらない部分がクリップされたイメージが出力領域に描画されます。  
  
-   <xref:System.Windows.Media.Stretch.Fill>:イメージが出力領域に合わせて拡大縮小します。 イメージの高さと幅は個別に拡大縮小されるため、イメージの元の縦横比は保持されないことがあります。 つまり、イメージは、出力コンテナーを完全に埋めるためにゆがんで表示される可能性があります。  
  
-   <xref:System.Windows.Media.Stretch.Uniform>:イメージに、出力領域内で完全に収まるようにスケーリングします。 イメージの縦横比は保持されます。  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>:イメージは、イメージの元の縦横比を維持しながら、出力領域を完全に塗りつぶすようにスケーリングします。  
  
 次の例では、適用の使用可能な各<xref:System.Windows.Media.Stretch>列挙を<xref:System.Windows.Controls.Image>します。  
  
 次の図の例からの出力およびさまざまな影響を示します<xref:System.Windows.Controls.Image.Stretch%2A>設定がある場合に、イメージに適用されます。  
  
 ![TileBrush のさまざまな Stretch 設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
異なる Stretch 設定  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>イメージによる塗りつぶし  
 描画でイメージがアプリケーションで表示することもできます、<xref:System.Windows.Media.Brush>します。 ブラシを使用すると、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] オブジェクトを単色で塗りつぶすことも、パターンとイメージの複雑な組み合わせで塗りつぶすこともできます。 イメージの描画に使用して、<xref:System.Windows.Media.ImageBrush>します。 <xref:System.Windows.Media.ImageBrush>の種類は、<xref:System.Windows.Media.TileBrush>ビットマップ イメージとしてその内容を定義します。 <xref:System.Windows.Media.ImageBrush>で指定された 1 つのイメージを表示します。 その<xref:System.Windows.Media.ImageBrush.ImageSource%2A>プロパティ。 イメージがゆがまないようしたり、パターンやその他の効果を作成したりするために、イメージの伸縮、配置、およびタイル表示方法を制御できます。 次の図に、いくつかの効果を達成できる、<xref:System.Windows.Media.ImageBrush>します。  
  
 ![ImageBrush の出力例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
イメージ ブラシは、図形、コントロール、テキストなどを塗りつぶすことができる  
  
 次の例を使用して、イメージ付きのボタンの背景を描画する方法、<xref:System.Windows.Media.ImageBrush>します。  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 詳細については<xref:System.Windows.Media.ImageBrush>イメージの描画を参照してくださいと[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>イメージのメタデータ  
 一部のイメージ ファイルには、ファイルの内容または特性を記述するメタデータが含まれています。 たとえば、ほとんどのデジタル カメラは、イメージをキャプチャするために使用されるカメラの型番に関するメタデータを含むイメージを作成します。 各イメージ形式は、メタデータを異なる方法で処理しますが、[!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] では、サポートしているイメージ形式のメタデータの格納と取得を一律に実行します。  
  
 メタデータへのアクセスがを通じて提供される、<xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>のプロパティを<xref:System.Windows.Media.Imaging.BitmapSource>オブジェクト。 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> 返します、<xref:System.Windows.Media.Imaging.BitmapMetadata>イメージに含まれるすべてのメタデータを含むオブジェクト。 このデータは、1 つのメタデータ スキーマでも、異なるスキーマの組み合わせでもかまいません。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 次のイメージのメタデータのスキーマをサポートしています: [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)]、テキスト (PNG テキスト データ)、 [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)]、 [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)]、および[!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)]します。  
  
 メタデータの読み取りのプロセスを簡略化するため<xref:System.Windows.Media.Imaging.BitmapMetadata>など簡単にアクセスできるいくつかの名前付きプロパティを提供します<xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>、 <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>、および<xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>します。 これらの名前付きプロパティの多くは、メタデータを書き込むためにも使用できます。 メタデータを読み取るための追加サポートは、メタデータ クエリ リーダーによって提供されます。 <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>など文字列クエリを指定して、メタデータ クエリ リーダーを取得するメソッドが使用される *"/app1/app1/exif/"* します。 次の例では、<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>に格納されているテキストを取得するために使用、 *「テキスト/説明」* 場所。  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 メタデータを書き込むには、メタデータ クエリ ライターが使用されます。 <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> クエリの記述を取得し、目的の値を設定します。 次の例では、<xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>に格納されているテキストを書き込むために使用、 *「テキスト/説明」* 場所。  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>コーデックの機能拡張  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] の核心的な機能は、新しいイメージ コーデック用の機能拡張モデルです。 これらのアンマネージ インターフェイスによって、コーデック開発者は、コーデックを [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] と統合して、新しいイメージ形式を [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションで自動的に使用できるようにすることができます。  
  
 機能拡張 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] のサンプルについては、[Win32 サンプル コーデック](https://go.microsoft.com/fwlink/?LinkID=160052)に関するページを参照してください。 このサンプルは、カスタム イメージ形式用のデコーダーとエンコーダーの作成方法を示しています。  
  
> [!NOTE]
>  システムで認識するは、コーデックをデジタル署名する必要があります。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 サンプル コーデック](https://go.microsoft.com/fwlink/?LinkID=160052)
