---
title: パフォーマンスの最適化:テキスト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rendering text [WPF]
- hyperlinks [WPF]
- formatted text [WPF]
- text [WPF], performance
- glyphs [WPF]
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
ms.openlocfilehash: db0738008766343fa19454cac14e75b318663f34
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352773"
---
# <a name="optimizing-performance-text"></a>パフォーマンスの最適化:テキスト
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、機能豊富な [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] コントロールを使用した、テキスト コンテンツ表示のサポートが含まれています。 一般にテキスト レンダリングは 3 つの階層に分けることができます。  
  
1.  使用して、<xref:System.Windows.Documents.Glyphs>と<xref:System.Windows.Media.GlyphRun>オブジェクトを直接します。  
  
2.  使用して、<xref:System.Windows.Media.FormattedText>オブジェクト。  
  
3.  などの高度なコントロールを使用して、<xref:System.Windows.Controls.TextBlock>と<xref:System.Windows.Documents.FlowDocument>オブジェクト。  
  
 このトピックでは、テキスト レンダリングのパフォーマンスに関する推奨事項を説明します。  
  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>グリフ レベルでのテキスト レンダリング  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 直接アクセスによるグリフ レベルのマークアップなどの高度なテキスト サポートを提供します<xref:System.Windows.Documents.Glyphs>を使用し、書式設定後のテキストの保持を希望するお客様向けです。 これらの機能は、下記のようなシナリオでのさまざまなテキスト レンダリング要件をサポートする不可欠なものです。  
  
-   固定形式のドキュメントの画面表示。  
  
-   印刷シナリオ。  
  
    -   デバイス プリンター言語としての [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]。  
  
    -   以前のプリンター ドライバー、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]アプリケーションから固定形式への出力。  
  
    -   印刷スプール形式。  
  
