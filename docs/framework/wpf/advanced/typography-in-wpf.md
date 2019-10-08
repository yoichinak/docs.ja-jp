---
title: WPF のタイポグラフィ
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 11087ed4da23d73fc8edc36680dd1b3587c011ce
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004930"
---
# <a name="typography-in-wpf"></a>WPF のタイポグラフィ
このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の主要な文字体裁の機能について説明します。 これらの機能には、テキストレンダリングの品質とパフォーマンスの向上、OpenType 文字体裁のサポート、強化されたインターナショナルテキスト、フォントサポートの強化、および新しいテキストアプリケーションプログラミングインターフェイス (Api) が含まれます。  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>テキストに関する品質とパフォーマンスの向上  
 @No__t-0 のテキストは Microsoft ClearType を使用して表示されます。これにより、テキストの明瞭さと読みやすさが向上します。 ClearType は、Microsoft によって開発されたソフトウェアテクノロジで、ラップトップの画面、Pocket PC の画面、フラットパネルモニターなど、既存の Lcd (液晶ディスプレイ) でのテキストの読みやすさを向上させます。 ClearType では、ピクセルレンダリングが使用されます。これにより、ピクセルの小数部に文字を配置することで、実際の図形に対する忠実度の高いテキストを表示できます。 解像度が上がるとテキスト表示の微細部の鮮明度が高くなるため、長時間にわたって読んでも苦になりません。 @No__t 0 での ClearType のもう1つの改良点は、y 方向のアンチエイリアシングです。これにより、テキスト文字での浅い曲線の上部と下部を滑らかにすることができます。 ClearType 機能の詳細については、「 [cleartype の概要](cleartype-overview.md)」を参照してください。  
  
 ![ClearType y 方向アンチエイリアシングを含むテキスト](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
ClearType の y 方向アンチエイリアシングを適用したテキスト  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、コンピューターがハードウェアの最小要件を満たしている限り、テキスト レンダリング パイプライン全体に対してハードウェア アクセラレータを使用できます。 ハードウェアを使用して実行できないレンダリングは、ソフトウェア レンダリングとなります。 ハードウェアアクセラレータは、テキストレンダリングパイプラインのすべてのフェーズに影響を及ぼします。これは、個々のグリフの格納、グリフの実行へのグリフの合成、効果の適用、最終的に表示される出力への ClearType ブレンディングアルゴリズムの適用に関するものです。 ハードウェア アクセラレータの詳細については、「[グラフィックスの描画層](graphics-rendering-tiers.md)」をご覧ください。  
  
 ![パイプラインを描画するテキストのダイアグラム](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 また、アニメーション化されたテキストは、文字とグリフのいずれによる場合でも、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で有効化されているグラフィックス ハードウェア機能をすべて利用できます。 これにより、テキスト アニメーションが滑らかになります。  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>多彩な文字体裁  
 OpenType フォント形式は、TrueType®フォント形式を拡張したものです。 OpenType フォント形式は、Microsoft と Adobe が共同で開発したものであり、高度な文字体裁機能が豊富に用意されています。 @No__t 0 オブジェクトは、スタイルの代替や巻きひげなど、OpenType フォントの高度な機能の多くを公開します。 Windows SDK には、Pericles や Pescadero フォントなどの豊富な機能を使用して設計されたサンプルの OpenType フォントのセットが用意されています。 詳細については、「[OpenType フォント パックのサンプル](sample-opentype-font-pack.md)」をご覧ください。  
  
 Pericles OpenType フォントには、グリフの標準セットに対してスタイルの代替を提供する追加のグリフが含まれています。 次のテキストでは、スタイル代替グリフが表示されています。  
  
 ![Opentype のスタイル代替グリフ]を使用したテキスト(./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "opentype のスタイルの代替グリフを使用し")たテキスト  
  
 スワッシュは装飾的なグリフで、カリグラフィを連想させることがよくある、手の込んだ装飾が使用されます。 次のテキストは、Pescadero フォントの標準グリフと巻きひげグリフを示しています。  
  
 Opentype の標準とスワッシュ字形を(./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "使用")した![テキストと、opentype の標準]およびスワッシュ字形を使用したテキスト  
  
 OpenType 機能の詳細については、「 [Opentype フォントの機能](opentype-font-features.md)」を参照してください。  
  
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
  
- @No__t-0、<xref:System.Windows.FontStretch>、<xref:System.Windows.FontStyle> の各型を分離して、@no__t を定義します。 これにより、斜体と太字のブール値の組み合わせでフォント ファミリを定義する [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] プログラミングよりも優れた柔軟性が提供されます。  
  
- フォント名とは関係なく処理される書き込み方向 (横書きまたは縦書き)。  
  
- 複合フォント技術を使用した、移植可能な [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ファイルにおけるフォント リンクとフォントの代替。 複合フォントは、完全な多言語フォントの構築を可能にします。 また、複合フォントは、欠落グリフの表示を防ぐ機能も備えています。 詳細については、<xref:System.Windows.Media.FontFamily> クラスの解説を参照してください。  
  
- 単一言語フォントのグループを使用した、複合フォントから構築される国際対応フォント。 これにより、複数言語に対応するフォントの開発時にリソースのコストを節約できます。  
  
- ドキュメントに埋め込むことで移植性が得られる複合フォント。 詳細については、<xref:System.Windows.Media.FontFamily> クラスの解説を参照してください。  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>新しいテキスト API (アプリケーション プログラミング インターフェイス)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、開発者がアプリケーションにテキストを含めるときに使用するテキスト Api がいくつか用意されています。 これらの Api は、次の3つのカテゴリに分類されます。  
  
- **レイアウトとユーザー インターフェイス**: グラフィカルユーザーインターフェイス (GUI) 用の一般的なテキストコントロール。  
  
- **軽量テキスト描画**: オブジェクトにテキストを直接描画できます。  
  
- **テキストの高度な書式設定**: カスタム テキスト エンジンを実装できます。  
  
### <a name="layout-and-user-interface"></a>レイアウトとユーザー インターフェイス  
 最高レベルの機能では、text Api は、<xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.TextBlock>、<xref:System.Windows.Controls.TextBox> などの一般的な @no__t 0 コントロールを提供します。 これらのコントロールは、アプリケーション内に基本的な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を提供し、テキストの表示や操作を簡単に実行できるようにします。 @No__t-0 や <xref:System.Windows.Controls.PasswordBox> などのコントロールを使用すると、より高度なテキスト処理を行うことができます。 @No__t-0、<xref:System.Windows.Documents.TextSelection>、<xref:System.Windows.Documents.TextPointer> などのクラスを使用すると、便利なテキスト操作を行うことができます。 これらの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] コントロールは、<xref:System.Windows.Controls.Control.FontFamily%2A>、<xref:System.Windows.Controls.Control.FontSize%2A>、<xref:System.Windows.Controls.Control.FontStyle%2A> などのプロパティを提供します。これにより、テキストの表示に使用するフォントを制御できます。  
  
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
  
 @No__t 0 オブジェクトは、テキスト文字列内の1つまたは複数の文字グループとしてテキストを扱うことができるヘルパーオブジェクトです。 次の例は、回転する個々の文字を示しています。 各文字は、1 秒間隔で個別に回転します。  
  
 ![テキストを回転するテキスト効果のスクリーンショット](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>フロー ドキュメントの使用  
 一般的な @no__t 0 コントロールに加えて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、テキスト表示 (<xref:System.Windows.Documents.FlowDocument> 要素) のレイアウトコントロールが用意されています。 @No__t-0 要素は、<xref:System.Windows.Controls.DocumentViewer> 要素と共に、さまざまなレイアウト要件を持つ大量のテキストのコントロールを提供します。 レイアウトコントロールは、他の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] コントロールの @no__t 0 オブジェクトおよびフォント関連のプロパティを使用して高度なタイポグラフィにアクセスできるようにします。  
  
 次の例は、検索、ナビゲーション、改ページ調整、およびコンテンツスケーリングのサポートを提供する @no__t 0 でホストされるテキストコンテンツを示しています。  
  
 ![OpenType フォントを示すスクリーンショット。](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 詳細については、「[WPF のドキュメント](documents-in-wpf.md)」を参照してください。  
  
### <a name="lightweight-text-drawing"></a>軽量テキスト描画  
 @No__t-2 オブジェクトの <xref:System.Windows.Media.DrawingContext.DrawText%2A> メソッドを使用して、@no__t 0 のオブジェクトにテキストを直接描画できます。 このメソッドを使用するには、@no__t 0 オブジェクトを作成します。 このオブジェクトを使用すると、複数行のテキストを描画できます。このテキストでは、テキスト内の各文字を個々に書式設定できます。 @No__t-0 オブジェクトの機能には、Windows API の DrawText フラグの機能の多くが含まれています。 また、@no__t 0 のオブジェクトには、省略記号のサポートなどの機能が含まれており、テキストの境界を超えたときに省略記号が表示されます。 いくつかの書式を適用したテキストを次の例に示します。たとえば、2 番目と 3 番目の単語には線状グラデーションが適用されています。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 書式設定されたテキストを @no__t 0 のオブジェクトに変換して、他の種類の視覚的に興味のあるテキストを作成できます。 たとえば、テキスト文字列のアウトラインに基づいて @no__t 0 オブジェクトを作成できます。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 変換されたテキストのストローク、塗りつぶし、強調表示を変更して、人の目をひく視覚効果を作成するいくつかの方法を次の例に示します。  
  
 ![塗りつぶしとストロークに別の色を使用するテキスト](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![ストロークと強調表示に適用されたイメージブラシを含むテキスト](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 @No__t 0 オブジェクトの詳細については、「[書式設定](drawing-formatted-text.md)されたテキストの描画」を参照してください。  
  
### <a name="advanced-text-formatting"></a>テキストの高度な書式設定  
 テキスト Api の最も高度なレベルでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を使用すると、<xref:System.Windows.Media.TextFormatting> 名前空間の <xref:System.Windows.Media.TextFormatting.TextFormatter> オブジェクトとその他の型を使用して、カスタムテキストレイアウトを作成できます。 @No__t 0 と関連クラスを使用すると、独自の文字形式、段落スタイル、改行規則、およびその他の国際対応テキストのレイアウト機能をサポートするカスタムテキストレイアウトを実装できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テキスト レイアウト サポートに関する既定の実装のオーバーライドが必要となるケースはほとんどありません。 ただし、テキストを編集するコントロールやアプリケーションを作成する場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既定の実装とは異なる実装が必要になることがあります。  
  
 従来のテキスト API とは異なり、<xref:System.Windows.Media.TextFormatting.TextFormatter> は、一連のコールバックメソッドを使用してテキストレイアウトクライアントと対話します。 クライアントは、@no__t 0 クラスの実装でこれらのメソッドを提供する必要があります。 次の図は、クライアントアプリケーションと <xref:System.Windows.Media.TextFormatting.TextFormatter> の間のテキストレイアウトの相互作用を示しています。  
  
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
