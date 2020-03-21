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
ms.openlocfilehash: 3365c35e3e7b7fe5c0be48a65d7a14da0882c90e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186691"
---
# <a name="imaging-overview"></a>イメージングの概要
このトピックでは、Microsoft Windows プレゼンテーション ファウンデーション イメージング コンポーネントの概要を説明します。 WPF イメージングを使用すると、開発者はイメージの表示、変換、および書式設定を行うことができます。  

## <a name="wpf-imaging-component"></a>WPF Imaging Component  
 WPF イメージングでは、Windows 内のイメージング機能が大幅に強化されています。 ビットマップの表示やコモン コントロールでのイメージの使用などのイメージング機能は、以前は、Windows グラフィックス デバイス インターフェイス (GDI) または Microsoft Windows GDI+ ライブラリに依存していました。 これらの API は、ベースライン・イメージング機能を提供しますが、コーデック機能拡張のサポートや忠実度の高いイメージ・サポートなどの機能が不足しています。 WPF イメージングは、GDI と GDI+ の欠点を克服し、アプリケーション内でイメージを表示および使用するための新しい API セットを提供するように設計されています。  
  
 WPF イメージング API にアクセスする方法には、マネージ コンポーネントとアンマネージ コンポーネントの 2 つの方法があります。 アンマネージ コンポーネントは、次の機能を提供します。  
  
- 新規または独自のイメージ形式の機能拡張モデル。  
  
- ビットマップ (BMP)、共同フォトグラフィックエキスパートグループ(JPEG)、ポータブルネットワークグラフィックス(PNG)、タグ付け画像ファイル形式(TIFF)、Microsoft Windowsメディア写真、グラフィックス交換形式(GIF)、ネイティブ画像フォーマットのパフォーマンスとセキュリティの向上、とアイコン (.ico).  
  
- チャネルあたり最大 8 ビットのビット深度の高いイメージ データの保存 (ピクセルあたり 32 ビット)。  
  
- 非破壊的なイメージのスケーリング、クロップ、および回転。  
  
- 単純化されたカラー管理。  
  
- ファイル内での専用メタデータのサポート。  
  
- マネージ コンポーネントは、アンマネージ インフラストラクチャを利用して、アニメーション、グラフィックスなどの[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]他の WPF 機能とシームレスに画像を統合します。 マネージ コンポーネントは、WPF アプリケーションで新しいイメージ形式を自動的に認識できるようにする、Windows プレゼンテーション ファンデーション (WPF) イメージング コーデック拡張モデルの利点もあります。  
  
 マネージ WPF<xref:System.Windows.Media.Imaging?displayProperty=nameWithType>イメージング API の大部分は名前空間に存在しますが、<xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.ImageDrawing><xref:System.Windows.Media?displayProperty=nameWithType>名前空間に存在し、名前空間に<xref:System.Windows.Controls.Image>存在するなどの重要な型が<xref:System.Windows.Controls?displayProperty=nameWithType>いくつか存在します。  
  
 このトピックでは、マネージド コンポーネントに関する追加情報について説明します。 アンマネージ API の詳細については、[アンマネージ WPF イメージング コンポーネント](/windows/desktop/wic/-wic-lh)のドキュメントを参照してください。  
  
