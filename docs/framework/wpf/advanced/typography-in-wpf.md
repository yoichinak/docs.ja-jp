---
title: WPF のタイポグラフィ
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 818d013356c3ca8151e9b5bb675bce4726759f6c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710347"
---
# <a name="typography-in-wpf"></a>WPF のタイポグラフィ
このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の主要な文字体裁の機能について説明します。 これらの機能には、テキスト レンダリングの品質とパフォーマンスの向上、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 文字体裁のサポート、国際対応テキストの強化、フォントのサポートの強化、新しいテキスト API (アプリケーション プログラミング インターフェイス) が含まれます。  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>テキストに関する品質とパフォーマンスの向上  
 の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テキストは Microsoft ClearType を使用してレンダリングされます。これにより、テキストの明瞭さと読みやすさが向上します。 ClearType は、によって[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]開発されたソフトウェアテクノロジで、ラップトップの画面、Pocket PC の画面、フラットパネルモニターなど、既存の lcd (液晶ディスプレイ) でのテキストの読みやすさを向上させます。 ClearType では、ピクセルレンダリングが使用されます。これにより、ピクセルの小数部に文字を配置することで、実際の図形に対する忠実度の高いテキストを表示できます。 解像度が上がるとテキスト表示の微細部の鮮明度が高くなるため、長時間にわたって読んでも苦になりません。 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の ClearType のもう1つの改良点は、y 方向のアンチエイリアシングです。これにより、テキスト文字での浅い曲線の上部および下部を滑らかにすることができます。 ClearType 機能の詳細については、「 [cleartype の概要](cleartype-overview.md)」を参照してください。  
  
 ![ClearType y 方向アンチエイリアシングを含むテキスト](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
ClearType の y 方向アンチエイリアシングを適用したテキスト  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、コンピューターがハードウェアの最小要件を満たしている限り、テキスト レンダリング パイプライン全体に対してハードウェア アクセラレータを使用できます。 ハードウェアを使用して実行できないレンダリングは、ソフトウェア レンダリングとなります。 ハードウェアアクセラレータは、テキストレンダリングパイプラインのすべてのフェーズに影響を及ぼします。これは、個々のグリフの格納、グリフの実行へのグリフの合成、効果の適用、最終的に表示される出力への ClearType ブレンディングアルゴリズムの適用に関するものです。 ハードウェア アクセラレータの詳細については、「[グラフィックスの描画層](graphics-rendering-tiers.md)」をご覧ください。  
  
 ![パイプラインを描画するテキストのダイアグラム](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 また、アニメーション化されたテキストは、文字とグリフのいずれによる場合でも、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で有効化されているグラフィックス ハードウェア機能をすべて利用できます。 これにより、テキスト アニメーションが滑らかになります。  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>多彩な文字体裁  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォント形式は、[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] フォント形式の拡張です。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォント形式は、[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] と Adobe が共同で開発したもので、高度な文字体裁機能を豊富に備えています。 オブジェクト<xref:System.Windows.Documents.Typography>は、スタイルの代替やスワッシュ字[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]など、フォントの高度な機能の多くを公開します。 [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] には、Pericles フォントや Pescadero フォントなど、豊富な機能を持つ [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォント サンプルが用意されています。 詳細については、「[OpenType フォント パックのサンプル](sample-opentype-font-pack.md)」をご覧ください。  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォントには、標準グリフ セットにスタイル代替グリフを提供する追加グリフが含まれています。 次のテキストでは、スタイル代替グリフが表示されています。  
  
 ![OpenType のスタイル代替グリフを使用するテキスト](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "OpenType のスタイル代替グリフを使用するテキスト")  
  
 スワッシュは装飾的なグリフで、カリグラフィを連想させることがよくある、手の込んだ装飾が使用されます。 次のテキストは、Pescadero フォントの標準グリフと巻きひげグリフを示しています。  
  
 ![OpenType の標準グリフとスワッシュ字形を使用したテキスト](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "OpenType の標準グリフとスワッシュ字形を使用したテキスト")  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] の機能の詳細については、「[OpenType フォントの機能](opentype-font-features.md)」をご覧ください。  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>国際対応テキストのサポートの強化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、次の機能を提供することで、国際対応テキストのサポートを強化しています。  
  
- すべての書記体系における、適用可能な単位を使用した自動行間隔設定。  
  
- 国際対応テキストの幅広いサポート。 詳細については、「[WPF のグローバリゼーション](globalization-for-wpf.md)」をご覧ください。  
  
- 言語に合わせた改行、ハイフネーション、両端揃え。  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>フォントのサポートの強化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、次の機能を提供することで、フォントのサポートを強化しています。  
  
- すべてのテキストに対応する Unicode。 フォントの動作や選択に文字セットやコードページが不要になりました。  
  
- システム ロケールなど、グローバル設定に左右されないフォント動作。  
  
- を定義するため<xref:System.Windows.FontStyle>に、、 <xref:System.Windows.FontWeight> <xref:System.Windows.Media.FontFamily>、およびの各型を区切ります。 <xref:System.Windows.FontStretch> これにより、斜体と太字のブール値の組み合わせでフォント ファミリを定義する [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] プログラミングよりも優れた柔軟性が提供されます。  
  
- フォント名とは関係なく処理される書き込み方向 (横書きまたは縦書き)。  
  
- 複合フォント技術を使用した、移植可能な [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ファイルにおけるフォント リンクとフォントの代替。 複合フォントは、完全な多言語フォントの構築を可能にします。 また、複合フォントは、欠落グリフの表示を防ぐ機能も備えています。 詳細については、 <xref:System.Windows.Media.FontFamily>クラスの「解説」を参照してください。  
  
- 単一言語フォントのグループを使用した、複合フォントから構築される国際対応フォント。 これにより、複数言語に対応するフォントの開発時にリソースのコストを節約できます。  
  
- ドキュメントに埋め込むことで移植性が得られる複合フォント。 詳細については、 <xref:System.Windows.Media.FontFamily>クラスの「解説」を参照してください。  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>新しいテキスト API (アプリケーション プログラミング インターフェイス)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、開発者がアプリケーションにテキストを含めるときに使用するテキスト Api がいくつか用意されています。 これらの Api は、次の3つのカテゴリに分類されます。  
  
- **レイアウトとユーザー インターフェイス**: グラフィカルユーザーインターフェイス (GUI) 用の一般的なテキストコントロール。  
  
- **軽量テキスト描画**: オブジェクトにテキストを直接描画できます。  
  
- **テキストの高度な書式設定**: カスタム テキスト エンジンを実装できます。  
  
### <a name="layout-and-user-interface"></a>レイアウトとユーザー インターフェイス  
 最高レベルの機能では[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 、text api は<xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox>、などの一般的なコントロールを提供します。 これらのコントロールは、アプリケーション内に基本的な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を提供し、テキストの表示や操作を簡単に実行できるようにします。 やなどのコントロール<xref:System.Windows.Controls.PasswordBox>を使用すると、より高度なテキスト処理を行うことができます。 <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Documents.TextRange>、 <xref:System.Windows.Documents.TextSelection> 、<xref:System.Windows.Documents.TextPointer>などのクラスを使用すると、便利なテキスト操作を行うことができます。 これら[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のコントロールは<xref:System.Windows.Controls.Control.FontFamily%2A>、 <xref:System.Windows.Controls.Control.FontSize%2A>、、 <xref:System.Windows.Controls.Control.FontStyle%2A>などのプロパティを提供します。このプロパティを使用すると、テキストの表示に使用するフォントを制御できます。  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>ビットマップ効果、変換、テキスト効果の使用  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、ビットマップ効果、変換、テキスト効果などの機能を利用して、人の目をひきつけるテキストを作成できます。 テキストに標準タイプのドロップ シャドウ効果を適用した例を次に示します。  
  
 ![ぼかし&#61; 0.25 を使用したテキストシャドウ](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
 テキストにドロップ シャドウ効果とノイズを適用した例を次に示します。  
  
 ![ノイズを含むテキスト シャドウ](./media/typography-in-wpf/drop-shadow-noise-text.jpg) 
  
 テキストの外縁にグロー効果を適用した例を次に示します。  
  
 ![OuterGlowBitmapEffect を使用するテキスト シャドウ](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 テキストにぼかし効果が適用されている例を次に示します。  
  
 ![BlurBitmapEffect を使用するテキスト シャドウ](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 テキストの 2 行目を x 軸に沿って 150% 拡大し、3 行目を y 軸に沿って 150% 拡大した例を次に示します。  
  
 ![ScaleTransform を使用してスケールされたテキスト](./media/typography-in-wpf/scaled-text-scaletransform.jpg) 
  
 x 軸に沿って傾斜させたテキストの例を次に示します。  
  
 ![SkewTransform を使用して傾斜させたテキスト](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 <xref:System.Windows.Media.TextEffect>オブジェクトは、テキスト文字列内の1つまたは複数の文字グループとしてテキストを扱うことができるヘルパーオブジェクトです。 次の例は、回転する個々の文字を示しています。 各文字は、1 秒間隔で個別に回転します。  
  
 ![テキストを回転するテキスト効果のスクリーンショット](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>フロー ドキュメントの使用  
 コモン[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コントロールに加えて、で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、テキスト表示 ( <xref:System.Windows.Documents.FlowDocument>要素) のレイアウトコントロールが用意されています。 <xref:System.Windows.Documents.FlowDocument> 要素<xref:System.Windows.Controls.DocumentViewer>と要素は、さまざまなレイアウト要件を持つ大量のテキストのコントロールを提供します。 レイアウトコントロールは、 <xref:System.Windows.Documents.Typography>他の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コントロールのオブジェクトおよびフォント関連のプロパティを使用して高度なタイポグラフィにアクセスできるようにします。  
  
 次の例は、で<xref:System.Windows.Controls.FlowDocumentReader>ホストされるテキストコンテンツを示しています。これは、検索、ナビゲーション、改ページ調整、およびコンテンツスケーリングのサポートを提供します。  
  
 ![OpenType フォントを示すスクリーンショット。](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 詳細については、「[WPF のドキュメント](documents-in-wpf.md)」を参照してください。  
  
### <a name="lightweight-text-drawing"></a>軽量テキスト描画  
 オブジェクトの<xref:System.Windows.Media.DrawingContext.DrawText%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] メソッドを使用して、テキストを直接オブジェクトに描画できます<xref:System.Windows.Media.DrawingContext> 。 このメソッドを使用するには、 <xref:System.Windows.Media.FormattedText>オブジェクトを作成します。 このオブジェクトを使用すると、複数行のテキストを描画できます。このテキストでは、テキスト内の各文字を個々に書式設定できます。 <xref:System.Windows.Media.FormattedText>オブジェクトの機能には、Windows API の DrawText フラグの機能の多くが含まれています。 また、オブジェクトに<xref:System.Windows.Media.FormattedText>は、テキストの境界を超えたときに省略記号が表示される、省略記号のサポートなどの機能が含まれています。 いくつかの書式を適用したテキストを次の例に示します。たとえば、2 番目と 3 番目の単語には線状グラデーションが適用されています。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 書式設定されたテキスト<xref:System.Windows.Media.Geometry>をオブジェクトに変換することで、他の種類の視覚的に面白いテキストを作成できます。 たとえば、テキスト文字列のアウトラインに<xref:System.Windows.Media.Geometry>基づいてオブジェクトを作成できます。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 変換されたテキストのストローク、塗りつぶし、強調表示を変更して、人の目をひく視覚効果を作成するいくつかの方法を次の例に示します。  
  
 ![塗りつぶしとストロークに別の色を使用するテキスト](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![ストロークと強調表示に適用されたイメージブラシを含むテキスト](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 オブジェクトの詳細につい<xref:System.Windows.Media.FormattedText>ては、「[書式設定](drawing-formatted-text.md)されたテキストの描画」を参照してください。  
  
### <a name="advanced-text-formatting"></a>テキストの高度な書式設定  
 テキスト api の最も高度なレベルでは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Media.TextFormatting.TextFormatter>オブジェクト<xref:System.Windows.Media.TextFormatting>や名前空間のその他の型を使用して、カスタムテキストレイアウトを作成することができます。 <xref:System.Windows.Media.TextFormatting.TextFormatter>および関連クラスを使用すると、独自の文字形式の定義、段落スタイル、改行規則、およびその他の国際対応テキストのレイアウト機能をサポートするカスタムテキストレイアウトを実装できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テキスト レイアウト サポートに関する既定の実装のオーバーライドが必要となるケースはほとんどありません。 ただし、テキストを編集するコントロールやアプリケーションを作成する場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既定の実装とは異なる実装が必要になることがあります。  
  
 従来のテキスト API とは異なり<xref:System.Windows.Media.TextFormatting.TextFormatter> 、は、一連のコールバックメソッドを使用してテキストレイアウトクライアントと対話します。 クライアントは、 <xref:System.Windows.Media.TextFormatting.TextSource>クラスの実装でこれらのメソッドを提供する必要があります。 次の図は、クライアントアプリケーションと<xref:System.Windows.Media.TextFormatting.TextFormatter>の間のテキストレイアウトの相互作用を示しています。  
  
 ![テキスト レイアウト クライアントと TextFormatter のダイアグラム](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 カスタム テキスト レイアウトの作成の詳細については、「[テキストの高度な書式設定](advanced-text-formatting.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType の概要](cleartype-overview.md)
- [OpenType フォントの機能](opentype-font-features.md)
- [書式設定されたテキストの描画](drawing-formatted-text.md)
- [テキストの高度な書式設定](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Microsoft の文字体裁](https://docs.microsoft.com/typography/)
