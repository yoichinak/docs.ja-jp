---
title: 書式設定されたテキストの描画
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: 1e82795afbdd5b1b0a05f95600ebdb92fc134b7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186562"
---
# <a name="drawing-formatted-text"></a>書式設定されたテキストの描画
このトピックでは、オブジェクトの機能の概要について<xref:System.Windows.Media.FormattedText>説明します。 このオブジェクトは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションでのテキストの描画に対する低レベルの制御を提供します。  

## <a name="technology-overview"></a>テクノロジの概要  
 オブジェクト<xref:System.Windows.Media.FormattedText>を使用すると、複数行のテキストを描画でき、テキスト内の各文字を個別に書式設定できます。 複数の書式が適用されたテキストを次の例に示します。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Win32 API から移行する開発者向けに[、Win32 移行](#win32_migration)セクションの表には、Win32 DrawText フラグと同等[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の概算値が一覧表示されます。  
  
### <a name="reasons-for-using-formatted-text"></a>書式設定されたテキストを使用する理由  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、画面にテキストを描画するための複数のコントロールが含まれています。 各コントロールは異なるシナリオを対象にしており、それぞれに一連の機能と制限があります。 一般に<xref:System.Windows.Controls.TextBlock>、この要素は、テキストサポートが限定されている場合 (短い文など)[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]で使用する必要があります。 <xref:System.Windows.Controls.Label>最小限のテキストサポートが必要な場合に使用できます。 詳細については、「[WPF のドキュメント](documents-in-wpf.md)」を参照してください。  
  
 オブジェクト<xref:System.Windows.Media.FormattedText>は、テキスト コントロールよりも[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]大きなテキスト書式設定機能を提供し、装飾要素としてテキストを使用する場合に便利です。 詳細については、後の「[書式設定されたテキストのジオメトリへの変換](#converting_formatted_text)」を参照してください。  
  
 また、この<xref:System.Windows.Media.FormattedText>オブジェクトは、テキスト指向の派生オブジェクトを作成<xref:System.Windows.Media.DrawingVisual>する場合に便利です。 <xref:System.Windows.Media.DrawingVisual>は、図形、イメージ、またはテキストのレンダリングに使用される軽量の描画クラスです。 詳細については、「[DrawingVisuals を使用したヒット テストのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)」を参照してください。  
  
## <a name="using-the-formattedtext-object"></a>FormattedText オブジェクトの使用  
 書式設定されたテキストを作成するには、コンストラクター<xref:System.Windows.Media.FormattedText.%23ctor%2A>を呼び出<xref:System.Windows.Media.FormattedText>してオブジェクトを作成します。 最初の書式設定済みテキスト文字列を作成したら、書式スタイルの範囲を適用できます。  
  
 このプロパティ<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>を使用して、テキストを特定の幅に制限します。 テキストは、指定された幅を超えないように自動的に折り返されます。 このプロパティ<xref:System.Windows.Media.FormattedText.MaxTextHeight%2A>を使用して、テキストを特定の高さに制限します。 テキストは、指定された高さを超えた部分に省略記号 "…" を表示します。  
  
 ![ワードラップと省略記号付きで表示されるテキスト。](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)
  
 複数の書式スタイルを 1 つ以上の文字に適用できます。 たとえば、<xref:System.Windows.Media.FormattedText.SetFontSize%2A>メソッドと メソッド<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>の両方を呼び出して、テキスト内の最初の 5 文字の書式を変更できます。  
  
 オブジェクトを<xref:System.Windows.Media.FormattedText>作成し、テキストに複数の書式スタイルを適用するコード例を次に示します。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>フォント サイズの単位  
 アプリケーションの他のテキスト[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]オブジェクトと同様<xref:System.Windows.Media.FormattedText>に、オブジェクトはデバイスに依存しないピクセルを測定単位として使用します。 ただし、ほとんどの Win32 アプリケーションでは、計測単位としてポイントを使用します。 アプリケーションで[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ポイント単位で表示テキストを使用する場合は、デバイスに依存しない単位 (単位当たり 1/96 インチ) をポイントに変換する必要があります。 この変換を実行する方法を次のコード例に示します。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>
### <a name="converting-formatted-text-to-a-geometry"></a>書式設定されたテキストのジオメトリへの変換  
 書式設定されたテキストをオブジェクトに<xref:System.Windows.Media.Geometry>変換して、他の種類の視覚的に興味深いテキストを作成できます。 たとえば、テキスト文字列のアウトラインに<xref:System.Windows.Media.Geometry>基づいてオブジェクトを作成できます。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](./media/typography-in-wpf/text-outline-linear-gradient.jpg)
  
 変換されたテキストのストローク、塗りつぶし、強調表示を変更して、人の目をひく視覚効果を作成するいくつかの方法を次の例に示します。  
  
 ![塗りつぶしとストロークに別の色を使用するテキスト](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![イメージ ブラシがストロークとハイライトに適用されたテキスト](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 テキストを<xref:System.Windows.Media.Geometry>オブジェクトに変換すると、文字のコレクションではなく、テキスト文字列の文字を変更することはできません。 ただし、変換されたテキストのストロークおよび塗りつぶしのプロパティを変更することで、テキストの外観を変えることができます。 ストロークは、変換したテキストのアウトラインを参照します。塗りつぶしは、変換したテキストのアウトラインの内側の領域を参照します。 詳細については、「[方法: 中抜きの文字列を作成する](how-to-create-outlined-text.md)」を参照してください。  
  
 また、書式設定されたテキストを<xref:System.Windows.Media.PathGeometry>オブジェクトに変換し、オブジェクトを使用してテキストをハイライト表示することもできます。 たとえば、アニメーションを<xref:System.Windows.Media.PathGeometry>オブジェクトに適用して、アニメーションが書式設定されたテキストのアウトラインに従うようにすることができます。  
  
 次の例は、オブジェクトに変換された書式設定されたテキストを<xref:System.Windows.Media.PathGeometry>示しています。 アニメーション化された楕円は、レンダリングされたテキストのストロークのパスに従います。  
  
 ![テキストのパス ジオメトリに続く球](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
テキストのパス ジオメトリに続く球  
  
 詳細については、「[How to: Create a PathGeometry Animation for Text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))」(方法: テキストの PathGeometry アニメーションを作成する) を参照してください。  
  
 書式設定されたテキストをオブジェクトに変換すると、その他の興味深い用途を<xref:System.Windows.Media.PathGeometry>作成できます。 たとえば、ビデオをクリップしてテキスト内に表示することができます。  
  
 ![テキストのパス ジオメトリに表示されるビデオ](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>
## <a name="win32-migration"></a>Win32 の移行  
 テキストを<xref:System.Windows.Media.FormattedText>描画するための機能は、Win32 DrawText 関数の機能に似ています。 Win32 API から移行する開発者の場合、次の表は、Win32 DrawText フラグと同等[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の概算値を示しています。  
  
|DrawText フラグ|同等の WPF 操作|Notes|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|プロパティを<xref:System.Windows.Media.FormattedText.Height%2A>使用して、適切な Win32 DrawText 'y' 位置を計算します。|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|出力矩<xref:System.Windows.Media.FormattedText.Height%2A>形<xref:System.Windows.Media.FormattedText.Width%2A>を計算するには、 および プロパティを使用します。|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|このプロパティ<xref:System.Windows.Media.FormattedText.TextAlignment%2A>を使用し、値を<xref:System.Windows.TextAlignment.Center>に設定します。|  
|DT_EDITCONTROL|なし|不要。 スペースの幅および最後の行のレンダリングは、フレームワークのエディット コントロールと同じです。|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|プロパティを<xref:System.Windows.Media.FormattedText.Trimming%2A>値<xref:System.Windows.TextTrimming.CharacterEllipsis>と共に使用します。<br /><br /> Win32 DT_END_ELLIPSISを末尾の省略記号で取得DT_WORD_ELIPSIS場合に使用<xref:System.Windows.TextTrimming.WordEllipsis>します( この場合、文字の省略記号は 1 行に収まらない単語でのみ発生します)。|  
|DT_EXPAND_TABS|なし|不要。 タブは自動的に全角 4 文字分ごとに展開されます。これは、言語非依存文字の約 8 文字分の幅です。|  
|DT_EXTERNALLEADING|なし|不要。 外部レディングは、常に行間隔に含まれます。 ユーザー定義<xref:System.Windows.Media.FormattedText.LineHeight%2A>の行間を作成するには、このプロパティを使用します。|  
|DT_HIDEPREFIX|なし|サポートされていません。 オブジェクトを構築する前に、文字列から '&' を<xref:System.Windows.Media.FormattedText>削除します。|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|これは、テキストの配置の既定値です。 このプロパティ<xref:System.Windows.Media.FormattedText.TextAlignment%2A>を使用し、値を<xref:System.Windows.TextAlignment.Left>に設定します。 (WPF のみ)。|  
|DT_MODIFYSTRING|なし|サポートされていません。|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|クリッピングは自動的には行われません。 テキストをクリップする場合は、 プロパティ<xref:System.Windows.Media.Visual.VisualClip%2A>を使用します。|  
|DT_NOFULLWIDTHCHARBREAK|なし|サポートされていません。|  
|DT_NOPREFIX|なし|不要。 文字列内の '&' 文字は、常に通常の文字として扱われます。|  
|DT_PATHELLIPSIS|なし|プロパティを<xref:System.Windows.Media.FormattedText.Trimming%2A>値<xref:System.Windows.TextTrimming.WordEllipsis>と共に使用します。|  
|DT_PREFIX|なし|サポートされていません。 アクセラレータ キーやリンクなどのテキストにアンダースコアを使用する場合は、 メソッドを使用<xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>します。|  
|DT_PREFIXONLY|なし|サポートされていません。|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|このプロパティ<xref:System.Windows.Media.FormattedText.TextAlignment%2A>を使用し、値を<xref:System.Windows.TextAlignment.Right>に設定します。 (WPF のみ)。|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|<xref:System.Windows.Media.FormattedText.FlowDirection%2A> プロパティを <xref:System.Windows.FlowDirection.RightToLeft> に設定します。|  
|DT_SINGLELINE|なし|不要。 <xref:System.Windows.Media.FormattedText><xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>プロパティが設定されているか、テキストにキャリッジ リターン/ライン フィード (CR/LF) が含まれている場合を除き、オブジェクトは単一の行コントロールとして動作します。|  
|DT_TABSTOP|なし|ユーザー定義のタブ位置はサポートされていません。|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|不要。 上端揃えが既定値です。 他の垂直位置の値は、<xref:System.Windows.Media.FormattedText.Height%2A>適切な Win32 DrawText 'y' 位置を計算するプロパティを使用して定義できます。|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|プロパティを<xref:System.Windows.Media.FormattedText.Height%2A>使用して、適切な Win32 DrawText 'y' 位置を計算します。|  
|DT_WORDBREAK|なし|不要。 ワード改行は、オブジェクト<xref:System.Windows.Media.FormattedText>で自動的に行われます。 無効にすることはできません。|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|プロパティを<xref:System.Windows.Media.FormattedText.Trimming%2A>値<xref:System.Windows.TextTrimming.WordEllipsis>と共に使用します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.FormattedText>
- [WPF のドキュメント](documents-in-wpf.md)
- [WPF のタイポグラフィ](typography-in-wpf.md)
- [中抜きの文字列を作成する](how-to-create-outlined-text.md)
- [方法: テキストの PathGeometry アニメーションを作成する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