<a name="_imageformats"></a>
## <a name="wpf-image-formats"></a>WPF イメージ形式  

 コーデックは、特定のメディア形式をデコードまたはエンコードするために使用されます。 WPF イメージングには、BMP、JPEG、PNG、TIFF、Windows メディア フォト、GIF、およびアイコン イメージ形式用のコーデックが含まれています。 アプリケーションは、これらのコーデックを使用して、対応するイメージ形式をデコードでき、ICON を除くイメージ形式をエンコードできます。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>は、イメージのデコードとエンコードで使用される重要なクラスです。 これは、WPF イメージング パイプラインの基本的な構成要素であり、特定のサイズと解像度で 1 つの一定のピクセル セットを表します。 A<xref:System.Windows.Media.Imaging.BitmapSource>は、複数フレームイメージの個々のフレームにすることも、に対して実行される変換の結果である場合<xref:System.Windows.Media.Imaging.BitmapSource>があります。 これは、 などの<xref:System.Windows.Media.Imaging.BitmapFrame>WPF イメージングで使用される多くのプライマリ クラスの親です。  
  
 A<xref:System.Windows.Media.Imaging.BitmapFrame>は、イメージ形式の実際のビットマップ データを格納するために使用されます。 多くの画像形式では 1<xref:System.Windows.Media.Imaging.BitmapFrame>つの みサポートのみが可能ですが、GIF や TIFF などの形式ではイメージごとに複数のフレームがサポートされています。 フレームは、デコーダーによって入力データとして使用され、イメージ ファイルを作成するためにエンコーダーに渡されます。  
  
 を作成し、TIFF イメージ<xref:System.Windows.Media.Imaging.BitmapFrame>に追加する方法<xref:System.Windows.Media.Imaging.BitmapSource>を次の例に示します。  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>イメージ形式のデコード  
 イメージのデコードは、イメージ形式をシステムで使用できるイメージ データに変換する操作です。 変換したイメージ データを使用して、表示、処理、または別の形式へのエンコードを実行できます。 デコーダーの選択は、イメージ形式に基づきます。 コーデックの選択は、特定のデコーダーを指定しない限り、自動的に行われます。 自動デコード操作については、「[WPF でのイメージの表示](#_displayingimages)」セクションの例を参照してください。 アンマネージ WPF イメージング インターフェイスを使用して開発され、システムに登録されたカスタム形式デコーダは、自動的にデコーダの選択に参加します。 これにより、カスタム形式を WPF アプリケーションで自動的に表示できます。  
  
 ビットマップ デコーダを使用して BMP 形式のイメージをデコードする例を次に示します。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>イメージ形式のエンコード  
 イメージのエンコードは、イメージ データを特定のイメージ形式に変換する操作です。 エンコードされたイメージ データを使用して、新しいイメージ ファイルを作成できます。 WPF イメージングでは、上記の各イメージ形式のエンコーダーが提供されます。  
  
 次の例は、エンコーダーを使用して新しく作成されたビットマップ イメージを保存する操作を示しています。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>
## <a name="displaying-images-in-wpf"></a>WPF でのイメージの表示  
 Windows プレゼンテーション ファウンデーション (WPF) アプリケーションでイメージを表示するには、いくつかの方法があります。 イメージは、コントロールを<xref:System.Windows.Controls.Image>使用して表示したり、ビジュアルに描画したり、<xref:System.Windows.Media.ImageBrush>を使用して描画したりできます<xref:System.Windows.Media.ImageDrawing>。  
  
### <a name="using-the-image-control"></a>イメージ コントロールの使用  
 <xref:System.Windows.Controls.Image>は、フレームワーク要素であり、アプリケーションでイメージを表示する主な方法です。 では[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、 <xref:System.Windows.Controls.Image> 2 つの方法で使用できます。属性構文またはプロパティ構文。 次の例は、属性構文とプロパティ タグ構文の両方を使用して、幅 200 ピクセルのイメージをレンダリングする方法を示しています。 属性の構文とプロパティの構文の詳細については、[Dependency Properties Overview](../advanced/dependency-properties-overview.md)を参照してください。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 多くの例では、オブジェクト<xref:System.Windows.Media.Imaging.BitmapImage>を使用してイメージ ファイルを参照しています。 <xref:System.Windows.Media.Imaging.BitmapImage>は、読み<xref:System.Windows.Media.Imaging.BitmapSource>込み用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]に最適化された特殊なものであり、コントロールのイメージを<xref:System.Windows.Controls.Image.Source%2A>表示する簡単な<xref:System.Windows.Controls.Image>方法です。  
  
 次の例では、コードを使用して幅 200 ピクセルのイメージをレンダリングする方法を示します。  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage>は、複数<xref:System.ComponentModel.ISupportInitialize>のプロパティの初期化を最適化するインターフェイスを実装します。 プロパティの変更は、オブジェクトの初期化中にのみ実行できます。 初期化<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>が開始されたことを通知し、初期化<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>が完了したことを通知する呼び出し。 初期化の完了後は、プロパティの変更は無視されます。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>イメージの回転、変換、およびクロップ  
 WPF を使用すると、ユーザーは の<xref:System.Windows.Media.Imaging.BitmapImage>プロパティを使用するか<xref:System.Windows.Media.Imaging.BitmapSource>、<xref:System.Windows.Media.Imaging.CroppedBitmap>または などの<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>追加のオブジェクトを使用してイメージを変換できます。 これらのイメージの変換では、イメージの拡大縮小、回転、ピクセル形式の変更、またはクロップを行うことができます。  
  
 イメージの回転は、 の<xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A><xref:System.Windows.Media.Imaging.BitmapImage>プロパティを使用して実行されます。 回転は、90 ° 単位でのみ実行できます。 次の例では、イメージが 90 ° 回転します。  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 イメージをグレースケールなどの別のピクセル形式に変換するには、 を<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>使用します。 次の例では、イメージが に<xref:System.Windows.Media.PixelFormats.Gray4%2A>変換されます。  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 イメージをトリミングするには、プロパティまたは<xref:System.Windows.UIElement.Clip%2A>の<xref:System.Windows.Controls.Image>プロパティ<xref:System.Windows.Media.Imaging.CroppedBitmap>を使用できます。 通常、画像の一部を表示するだけの場合は、<xref:System.Windows.UIElement.Clip%2A>使用する必要があります。 トリミングした画像をエンコードして保存する必要がある場合は、<xref:System.Windows.Media.Imaging.CroppedBitmap>を使用する必要があります。 次の例では、Clip プロパティを使用してイメージを<xref:System.Windows.Media.EllipseGeometry>トリミングします。  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>イメージの引き伸ばし  
 プロパティ<xref:System.Windows.Controls.Image.Stretch%2A>は、イメージをコンテナーに拡大する方法を制御します。 この<xref:System.Windows.Controls.Image.Stretch%2A>プロパティは、列挙体によって定義される次の<xref:System.Windows.Media.Stretch>値を受け入れます。  
  
- <xref:System.Windows.Media.Stretch.None>: 出力領域を埋めるために画像が伸長されていません。 イメージが出力領域よりも大きい場合は、出力領域に収まらない部分がクリップされたイメージが出力領域に描画されます。  
  
- <xref:System.Windows.Media.Stretch.Fill>: 出力領域に合わせて画像が拡大縮小されます。 イメージの高さと幅は個別に拡大縮小されるため、イメージの元の縦横比は保持されないことがあります。 つまり、イメージは、出力コンテナーを完全に埋めるためにゆがんで表示される可能性があります。  
  
- <xref:System.Windows.Media.Stretch.Uniform>: 画像は出力領域内に完全に収まるように拡大縮小されます。 イメージの縦横比は保持されます。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: イメージの元の縦横比を維持したまま、出力領域全体が完全に塗りつぶされるように、イメージが拡大/縮小されます。  
  
 次の例では、使用可能な<xref:System.Windows.Media.Stretch>各列挙体を<xref:System.Windows.Controls.Image>に適用します。  
  
 次の図は、例の出力を示し、イメージ<xref:System.Windows.Controls.Image.Stretch%2A>に適用した場合のさまざまな設定が与える影響を示しています。  
  
 ![異なる TileBrush Stretch 設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
異なる Stretch 設定  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>イメージによる塗りつぶし  
 イメージは、 でペイントすることでアプリケーションに表示することもできます<xref:System.Windows.Media.Brush>。 ブラシを使用すると、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] オブジェクトを単色で塗りつぶすことも、パターンとイメージの複雑な組み合わせで塗りつぶすこともできます。 イメージでペイントするには、 を<xref:System.Windows.Media.ImageBrush>使用します。 A<xref:System.Windows.Media.ImageBrush>は、その<xref:System.Windows.Media.TileBrush>コンテンツをビットマップ イメージとして定義する型です。 プロパティ<xref:System.Windows.Media.ImageBrush>で指定された単一のイメージを<xref:System.Windows.Media.ImageBrush.ImageSource%2A>表示します。 イメージがゆがまないようしたり、パターンやその他の効果を作成したりするために、イメージの伸縮、配置、およびタイル表示方法を制御できます。 次の図は、 で実現できる効果をいくつか示<xref:System.Windows.Media.ImageBrush>しています。  
  
 ![ImageBrush の出力例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
イメージ ブラシは、図形、コントロール、テキストなどを塗りつぶすことができる  
  
 次の例は、 を使用して、ボタンの背景をイメージで描画する<xref:System.Windows.Media.ImageBrush>方法を示しています。  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 イメージの詳細<xref:System.Windows.Media.ImageBrush>およびペイントについては、「[イメージ、描画、およびビジュアルを使用したペイント](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="_metadata"></a>
## <a name="image-metadata"></a>イメージのメタデータ  
 一部のイメージ ファイルには、ファイルの内容または特性を記述するメタデータが含まれています。 たとえば、ほとんどのデジタル カメラは、イメージをキャプチャするために使用されるカメラの型番に関するメタデータを含むイメージを作成します。 各イメージ形式はメタデータを異なる方法で処理しますが、WPF イメージングは、サポートされている各イメージ形式のメタデータを格納および取得する統一された方法を提供します。  
  
 メタデータへのアクセスは、オブジェクトのプロパティ<xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>を<xref:System.Windows.Media.Imaging.BitmapSource>通じて提供されます。 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>は、<xref:System.Windows.Media.Imaging.BitmapMetadata>イメージに含まれるすべてのメタデータを含むオブジェクトを返します。 このデータは、1 つのメタデータ スキーマでも、異なるスキーマの組み合わせでもかまいません。 WPF イメージングでは、交換可能なイメージ ファイル (Exif)、tEXt (PNG テキスト データ)、イメージ ファイル ディレクトリ (IFD)、国際プレス通信協議会 (IPTC)、および拡張メタデータ プラットフォーム (XMP) のイメージ メタデータ スキーマがサポートされています。  
  
 メタデータの読み取りプロセスを簡略化するために、 <xref:System.Windows.Media.Imaging.BitmapMetadata> <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>、 など<xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>、簡単にアクセスできるいくつかの名前付きプロパティ<xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>を提供します。 これらの名前付きプロパティの多くは、メタデータを書き込むためにも使用できます。 メタデータを読み取るための追加サポートは、メタデータ クエリ リーダーによって提供されます。 この<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>メソッドは *、"/app1/exif/"* などの文字列クエリを提供することによって、メタデータ クエリ リーダーを取得するために使用されます。 次の例では<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>*、"/Text/Description"* の場所に格納されているテキストを取得するために使用します。  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 メタデータを書き込むには、メタデータ クエリ ライターが使用されます。 <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>クエリ ライターを取得し、目的の値を設定します。 次の例では<xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>*、"/Text/Description"* の場所に格納されているテキストを書き込むために使用します。  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>
## <a name="codec-extensibility"></a>コーデックの機能拡張  
 WPF イメージングのコア機能は、新しいイメージ コーデックの機能拡張モデルです。 これらのアンマネージ インターフェイスを使用すると、コーデック開発者は、WPF アプリケーションで新しいイメージ形式を自動的に使用できるように、WPF とコーデックを統合できます。  
  
 機能拡張 API のサンプルについては、 [Win32 サンプル コーデック](https://go.microsoft.com/fwlink/?LinkID=160052)を参照してください。 このサンプルは、カスタム イメージ形式用のデコーダーとエンコーダーの作成方法を示しています。  
  
> [!NOTE]
> システムで認識するは、コーデックをデジタル署名する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 サンプル コーデック](https://go.microsoft.com/fwlink/?LinkID=160052)
