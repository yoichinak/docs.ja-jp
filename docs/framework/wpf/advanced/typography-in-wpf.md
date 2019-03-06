---
title: WPF のタイポグラフィ
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 086e02601e527229eed7dc3e2fab73df1f918a8c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359550"
---
# <a name="typography-in-wpf"></a>WPF のタイポグラフィ
このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の主要な文字体裁の機能について説明します。 これらの機能には、テキスト レンダリングの品質とパフォーマンスの向上、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 文字体裁のサポート、国際対応テキストの強化、フォントのサポートの強化、新しいテキスト API (アプリケーション プログラミング インターフェイス) が含まれます。  
  

  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>テキストに関する品質とパフォーマンスの向上  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のテキストは、テキストのわかりやすさと読みやすさを高める [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] を使用して描画されます。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] は、ラップトップや Pocket PC の画面、フラット パネル モニターなど、既存の LCD (液晶ディスプレイ) でのテキストの読みやすさを向上させるために [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] が開発したソフトウェア テクノロジです。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] は、ピクセルの画素レベルで文字を表示調整することで実際の形状を忠実に再現したテキストを表示できる、サブピクセル レンダリングを採用しています。 解像度が上がるとテキスト表示の微細部の鮮明度が高くなるため、長時間にわたって読んでも苦になりません。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] での [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] のもう 1 つの改良点は、y 方向のアンチエイリアシングです。これにより、テキスト文字の緩やかな曲線部の上下が滑らかになります。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] の機能の詳細については、「[ClearType の概要](cleartype-overview.md)」をご覧ください。  
  
 ![テキストを ClearType y&#45;方向&#45;エイリアス](./media/typographyinwpf02.gif "TypographyInWPF02")  
ClearType の y 方向アンチエイリアシングを適用したテキスト  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、コンピューターがハードウェアの最小要件を満たしている限り、テキスト レンダリング パイプライン全体に対してハードウェア アクセラレータを使用できます。 ハードウェアを使用して実行できないレンダリングは、ソフトウェア レンダリングとなります。 ハードウェア アクセラレータは、個々のグリフの格納から始まり、グリフ実行への複数のグリフの合成、効果の適用、最終的な表示出力への [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ブレンディング アルゴリズムの適用まで、テキスト レンダリング パイプラインのすべてのフェーズに影響します。 ハードウェア アクセラレータの詳細については、「[グラフィックスの描画層](graphics-rendering-tiers.md)」をご覧ください。  
  
 ![テキスト レンダリング パイプラインのダイアグラム](./media/typographyinwpf01.png "TypographyInWPF01")  
パイプラインを描画するテキストのダイアグラム  
  
 また、アニメーション化されたテキストは、文字とグリフのいずれによる場合でも、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で有効化されているグラフィックス ハードウェア機能をすべて利用できます。 これにより、テキスト アニメーションが滑らかになります。  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>多彩な文字体裁  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォント形式は、[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] フォント形式の拡張です。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォント形式は、[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] と Adobe が共同で開発したもので、高度な文字体裁機能を豊富に備えています。 <xref:System.Windows.Documents.Typography>オブジェクトは、多くの高度な機能の公開[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]フォント、スタイル代替グリフや飾り付きなど。 [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] には、Pericles フォントや Pescadero フォントなど、豊富な機能を持つ [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォント サンプルが用意されています。 詳細については、「[OpenType フォント パックのサンプル](sample-opentype-font-pack.md)」をご覧ください。  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォントには、標準グリフ セットにスタイル代替グリフを提供する追加グリフが含まれています。 次のテキストでは、スタイル代替グリフが表示されています。  
  
 ![OpenType のスタイル代替グリフを使用してテキストを](./media/opentypefont02.gif "opentypefont02")  
OpenType のスタイル代替グリフを使用するテキスト  
  
 スワッシュは装飾的なグリフで、カリグラフィを連想させることがよくある、手の込んだ装飾が使用されます。 次のテキストには、Pescadero フォントの標準と飾り付きグリフが表示されます。  
  
 ![OpenType の標準と飾り付きグリフを使用してテキストを](./media/opentypefont08.gif "opentypefont08")  
OpenType の標準グリフと飾り付きグリフを使用するテキスト  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] の機能の詳細については、「[OpenType フォントの機能](opentype-font-features.md)」をご覧ください。  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>国際対応テキストのサポートの強化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、次の機能を提供することで、国際対応テキストのサポートを強化しています。  
  
-   すべての書記体系における、適用可能な単位を使用した自動行間隔設定。  
  
-   国際対応テキストの幅広いサポート。 詳細については、「[WPF のグローバリゼーション](globalization-for-wpf.md)」をご覧ください。  
  
-   言語に合わせた改行、ハイフネーション、両端揃え。  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>フォントのサポートの強化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、次の機能を提供することで、フォントのサポートを強化しています。  
  
-   すべてのテキストに対応する Unicode。 フォントの動作や選択に文字セットやコードページが不要になりました。  
  
-   システム ロケールなど、グローバル設定に左右されないフォント動作。  
  
-   個別<xref:System.Windows.FontWeight>、 <xref:System.Windows.FontStretch>、および<xref:System.Windows.FontStyle>型を定義するため、<xref:System.Windows.Media.FontFamily>します。 これにより、斜体と太字のブール値の組み合わせでフォント ファミリを定義する [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] プログラミングよりも優れた柔軟性が提供されます。  
  
-   フォント名とは関係なく処理される書き込み方向 (横書きまたは縦書き)。  
  
-   複合フォント技術を使用した、移植可能な [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ファイルにおけるフォント リンクとフォントの代替。 複合フォントは、完全な多言語フォントの構築を可能にします。 また、複合フォントは、欠落グリフの表示を防ぐ機能も備えています。 詳細についてで「解説」を参照してください、<xref:System.Windows.Media.FontFamily>クラス。  
  
-   単一言語フォントのグループを使用した、複合フォントから構築される国際対応フォント。 これにより、複数言語に対応するフォントの開発時にリソースのコストを節約できます。  
  
-   ドキュメントに埋め込むことで移植性が得られる複合フォント。 詳細についてで「解説」を参照してください、<xref:System.Windows.Media.FontFamily>クラス。  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>新しいテキスト API (アプリケーション プログラミング インターフェイス)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、開発者がアプリケーションにテキストを含めるときに使用できるいくつかのテキスト [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を提供します。 これらの [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] は、次の 3 つのカテゴリに分類されます。  
  
-   **レイアウトとユーザー インターフェイス**:  [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)] に対応した一般的なテキスト コントロールです。  
  
-   **軽量テキスト描画**:  オブジェクトにテキストを直接描画できます。  
  
-   **テキストの高度な書式設定**:  カスタム テキスト エンジンを実装できます。  
  
### <a name="layout-and-user-interface"></a>レイアウトとユーザー インターフェイス  
 最上位レベルの機能、テキスト[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]一般的な提供[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]などのコントロール<xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.TextBox>します。 これらのコントロールは、アプリケーション内に基本的な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を提供し、テキストの表示や操作を簡単に実行できるようにします。 などのコントロール<xref:System.Windows.Controls.RichTextBox>と<xref:System.Windows.Controls.PasswordBox>より高度なのメッセージまたは専用のテキスト処理を有効にします。 などのクラスと<xref:System.Windows.Documents.TextRange>、 <xref:System.Windows.Documents.TextSelection>、および<xref:System.Windows.Documents.TextPointer>便利なテキスト操作を有効にします。 これら[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コントロールなどのプロパティを提供<xref:System.Windows.Controls.Control.FontFamily%2A>、 <xref:System.Windows.Controls.Control.FontSize%2A>、および<xref:System.Windows.Controls.Control.FontStyle%2A>テキストを表示するために使用されるフォントを制御できます。  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>ビットマップ効果、変換、テキスト効果の使用  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、ビットマップ効果、変換、テキスト効果などの機能を利用して、人の目をひきつけるテキストを作成できます。 テキストに標準タイプのドロップ シャドウ効果を適用した例を次に示します。  
  
 ![テキストの影のぼかしを&#61;0.25](./media/shadowtext01.jpg "ShadowText01")  
ドロップ シャドウが適用されたテキスト  
  
 テキストにドロップ シャドウ効果とノイズを適用した例を次に示します。  
  
 ![ノイズを含むテキスト シャドウ](./media/shadowtext04.jpg "ShadowText04")  
ドロップ シャドウとノイズが適用されたテキスト  
  
 テキストの外縁にグロー効果を適用した例を次に示します。  
  
 ![OuterGlowBitmapEffect を使用するテキスト シャドウ](./media/shadowtext05.jpg "ShadowText05")  
外縁にグロー効果が適用されたテキスト  
  
 テキストにぼかし効果が適用されている例を次に示します。  
  
 ![BlurBitmapEffect を使用するテキスト シャドウ](./media/shadowtext06.jpg "ShadowText06")  
ぼかし効果が適用されたテキスト  
  
 テキストの 2 行目を x 軸に沿って 150% 拡大し、3 行目を y 軸に沿って 150% 拡大した例を次に示します。  
  
 ![ScaleTransform を使用して拡大縮小されたテキスト](./media/transformedtext02.jpg "TransformedText02")  
ScaleTransform を使用したテキスト  
  
 x 軸に沿って傾斜させたテキストの例を次に示します。  
  
 ![SkewTransform を使用して傾斜させたテキスト](./media/transformedtext03.jpg "TransformedText03")  
SkewTransform を使用したテキスト  
  
 A<xref:System.Windows.Media.TextEffect>オブジェクトは、テキストをテキスト文字列内の文字の 1 つまたは複数のグループとして扱うことができるヘルパー オブジェクト。 次の例は、回転する個々の文字を示しています。 各文字は、1 秒間隔で個別に回転します。  
  
 ![テキストを回転させるテキスト効果のスクリーン ショット](./media/texteffect01.jpg "TextEffect01")  
回転するテキスト効果アニメーションの例  
  
#### <a name="using-flow-documents"></a>フロー ドキュメントの使用  
 一般的なだけでなく[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コントロール、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テキスト表示のレイアウト コントロールは、-、<xref:System.Windows.Documents.FlowDocument>要素。 <xref:System.Windows.Documents.FlowDocument>要素と組み合わせて、<xref:System.Windows.Controls.DocumentViewer>要素のレイアウト要件をさまざまなテキストの大量のコントロールを提供します。 レイアウト コントロールでの高度な文字体裁へのアクセスを提供する、<xref:System.Windows.Documents.Typography>オブジェクトとその他のフォント関連プロパティ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コントロール。  
  
 次の例では、テキスト コンテンツでホストされている、<xref:System.Windows.Controls.FlowDocumentReader>検索、ナビゲーション、改ページ、およびスケーリングをサポートするコンテンツを提供します。  
  
 ![OpenType フォント サンプルの使用のスクリーン ショット](./media/typographyinwpf-03.png "TypographyInWPF_03")  
FlowDocumentReader でホストされるテキスト  
  
 詳細については、「[WPF のドキュメント](documents-in-wpf.md)」を参照してください。  
  
### <a name="lightweight-text-drawing"></a>軽量テキスト描画  
 テキストに直接描画できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]オブジェクトを使用して、<xref:System.Windows.Media.DrawingContext.DrawText%2A>のメソッド、<xref:System.Windows.Media.DrawingContext>オブジェクト。 このメソッドを使用して、作成、<xref:System.Windows.Media.FormattedText>オブジェクト。 このオブジェクトを使用すると、複数行のテキストを描画できます。このテキストでは、テキスト内の各文字を個々に書式設定できます。 機能、<xref:System.Windows.Media.FormattedText>オブジェクトには、Win32 API の DrawText フラグの機能の多くが含まれます。 さらに、<xref:System.Windows.Media.FormattedText>オブジェクトにテキストがその境界を超えると、省略記号を表示する、省略記号のサポートなどの機能が含まれています。 いくつかの書式を適用したテキストを次の例に示します。たとえば、2 番目と 3 番目の単語には線状グラデーションが適用されています。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](./media/formattedtext01.jpg "FormattedText01")  
FormattedText オブジェクトを使用して表示されるテキスト  
  
 書式設定されたテキストに変換できます<xref:System.Windows.Media.Geometry>オブジェクト、テキストを視覚的に興味深いは、他の種類を作成することができます。 たとえば、作成する、<xref:System.Windows.Media.Geometry>のテキスト文字列のアウトラインに基づいてオブジェクト。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](./media/outlinedtext02.jpg "OutlinedText02")  
線形グラデーション ブラシを使用するテキスト アウトライン  
  
 変換されたテキストのストローク、塗りつぶし、強調表示を変更して、人の目をひく視覚効果を作成するいくつかの方法を次の例に示します。  
  
 ![塗りつぶしとストロークに別の色とテキスト](./media/outlinedtext03.jpg "OutlinedText03")  
ストロークと塗りつぶしを別々の色に設定した例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/outlinedtext04.jpg "OutlinedText04")  
ストロークに適用したイメージ ブラシの例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/outlinedtext05.jpg "OutlinedText05")  
ストロークと強調表示に適用したイメージ ブラシの例  
  
 詳細については、<xref:System.Windows.Media.FormattedText>オブジェクトを参照してください[書式設定されたテキストの描画](drawing-formatted-text.md)します。  
  
### <a name="advanced-text-formatting"></a>テキストの高度な書式設定  
 テキストの高度なレベル、一番[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用してカスタム テキスト レイアウトを作成する機能が提供する、<xref:System.Windows.Media.TextFormatting.TextFormatter>オブジェクトとその他の種類で、<xref:System.Windows.Media.TextFormatting>名前空間。 <xref:System.Windows.Media.TextFormatting.TextFormatter>関連クラスは、ユーザー定義による文字形式、段落のスタイルをサポートするカスタム テキスト レイアウトを実装する線の改行ルール、および他のレイアウトが国際対応テキストの機能を使用するとします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テキスト レイアウト サポートに関する既定の実装のオーバーライドが必要となるケースはほとんどありません。 ただし、テキストを編集するコントロールやアプリケーションを作成する場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既定の実装とは異なる実装が必要になることがあります。  
  
 従来のテキストとは異なり[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]、<xref:System.Windows.Media.TextFormatting.TextFormatter>一連のコールバック メソッドを介してテキスト レイアウト クライアントと対話します。 クライアントは、これらのメソッドの実装を提供する必要があります、<xref:System.Windows.Media.TextFormatting.TextSource>クラス。 次の図は、クライアント アプリケーション間でテキスト レイアウトの相互作用と<xref:System.Windows.Media.TextFormatting.TextFormatter>します。  
  
 ![テキスト レイアウト クライアントと TextFormatter のダイアグラム](./media/textformatter01.png "TextFormatter01")  
アプリケーションと TextFormatter の間の相互作用  
  
 カスタム テキスト レイアウトの作成の詳細については、「[テキストの高度な書式設定](advanced-text-formatting.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType の概要](cleartype-overview.md)
- [OpenType フォントの機能](opentype-font-features.md)
- [書式設定されたテキストの描画](drawing-formatted-text.md)
- [テキストの高度な書式設定](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Microsoft の文字体裁](https://www.microsoft.com/typography/default.mspx)
