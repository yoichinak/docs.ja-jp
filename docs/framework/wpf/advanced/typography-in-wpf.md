---
title: タイポグラフィ
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 501a4221c99d405484a2fb908641d27d1f38f266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187349"
---
# <a name="typography-in-wpf"></a>WPF のタイポグラフィ
このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の主要な文字体裁の機能について説明します。 これらの機能には、テキストレンダリングの品質とパフォーマンスの向上、OpenType タイポグラフィのサポート、拡張された国際テキスト、拡張フォントサポート、新しいテキストアプリケーションプログラミングインタフェース(API)などがあります。  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>
## <a name="improved-quality-and-performance-of-text"></a>テキストに関する品質とパフォーマンスの向上  
 テキストの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]表示は、テキストのわかりやすさと読みやすさを向上させる Microsoft ClearType を使用してレンダリングされます。 ClearType は、ラップトップの画面、ポケット PC 画面、フラット パネル モニターなどの既存の LCD (液晶ディスプレイ) 上のテキストの読みやすさを向上させるマイクロソフトが開発したソフトウェア テクノロジです。 ClearType は、ピクセルの小数部分に文字を揃えることで、テキストを実際の図形に忠実に表示できるサブピクセル レンダリングを使用します。 解像度が上がるとテキスト表示の微細部の鮮明度が高くなるため、長時間にわたって読んでも苦になりません。 ClearType のもう 1[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]つの改善点は、y 方向アンチエイリアシングで、テキスト文字の浅いカーブの上部と下部を滑らかにします。 ClearType 機能の詳細については、「 [ClearType の概要](cleartype-overview.md)」を参照してください。  
  
 ![ClearType y 方向アンチエイリアシングを含むテキスト](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
ClearType の y 方向アンチエイリアシングを適用したテキスト  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、コンピューターがハードウェアの最小要件を満たしている限り、テキスト レンダリング パイプライン全体に対してハードウェア アクセラレータを使用できます。 ハードウェアを使用して実行できないレンダリングは、ソフトウェア レンダリングとなります。 ハードウェア アクセラレーションは、個々のグリフの格納、グリフの実行へのグリフの合成、効果の適用、最終的な表示出力への ClearType ブレンド アルゴリズムの適用など、テキスト レンダリング パイプラインのすべてのフェーズに影響します。 ハードウェア アクセラレータの詳細については、「[グラフィックスの描画層](graphics-rendering-tiers.md)」をご覧ください。  
  
 ![パイプラインを描画するテキストのダイアグラム](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 また、アニメーション化されたテキストは、文字とグリフのいずれによる場合でも、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で有効化されているグラフィックス ハードウェア機能をすべて利用できます。 これにより、テキスト アニメーションが滑らかになります。  
  
<a name="Rich_Typography"></a>
## <a name="rich-typography"></a>多彩な文字体裁  
 OpenType フォント形式は、TrueType® フォント形式の拡張機能です。 OpenType フォント形式は、マイクロソフトとアドビによって共同で開発され、高度なタイポグラフィ機能の豊富な品揃えを提供します。 この<xref:System.Windows.Documents.Typography>オブジェクトは、スタイルの代替や swashe など、OpenType フォントの高度な機能の多くを公開します。 Windows SDK には、Pericles やペスカデロなどの豊富な機能を使用して設計された OpenType フォントのサンプル セットが用意されています。 詳細については、「[OpenType フォント パックのサンプル](sample-opentype-font-pack.md)」を参照してください。  
  
 Pericles OpenType フォントには、標準のグリフセットに対するスタイルの代替を提供する追加のグリフが含まれています。 次のテキストでは、スタイル代替グリフが表示されています。  
  
 ![OpenType のスタイル代替グリフを使用するテキスト](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "OpenType のスタイル代替グリフを使用するテキスト")  
  
 飾り付きは装飾的なグリフで、カリグラフィを連想させる、手の込んだ装飾が使用されます。 次のテキストは、ペスカデロフォントの標準およびスワッシュグリフを表示します。  
  
 ![OpenType の標準グリフと飾り付きグリフを使用するテキスト](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "OpenType の標準グリフと飾り付きグリフを使用するテキスト")  
  
 OpenType 機能の詳細については、「 [OpenType フォント機能](opentype-font-features.md)」を参照してください。  
  
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
  
- を<xref:System.Windows.FontWeight>定義<xref:System.Windows.FontStretch>するための、 <xref:System.Windows.FontStyle> 、、および<xref:System.Windows.Media.FontFamily>の各型を分離します。 これにより、フォント ファミリを定義するために斜体と太字のブール値の組み合わせを使用する Win32 プログラミングよりも柔軟性が高くなります。  
  
- フォント名とは関係なく処理される書き込み方向 (横書きまたは縦書き)。  
  
- フォントリンクとフォントフォールバックは、合成フォント技術を使用して、ポータブル XML ファイルで。 複合フォントは、完全な多言語フォントの構築を可能にします。 また、複合フォントは、欠落グリフの表示を防ぐ機能も備えています。 詳細については、クラスの解説を<xref:System.Windows.Media.FontFamily>参照してください。  
  
- 単一言語フォントのグループを使用した、複合フォントから構築される国際対応フォント。 これにより、複数言語に対応するフォントの開発時にリソースのコストを節約できます。  
  
- ドキュメントに埋め込むことで移植性が得られる複合フォント。 詳細については、クラスの解説を<xref:System.Windows.Media.FontFamily>参照してください。  
  
<a name="New_Text_APIs"></a>
## <a name="new-text-application-programming-interfaces-apis"></a>新しいテキスト API (アプリケーション プログラミング インターフェイス)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、アプリケーションにテキストを含める開発者向けのテキスト API がいくつか用意されています。 これらの API は、次の 3 つのカテゴリに分類されます。  
  
- **レイアウトとユーザー インターフェイス**: グラフィカル・ユーザー・インターフェース (GUI) の共通テキスト制御。  
  
- **軽量テキスト描画**: オブジェクトにテキストを直接描画できます。  
  
- **高度なテキストフォーマット**: カスタム テキスト エンジンを実装できます。  
  
### <a name="layout-and-user-interface"></a>レイアウトとユーザー インターフェイス  
 機能の最上位レベルでは、テキスト API は、 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 、<xref:System.Windows.Controls.Label><xref:System.Windows.Controls.TextBlock>および などの一般的<xref:System.Windows.Controls.TextBox>なコントロールを提供します。 これらのコントロールは、アプリケーション内に基本的な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を提供し、テキストの表示や操作を簡単に実行できるようにします。 より高度な<xref:System.Windows.Controls.RichTextBox><xref:System.Windows.Controls.PasswordBox>、または特殊なテキスト処理を有効にするなどのコントロール。 また、<xref:System.Windows.Documents.TextRange><xref:System.Windows.Documents.TextSelection>などのクラスは、<xref:System.Windows.Documents.TextPointer>有用なテキスト操作を可能にします。 これらの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コントロールには、 、<xref:System.Windows.Controls.Control.FontFamily%2A><xref:System.Windows.Controls.Control.FontSize%2A>および<xref:System.Windows.Controls.Control.FontStyle%2A>などのプロパティが用意されており、テキストのレンダリングに使用するフォントを制御できます。  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>ビットマップ効果、変換、テキスト効果の使用  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、ビットマップ効果、変換、テキスト効果などの機能を利用して、人の目をひきつけるテキストを作成できます。 テキストに標準タイプのドロップ シャドウ効果を適用した例を次に示します。  
  
 ![ソフトネス&#61;のテキストシャドウ 0.25](./media/typography-in-wpf/drop-shadow-text-effect.jpg)
  
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
  
 <xref:System.Windows.Media.TextEffect>オブジェクトは、テキストをテキスト文字列内の 1 つ以上の文字グループとして扱うことを可能にするヘルパー オブジェクトです。 次の例は、回転する個々の文字を示しています。 各文字は、1 秒間隔で個別に回転します。  
  
 ![テキストを回転するテキスト効果のスクリーンショット](./media/typography-in-wpf/rotating-text-effect.jpg)
  
#### <a name="using-flow-documents"></a>フロー ドキュメントの使用  
 コモン[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コントロールに加えて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テキスト表示用のレイアウト コントロール (<xref:System.Windows.Documents.FlowDocument>要素) も提供します。 要素<xref:System.Windows.Documents.FlowDocument>は、<xref:System.Windows.Controls.DocumentViewer>要素と共に、さまざまなレイアウト要件を持つ大量のテキストのコントロールを提供します。 レイアウト コントロールを使用すると、<xref:System.Windows.Documents.Typography>オブジェクトを介した高度な文字体裁や、他[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のコントロールのフォント関連プロパティにアクセスできます。  
  
 でホストされるテキスト コンテンツの例を<xref:System.Windows.Controls.FlowDocumentReader>次に示します。  
  
 ![OpenType フォントを示すスクリーンショット。](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 詳細については、「[WPF のドキュメント](documents-in-wpf.md)」を参照してください。  
  
### <a name="lightweight-text-drawing"></a>軽量テキスト描画  
 オブジェクトのメソッドを使用して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、オブジェクトに直接<xref:System.Windows.Media.DrawingContext.DrawText%2A>テキストを<xref:System.Windows.Media.DrawingContext>描画できます。 このメソッドを使用するには、オブジェクトを<xref:System.Windows.Media.FormattedText>作成します。 このオブジェクトを使用すると、複数行のテキストを描画できます。このテキストでは、テキスト内の各文字を個々に書式設定できます。 オブジェクトの機能には<xref:System.Windows.Media.FormattedText>、Windows API の DrawText フラグの機能の多くが含まれています。 また、<xref:System.Windows.Media.FormattedText>このオブジェクトには省略記号のサポートなどの機能が含まれており、テキストが境界を超えると省略記号が表示されます。 いくつかの書式を適用したテキストを次の例に示します。たとえば、2 番目と 3 番目の単語には線状グラデーションが適用されています。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)
  
 書式設定されたテキストをオブジェクトに<xref:System.Windows.Media.Geometry>変換して、他の種類の視覚的に興味深いテキストを作成できます。 たとえば、テキスト文字列のアウトラインに<xref:System.Windows.Media.Geometry>基づいてオブジェクトを作成できます。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 変換されたテキストのストローク、塗りつぶし、強調表示を変更して、人の目をひく視覚効果を作成するいくつかの方法を次の例に示します。  
  
 ![塗りつぶしとストロークに別の色を使用するテキスト](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![イメージ ブラシがストロークとハイライトに適用されたテキスト](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 オブジェクトの詳細については、「<xref:System.Windows.Media.FormattedText>[書式設定されたテキストを描画](drawing-formatted-text.md)する」を参照してください。  
  
### <a name="advanced-text-formatting"></a>テキストの高度な書式設定  
 テキスト API の最も高度なレベルでは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、名前空間内のオブジェクトと他の型を使用して<xref:System.Windows.Media.TextFormatting.TextFormatter>カスタム テキスト レイアウトを<xref:System.Windows.Media.TextFormatting>作成する機能が提供されます。 関連<xref:System.Windows.Media.TextFormatting.TextFormatter>付けられたクラスでは、文字書式、段落スタイル、改行ルール、および国際テキストのその他のレイアウト機能の独自の定義をサポートするカスタムテキストレイアウトを実装できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テキスト レイアウト サポートに関する既定の実装のオーバーライドが必要となるケースはほとんどありません。 ただし、テキストを編集するコントロールやアプリケーションを作成する場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既定の実装とは異なる実装が必要になることがあります。  
  
 従来のテキスト API と<xref:System.Windows.Media.TextFormatting.TextFormatter>は異なり、コールバック メソッドのセットを通じてテキスト レイアウト クライアントと対話します。 クライアントは、クラスの実装でこれらのメソッドを提供する必要<xref:System.Windows.Media.TextFormatting.TextSource>があります。 次の図は、クライアント アプリケーションと のテキスト レイアウト<xref:System.Windows.Media.TextFormatting.TextFormatter>の相互作用を示しています。  
  
 ![テキスト レイアウト クライアントと TextFormatter のダイアグラム](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 カスタム テキスト レイアウトの作成の詳細については、「[テキストの高度な書式設定](advanced-text-formatting.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType の概要](cleartype-overview.md)
- [OpenType フォントの機能](opentype-font-features.md)
- [書式設定されたテキストの描画](drawing-formatted-text.md)
- [テキストの高度な書式設定](advanced-text-formatting.md)
- [テキスト](optimizing-performance-text.md)
- [Microsoft の文字体裁](https://docs.microsoft.com/typography/)
