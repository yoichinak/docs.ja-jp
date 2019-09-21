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
ms.openlocfilehash: 318972c20f6461489226e19b3e517ba0ac069b28
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933365"
---
# <a name="optimizing-performance-text"></a>パフォーマンスの最適化:テキスト

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、機能豊富な [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] コントロールを使用した、テキスト コンテンツ表示のサポートが含まれています。 一般にテキスト レンダリングは 3 つの階層に分けることができます。

1. <xref:System.Windows.Documents.Glyphs>オブジェクトと<xref:System.Windows.Media.GlyphRun>オブジェクトを直接使用する。

2. <xref:System.Windows.Media.FormattedText>オブジェクトを使用します。

3. オブジェクトや<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.FlowDocument>オブジェクトなどの高レベルのコントロールを使用します。

このトピックでは、テキスト レンダリングのパフォーマンスに関する推奨事項を説明します。

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>グリフ レベルでのテキスト レンダリング

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]書式設定後にテキストを傍受して保持する必要が<xref:System.Windows.Documents.Glyphs>ある顧客に対して、に直接アクセスするグリフレベルのマークアップなどの高度なテキストサポートを提供します。 これらの機能は、下記のようなシナリオでのさまざまなテキスト レンダリング要件をサポートする不可欠なものです。

- 固定形式のドキュメントの画面表示。

- 印刷シナリオ。

  - デバイス プリンター言語としての [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。

  - Microsoft XPS ドキュメントライター。

  - 以前のプリンター ドライバー、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]アプリケーションから固定形式への出力。

  - 印刷スプール形式。

- 以前のバージョンの Windows およびその他のコンピューティングデバイス用のクライアントを含む、固定形式のドキュメント表現。

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>および<xref:System.Windows.Media.GlyphRun>は、固定形式のドキュメントのプレゼンテーションと印刷のシナリオ向けに設計されています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]には、一般的なレイアウトと[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 、や<xref:System.Windows.Controls.TextBlock>など<xref:System.Windows.Controls.Label>のシナリオのためのいくつかの要素が用意されています。 レイアウトと [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] シナリオの詳細については、[WPF のタイポグラフィ](typography-in-wpf.md)を参照してください。

次の例は、で<xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]オブジェクトのプロパティを定義する方法を示しています。 オブジェクト<xref:System.Windows.Documents.Glyphs>は、の<xref:System.Windows.Media.GlyphRun>の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]出力を表します。 この例では、Arial、Courier New、Times New Roman フォントがローカル コンピューターの **C:\WINDOWS\Fonts** フォルダーにインストールされていると想定しています。

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>DrawGlyphRun を使用する