-   以前のバージョンの [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] のクライアントおよびその他のコンピューティング デバイスを含む、固定形式のドキュメント表示。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> <xref:System.Windows.Media.GlyphRun>固定形式のドキュメント プレゼンテーションと印刷シナリオ向けに設計されています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] いくつかの要素は、一般的なレイアウトと[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]などのシナリオ<xref:System.Windows.Controls.Label>と<xref:System.Windows.Controls.TextBlock>します。 レイアウトと [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] シナリオの詳細については、[WPF のタイポグラフィ](typography-in-wpf.md)を参照してください。  
  
 次の例のプロパティを定義する方法を示して、<xref:System.Windows.Documents.Glyphs>オブジェクト[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。 <xref:System.Windows.Documents.Glyphs>オブジェクトの出力を表して、<xref:System.Windows.Media.GlyphRun>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 この例では、Arial、Courier New、Times New Roman フォントがローカル コンピューターの **C:\WINDOWS\Fonts** フォルダーにインストールされていると想定しています。  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>DrawGlyphRun を使用する  
 カスタム コントロールがあるし、グリフをレンダリングするには、使用するかどうか、<xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>メソッド。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] カスタム書式を使用するとの下位レベル サービスも提供します、<xref:System.Windows.Media.FormattedText>オブジェクト。 最も効率的な方法でテキストをレンダリング[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グリフ レベルを使用して、テキストの内容を生成することによって、<xref:System.Windows.Documents.Glyphs>と<xref:System.Windows.Media.GlyphRun>。 ただし、この効率性のコストは、簡単に使用されるリッチ テキスト書式設定、組み込まれている機能の損失の[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]などのコントロール<xref:System.Windows.Controls.TextBlock>と<xref:System.Windows.Documents.FlowDocument>します。  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>FormattedText オブジェクト  
 <xref:System.Windows.Media.FormattedText>オブジェクトを使用すると、これで、テキスト内の各文字に個別に書式設定できます、複数行のテキストを描画します。 詳細については、「[書式設定されたテキストの描画](drawing-formatted-text.md)」を参照してください。  
  
 書式設定されたテキストを作成するには、<xref:System.Windows.Media.FormattedText.%23ctor%2A>を作成するコンス トラクター、<xref:System.Windows.Media.FormattedText>オブジェクト。 最初の書式設定済みテキスト文字列を作成したら、書式スタイルの範囲を適用できます。 アプリケーションが独自のレイアウトを実装する必要がある場合、<xref:System.Windows.Media.FormattedText>オブジェクトは、コントロールを使用してよりも適した選択肢<xref:System.Windows.Controls.TextBlock>します。 詳細については、<xref:System.Windows.Media.FormattedText>オブジェクトを参照してください[書式設定されたテキストの描画](drawing-formatted-text.md)します。  
  
 <xref:System.Windows.Media.FormattedText>オブジェクトが低レベルのテキストを書式設定機能を提供します。 複数の書式スタイルを 1 つ以上の文字に適用できます。 たとえば、両方を呼び出すことが、<xref:System.Windows.Media.FormattedText.SetFontSize%2A>と<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>テキストの最初の 5 文字の書式を変更する方法。  
  
 次のコード例を作成、<xref:System.Windows.Media.FormattedText>オブジェクトし、それをレンダリングします。  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument、TextBlock、ラベル コントロール  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には画面にテキストを描画するための複数のコントロールが含まれています。 各コントロールは異なるシナリオを対象にしており、それぞれに一連の機能と制限があります。  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument は TextBlock やラベルよりもパフォーマンスへの影響が大きい  
 一般に、<xref:System.Windows.Controls.TextBlock>要素は、制限付きのテキストのサポートがで短い文など、必要な場合に、使用する必要があります、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]します。 <xref:System.Windows.Controls.Label> 最小限のテキストのサポートが必要な場合に使用できます。 <xref:System.Windows.Documents.FlowDocument>要素は、コンテンツのリッチ プレゼンテーションをサポートする再フロー ドキュメントのコンテナーであり、したがって、使用するよりも大きい、パフォーマンスに影響があります、<xref:System.Windows.Controls.TextBlock>または<xref:System.Windows.Controls.Label>コントロール。  
  
 詳細については<xref:System.Windows.Documents.FlowDocument>を参照してください[フロー ドキュメントの概要](flow-document-overview.md)します。  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>FlowDocument での TextBlock の使用を避ける  
 <xref:System.Windows.Controls.TextBlock>から派生した要素が<xref:System.Windows.UIElement>します。 <xref:System.Windows.Documents.Run>から派生した要素が<xref:System.Windows.Documents.TextElement>、使用するよりも低コストである、 <xref:System.Windows.UIElement>-派生オブジェクト。 可能であればを使用して、<xref:System.Windows.Documents.Run>なく<xref:System.Windows.Controls.TextBlock>、テキスト コンテンツを表示するため、<xref:System.Windows.Documents.FlowDocument>します。  
  
 次のマークアップ サンプル内のテキスト コンテンツの設定の 2 つの方法を示しています、 <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>テキスト プロパティの設定に Run は使用しない  
 一般を使用して、<xref:System.Windows.Documents.Run>内、<xref:System.Windows.Controls.TextBlock>明示的なを使用していないよりも負荷がさらに高いパフォーマンスがいない<xref:System.Windows.Documents.Run>すべてのオブジェクトします。 使用する場合、<xref:System.Windows.Documents.Run>テキストのプロパティを設定するには、上で直接それらのプロパティを設定します、<xref:System.Windows.Controls.TextBlock>代わりにします。  
  
 次のマークアップのサンプルは、ここでは、text プロパティの設定のこれら 2 つの方法を示しています、<xref:System.Windows.Controls.TextBlock.FontWeight%2A>プロパティ。  
  
 [!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 次の表に、1000 を表示するコスト<xref:System.Windows.Controls.TextBlock>オブジェクトと、明示的ななし<xref:System.Windows.Documents.Run>します。  
  
|**TextBlock 型**|**作成時間 (ミリ秒)**|**レンダリング時間 (ミリ秒)**|  
|------------------------|------------------------------|----------------------------|  
|Run によるテキスト プロパティ設定|146|540|  
|TextBlock によるテキスト プロパティ設定|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Label.Content プロパティへのデータ バインドを避ける  
 あるシナリオを想像してください、<xref:System.Windows.Controls.Label>から頻繁に更新されるオブジェクト、<xref:System.String>ソース。 ときにデータ バインディング、<xref:System.Windows.Controls.Label>要素の<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティを<xref:System.String>ソース オブジェクト、パフォーマンスの低下が発生する可能性があります。 たびに、ソース<xref:System.String>が更新されると、古い<xref:System.String>オブジェクトが破棄され、新しい<xref:System.String>が再作成されます: ため、<xref:System.String>オブジェクトは、変更、変更することはできません。 これにより、<xref:System.Windows.Controls.ContentPresenter>の<xref:System.Windows.Controls.Label>オブジェクトをその古いコンテンツを破棄し、新しい表示する新しいコンテンツを再生成<xref:System.String>。  
  
 この問題の解決策は単純です。 場合、<xref:System.Windows.Controls.Label>カスタムに設定されていない<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>値で置き換えます、<xref:System.Windows.Controls.Label>で、<xref:System.Windows.Controls.TextBlock>とデータ バインド、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティをソース文字列。  
  
|**データ バインドされたプロパティ**|**更新時間 (ミリ秒)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>ハイパーリンク  
 <xref:System.Windows.Documents.Hyperlink>オブジェクトがインライン レベル フロー コンテンツ要素、フロー コンテンツ内のハイパーリンクをホストすることができます。  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>1 つの TextBlock オブジェクト内でハイパーリンクを結合  
 複数の使用を最適化する<xref:System.Windows.Documents.Hyperlink>要素内で同じ化することで<xref:System.Windows.Controls.TextBlock>します。 こうすると、アプリケーション内で作成するオブジェクトの数を最小限に抑えるのに役立ちます。 たとえば、次のように複数のハイパーリンクを表示するとします。  
  
 MSN Home &#124; My MSN  
  
 次のマークアップ例は複数<xref:System.Windows.Controls.TextBlock>要素は、ハイパーリンクを表示するために使用します。  
  
 [!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 次のマークアップ例を表示するハイパーリンク、今回は、1 つを使用してより効率的な方法を示しています<xref:System.Windows.Controls.TextBlock>:。  
  
 [!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>MouseEnter イベントでのみハイパーリンクに下線を表示  
 A<xref:System.Windows.TextDecoration>オブジェクトがテキストに追加できるビジュアルの装飾。 ただし、パフォーマンスの処理を要するインスタンスを作成することできます。 広範に使用する場合<xref:System.Windows.Documents.Hyperlink>要素など、イベントをトリガーするときにのみ下線を表示を検討してください、<xref:System.Windows.ContentElement.MouseEnter>イベント。 詳細については、「[方法: ハイパーリンクに下線を引くかどうかを指定する](how-to-specify-whether-a-hyperlink-is-underlined.md)」を参照してください。  
  
 ![Textdecorations を表示するハイパーリンク](./media/textdecoration03.png "TextDecoration03")  
MouseEnter で表示されるハイパーリンク  
  
 次のマークアップ サンプルでは、<xref:System.Windows.Documents.Hyperlink>下線なしで定義されています。  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 次の表の 1000 を表示するパフォーマンス コスト<xref:System.Windows.Documents.Hyperlink>要素と、下線なし。  
  
|**ハイパーリンク**|**作成時間 (ミリ秒)**|**レンダリング時間 (ミリ秒)**|  
|-------------------|------------------------------|----------------------------|  
|下線あり|289|1130|  
|下線なし|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>テキスト書式設定機能  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、自動ハイフネーションなどのリッチ テキスト書式設定サービスを提供します。 これらのサービスはアプリケーションのパフォーマンスに影響を与える可能性があり、必要な場合のみ使用すべきです。  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>ハイフネーションの不要な使用を避ける  
 自動ハイフネーションは、テキスト、行のハイフンのブレークポイントを検索でき、内の行の追加の改行位置<xref:System.Windows.Controls.TextBlock>と<xref:System.Windows.Documents.FlowDocument>オブジェクト。 既定では、これらのオブジェクトでは自動ハイフネーション機能は無効です。 この機能は、オブジェクトの IsHyphenationEnabled プロパティを `true` に設定することで有効にできます。 しかし、この機能を有効にすると [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] の相互運用機能が開始され、アプリケーションのパフォーマンスに影響を与えることがあります。 必要でない限り、自動ハイフネーションを使用しないことをお勧めします。  
  
### <a name="use-figures-carefully"></a>図表を慎重に使用する  
 A<xref:System.Windows.Documents.Figure>要素のコンテンツ ページ内で絶対配置できるフロー コンテンツの一部を表します。 場合によってで、<xref:System.Windows.Documents.Figure>ページ全体の位置が既に配置されているコンテンツと競合している場合に自動的に再フォーマットする場合があります。いずれかのグループ化して不要な再フォーマットの可能性を最小限に抑えることができます<xref:System.Windows.Documents.Figure>または固定ページ サイズのシナリオでのコンテンツの先頭付近にある宣言して、互いの横にある要素。  
  
### <a name="optimal-paragraph"></a>適切な段落  
 最適な段落の機能、<xref:System.Windows.Documents.FlowDocument>オブジェクトは、空白文字をできるだけ均等に分散するように段落をレイアウトします。 既定では、適切な段落の機能は無効です。 この機能を有効にするには、オブジェクトの<xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A>プロパティを`true`します。 ただし、この機能を有効にするとアプリケーションのパフォーマンスに影響します。 必要でない限り、適切な段落の機能を使用しないことをお勧めします。  
  
## <a name="see-also"></a>関連項目
- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [2D グラフィックスとイメージング](optimizing-performance-2d-graphics-and-imaging.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
