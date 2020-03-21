---
title: GlyphRun オブジェクトと Glyphs 要素の概要
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181961"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>GlyphRun オブジェクトと Glyphs 要素の概要
このトピックでは、<xref:System.Windows.Media.GlyphRun>オブジェクトと要素について<xref:System.Windows.Documents.Glyphs>説明します。  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a>GlyphRun の概要  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]書式設定後にテキストをインターセプトして永続化する顧客に直接アクセス<xref:System.Windows.Documents.Glyphs>できるグリフ レベルのマークアップを含む高度なテキスト サポートを提供します。 これらの機能は、下記のようなシナリオでのさまざまなテキスト レンダリング要件をサポートする不可欠なものです。  
  
1. 固定形式のドキュメントの画面表示。  
  
2. 印刷シナリオ。  
  
    - デバイス プリンター言語としての [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
    - マイクロソフト XPS ドキュメント ライター。  
  
    - 以前のプリンター ドライバー、Win32 アプリケーションから固定形式に出力します。  
  
    - 印刷スプール形式。  
  
3. 以前のバージョンの Windows やその他のコンピューティング デバイス用のクライアントを含む、固定形式のドキュメント表現。  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>固定<xref:System.Windows.Media.GlyphRun>形式のドキュメントプレゼンテーションおよび印刷シナリオ用に設計されています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]には、一般的なレイアウトや[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]シナリオなど<xref:System.Windows.Controls.Label>、いくつかの<xref:System.Windows.Controls.TextBlock>要素が用意されています。 レイアウトと[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]シナリオの詳細については、 WPF の[文字体裁](typography-in-wpf.md)を参照してください。  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a>GlyphRun オブジェクト  
 オブジェクト<xref:System.Windows.Media.GlyphRun>は、単一のフォントの単一の面から単一のサイズで、単一のレンダリング スタイルでのグリフのシーケンスを表します。  
  
 <xref:System.Windows.Media.GlyphRun>には、グリフや個々のグリフ<xref:System.Windows.Documents.Glyphs.Indices%2A>の位置などのフォントの詳細が含まれます。 また、実行元の Unicode コード ポイント、文字からグリフへのバッファー オフセット マッピング情報、および文字単位およびグリフごとのフラグも含まれます。  
  
 <xref:System.Windows.Media.GlyphRun>には、対応する高レベル<xref:System.Windows.FrameworkElement> <xref:System.Windows.Documents.Glyphs>、 を持ちます。 <xref:System.Windows.Documents.Glyphs>は、要素ツリーおよびマークアップで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]出力を表すために<xref:System.Windows.Media.GlyphRun>使用できます。  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a>Glyphs 要素  
 要素<xref:System.Windows.Documents.Glyphs>は、 の出力を<xref:System.Windows.Media.GlyphRun>表[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 要素を記述するために、次のマークアップ構文<xref:System.Windows.Documents.Glyphs>を使用します。  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 次のプロパティの定義は、サンプルのマークアップ内の最初の 4 つの属性に対応しています。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|リソース識別子 (ファイル名、Web ユニフォーム リソース識別子 (URI)、またはアプリケーション .exe またはコンテナー内のリソース参照を指定します。|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|フォント サイズを描画サーフェイスの単位で指定します (既定値は .96 インチ)。|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|太字や斜体のスタイルのフラグを指定します。|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|双方向のレイアウト レベルを指定します。 偶数とゼロの値は左から右のレイアウトを意味し、奇数の値は右から左のレイアウトを意味します。|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a>Indices プロパティ  
 プロパティ<xref:System.Windows.Documents.Glyphs.Indices%2A>はグリフの指定の文字列です。 グリフのシーケンスが 1 つのクラスターを形成している場合、クラスター内の最初のグリフの仕様は、クラスターを形成するために組み合わせるグリフの数とコード ポイントの数の仕様によって先行されます。 プロパティ<xref:System.Windows.Documents.Glyphs.Indices%2A>は、次のプロパティを 1 つの文字列で収集します。  
  
- グリフ インデックス  
  
- グリフアドバンス幅  
  
- グリフの結合ベクトルの結合  
  
- コード ポイントからグリフへのクラスタ マッピング  
  
- グリフフラグ  
  
 各グリフの仕様には、次の形式があります。  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a>グリフのメトリック  
 各グリフは、他<xref:System.Windows.Documents.Glyphs>の グリフとの位置合わせ方法を指定するメトリックを定義します。 次の図では、2 つの異なるグリフ文字のさまざまな印刷用品質を定義しています。  
  
 ![グリフ単位のダイアグラム](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a>グリフ マークアップ  
 次のコード例は、 で<xref:System.Windows.Documents.Glyphs>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素のさまざまなプロパティを使用する方法を示しています。  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>関連項目

- [WPF のタイポグラフィ](typography-in-wpf.md)
- [WPF のドキュメント](documents-in-wpf.md)
- [テキスト](optimizing-performance-text.md)