カスタムコントロールがあり、グリフをレンダリングする場合は、 <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>メソッドを使用します。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、 <xref:System.Windows.Media.FormattedText>オブジェクトを使用して、カスタムテキスト書式設定用の下位レベルのサービスも提供します。 で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]テキストを表示する最も効率的な方法は、と<xref:System.Windows.Media.GlyphRun>を使用して<xref:System.Windows.Documents.Glyphs>グリフレベルでテキストコンテンツを生成することです。 ただし、この効率のコストは、や[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Documents.FlowDocument>など<xref:System.Windows.Controls.TextBlock>のコントロールの組み込み機能である、使いやすいリッチテキスト書式設定が失われることにあります。

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>FormattedText オブジェクト

<xref:System.Windows.Media.FormattedText>オブジェクトを使用すると、複数行のテキストを描画できます。この場合、テキストの各文字を個別に書式設定できます。 詳細については、「[書式設定されたテキストの描画](drawing-formatted-text.md)」を参照してください。

書式設定されたテキストを<xref:System.Windows.Media.FormattedText.%23ctor%2A>作成するには<xref:System.Windows.Media.FormattedText> 、コンストラクターを呼び出してオブジェクトを作成します。 最初の書式設定済みテキスト文字列を作成したら、書式スタイルの範囲を適用できます。 アプリケーションで独自のレイアウトを実装する場合は、など<xref:System.Windows.Media.FormattedText> <xref:System.Windows.Controls.TextBlock>のコントロールを使用するよりも、オブジェクトの方が適しています。 オブジェクトの詳細につい<xref:System.Windows.Media.FormattedText>ては、「[書式設定](drawing-formatted-text.md)されたテキストの描画」を参照してください。

オブジェクト<xref:System.Windows.Media.FormattedText>は、低レベルのテキスト書式設定機能を提供します。 複数の書式スタイルを 1 つ以上の文字に適用できます。 たとえば、メソッドと<xref:System.Windows.Media.FormattedText.SetFontSize%2A> <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>メソッドの両方を呼び出して、テキスト内の最初の5文字の書式を変更することができます。

オブジェクトを<xref:System.Windows.Media.FormattedText>作成してレンダリングするコード例を次に示します。

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument、TextBlock、ラベル コントロール

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には画面にテキストを描画するための複数のコントロールが含まれています。 各コントロールは異なるシナリオを対象にしており、それぞれに一連の機能と制限があります。

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument は TextBlock やラベルよりもパフォーマンスへの影響が大きい

一般<xref:System.Windows.Controls.TextBlock>に、の簡単な文[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]など、制限されたテキストのサポートが必要な場合は、要素を使用する必要があります。 <xref:System.Windows.Controls.Label>最小限のテキストのサポートが必要な場合に使用できます。 要素は、コンテンツの豊富な表示をサポートする、再調整可能なドキュメントのコンテナーです。したがって、コントロール<xref:System.Windows.Controls.TextBlock>または<xref:System.Windows.Controls.Label>コントロールを使用する場合よりもパフォーマンスに大きな影響があります。 <xref:System.Windows.Documents.FlowDocument>

の<xref:System.Windows.Documents.FlowDocument>詳細については、「[フロードキュメントの概要](flow-document-overview.md)」を参照してください。

### <a name="avoid-using-textblock-in-flowdocument"></a>FlowDocument での TextBlock の使用を避ける

要素はから<xref:System.Windows.UIElement>派生します。 <xref:System.Windows.Controls.TextBlock> 要素<xref:System.Windows.Documents.Run>はから派生し<xref:System.Windows.Documents.TextElement>ています。これは、から派生<xref:System.Windows.UIElement>したオブジェクトよりも使用コストが低くなります。 可能であれば<xref:System.Windows.Documents.Run> 、で<xref:System.Windows.Controls.TextBlock>テキストコンテンツを<xref:System.Windows.Documents.FlowDocument>表示するのではなく、を使用します。

次のマークアップサンプルは、内にテキストコンテンツを設定<xref:System.Windows.Documents.FlowDocument>する2つの方法を示しています。

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>テキスト プロパティの設定に Run は使用しない

一般に、 <xref:System.Windows.Documents.Run> <xref:System.Windows.Controls.TextBlock>内でを使用すると、明示的<xref:System.Windows.Documents.Run>なオブジェクトを使用しない場合よりもパフォーマンスが高くなります。 テキストプロパティを設定する<xref:System.Windows.Documents.Run>ためにを使用している場合は、 <xref:System.Windows.Controls.TextBlock>代わりにそのプロパティを直接設定します。

次のマークアップサンプルでは、text プロパティ (この場合は<xref:System.Windows.Controls.TextBlock.FontWeight%2A>プロパティ) を設定する2つの方法を示しています。

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

次の表は、明示的<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.Run>にを指定していない場合に、1000オブジェクトを表示する場合のコストを示しています。

|**TextBlock 型**|**作成時間 (ミリ秒)**|**レンダリング時間 (ミリ秒)**|
|------------------------|------------------------------|----------------------------|
|Run によるテキスト プロパティ設定|146|540|
|TextBlock によるテキスト プロパティ設定|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Label.Content プロパティへのデータ バインドを避ける

ソースから頻繁に更新される<xref:System.Windows.Controls.Label>オブジェクトがあるシナリオを考えてみましょう。 <xref:System.String> <xref:System.Windows.Controls.Label>要素<xref:System.String>の<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティをソースオブジェクトにバインドすると、パフォーマンスが低下することがあります。 ソース<xref:System.String>が更新されるたびに、古い<xref:System.String>オブジェクトが破棄され、 <xref:System.String>新しいが再作成さ<xref:System.String>れます。これは、オブジェクトが不変であるため、変更できないためです。 これにより、 <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.Label>オブジェクトのが古いコンテンツを破棄し、新しいコンテンツを再生成して新しい<xref:System.String>が表示されるようになります。

この問題の解決策は単純です。 <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.Label>がカスタム<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>値に設定されていない場合は、をに置き換え、そのプロパティをソース文字列にバインドします。 <xref:System.Windows.Controls.Label>

|**データ バインドされたプロパティ**|**更新時間 (ミリ秒)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>ハイパーリンク

<xref:System.Windows.Documents.Hyperlink>オブジェクトは、フローコンテンツ内のハイパーリンクをホストできるようにするインラインレベルのフローコンテンツ要素です。

### <a name="combine-hyperlinks-in-one-textblock-object"></a>1 つの TextBlock オブジェクト内でハイパーリンクを結合

複数<xref:System.Windows.Documents.Hyperlink>の要素を同じ<xref:System.Windows.Controls.TextBlock>内にグループ化することで、その使用を最適化できます。 こうすると、アプリケーション内で作成するオブジェクトの数を最小限に抑えるのに役立ちます。 たとえば、次のように複数のハイパーリンクを表示するとします。

MSN Home &#124; My MSN

次のマークアップの例<xref:System.Windows.Controls.TextBlock>は、ハイパーリンクを表示するために使用される複数の要素を示しています。

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

次のマークアップの例では、1つ<xref:System.Windows.Controls.TextBlock>のを使用して、ハイパーリンクを表示するより効率的な方法を示しています。

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>MouseEnter イベントでのみハイパーリンクに下線を表示

<xref:System.Windows.TextDecoration>オブジェクトは、テキストに追加できるビジュアル装飾ですが、インスタンス化するのにパフォーマンスに大きな影響を与える可能性があります。 <xref:System.Windows.Documents.Hyperlink>要素を広範囲に使用する場合は、 <xref:System.Windows.ContentElement.MouseEnter>イベントなどのイベントをトリガーするときにのみ下線を表示することを検討してください。 詳細については、「[方法: ハイパーリンクに下線を引くかどうかを指定する](how-to-specify-whether-a-hyperlink-is-underlined.md)」を参照してください。

次の図は、MouseEnter イベントが下線付きのハイパーリンクをトリガーする方法を示しています。

![TextDecorations を表示するハイパーリンク](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

次のマークアップサンプルは<xref:System.Windows.Documents.Hyperlink> 、下線付きで定義されているを示しています。

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

次の表は、1000 <xref:System.Windows.Documents.Hyperlink>要素を下線付きで、または下線なしで表示する場合のパフォーマンスコストを示しています。

|**ハイパーリンク**|**作成時間 (ミリ秒)**|**レンダリング時間 (ミリ秒)**|
|-------------------|------------------------------|----------------------------|
|下線あり|289|1130|
|下線なし|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>テキスト書式設定機能

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、自動ハイフネーションなどのリッチ テキスト書式設定サービスを提供します。 これらのサービスはアプリケーションのパフォーマンスに影響を与える可能性があり、必要な場合のみ使用すべきです。

### <a name="avoid-unnecessary-use-of-hyphenation"></a>ハイフネーションの不要な使用を避ける

自動ハイフネーションでは、テキスト行のハイフンブレークポイントが検出され、オブジェクトと<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.FlowDocument>オブジェクトの行に追加のブレーク位置が許可されます。 既定では、これらのオブジェクトでは自動ハイフネーション機能は無効です。 この機能は、オブジェクトの IsHyphenationEnabled プロパティを `true` に設定することで有効にできます。 ただし、この機能を有効[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にすると、によってコンポーネントオブジェクトモデル (COM) の相互運用性が開始され、アプリケーションのパフォーマンスに影響を与える可能性があります。 必要でない限り、自動ハイフネーションを使用しないことをお勧めします。

### <a name="use-figures-carefully"></a>図表を慎重に使用する

要素<xref:System.Windows.Documents.Figure>は、コンテンツのページ内に絶対に配置できるフローコンテンツの一部を表します。 場合によっては<xref:System.Windows.Documents.Figure> 、その位置が既にレイアウトされているコンテンツと競合すると、ページ全体が自動的に再フォーマットされることがあります。複数の要素を相互にグループ化<xref:System.Windows.Documents.Figure>するか、固定ページサイズのシナリオでコンテンツの先頭付近に宣言することで、不要な再フォーマットの可能性を最小限に抑えることができます。

### <a name="optimal-paragraph"></a>適切な段落

<xref:System.Windows.Documents.FlowDocument>オブジェクトの最適な段落機能により、空白が可能な限り均等に分布するように段落がレイアウトされます。 既定では、適切な段落の機能は無効です。 この機能を有効にするには、オブジェクト<xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A>のプロパティ`true`をに設定します。 ただし、この機能を有効にするとアプリケーションのパフォーマンスに影響します。 必要でない限り、適切な段落の機能を使用しないことをお勧めします。

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
