---
title: OpenType フォントの機能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 52fe73bccd625c9508b398874fd6b075af2445e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186803"
---
# <a name="opentype-font-features"></a>OpenType フォントの機能

このトピックでは、 の OpenType フォント テクノロジの主な機能[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の概要を説明します。  
  
<a name="overview"></a>
## <a name="opentype-font-format"></a>OpenType フォントの書式  
 OpenType フォント形式は、TrueType® フォント形式の拡張であり、PostScript フォント データのサポートを追加します。 OpenType フォント形式は、マイクロソフトとアドビ株式会社が共同で開発しました。 OpenType フォントと OpenType フォントをサポートするオペレーティング システム サービスは、フォントに TrueType アウトラインまたは CFF (PostScript) アウトラインが含まれているかどうかにかかわらず、フォントを簡単にインストールして使用できるようにします。  
  
 OpenType フォント形式は、開発者の次の課題に対処します。  
  
- より広範なマルチプラットフォームのサポート。  
  
- 国際文字セットのサポート強化。  
  
- フォント データの保護強化。  
  
- ファイルのサイズを小さくして、より効率的にフォントを配布。  
  
- 高度なテキスト編集コントロールの幅広いサポート。  
  
> [!NOTE]
> Windows SDK には、アプリケーションで[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用できる OpenType フォントのサンプル セットが含まれています。 これらのフォントでは、このトピックで説明していく機能の大半が提供されています。 詳細については、「[OpenType フォント パックのサンプル](sample-opentype-font-pack.md)」を参照してください。  
  
OpenType フォント形式の詳細については[、OpenType 仕様](https://docs.microsoft.com/typography/opentype/spec/)を参照してください。  
  
### <a name="advanced-typographic-extensions"></a>高度なテキスト編集の拡張機能  
 高度なタイポグラフィテーブル (OpenType レイアウトテーブル) は、TrueType または CFF のアウトラインを使用してフォントの機能を拡張します。 OpenType レイアウト フォントには、高品質の国際線種法をサポートするためにフォントの機能を拡張する追加情報が含まれています。 ほとんどの OpenType フォントは、使用可能な OpenType 機能のサブセットのみを公開します。 OpenType フォントには、次の機能があります。  
  
- 合字、位置フォーム、代替、およびその他のフォント置換をサポートする、文字とグリフの間の充実したマッピング。  
  
- 2 次元配置とグリフ結合のサポート。  
  
- フォントには明示的なスクリプトと言語情報が含まれるため、テキスト処理アプリケーションはそれに従って動作を調整可能。  
  
 OpenType のレイアウトテーブルについては、OpenType 仕様の[「フォント ファイル テーブル」](https://www.microsoft.com/typography/otspec/otff.htm)で詳しく説明します。  
  
 この概要の残りの部分では、オブジェクトのプロパティによって公開される、視覚的に興味深い OpenType 機能の一部の幅と柔軟性<xref:System.Windows.Documents.Typography>について説明します。 このオブジェクトの詳細については、「[タイポグラフィ クラス](#typography_class)」を参照してください。  
  
<a name="variants"></a>
## <a name="variants"></a>バリアント  
 バリアントを使用して、上付き文字と下付きなどのさまざまなタイポグラフィ スタイルを表示します。  
  
### <a name="superscripts-and-subscripts"></a>上付き/下付きの文字  
 この<xref:System.Windows.Documents.Typography.Variants%2A>プロパティを使用すると、OpenType フォントの上付き文字と下付き文字の値を設定できます。  
  
 次のテキストは、Palatino Linotype フォントの上付き文字を示したものです。  
  
 ![OpenType の上付き文字を使用するテキスト](./media/opentype-font-features/opentype-superscripts.gif "OpenType の上付き文字を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して、パラティーノ Linotype フォントの<xref:System.Windows.Documents.Typography>上付き文字を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 次のテキストは、パラティーノ Linotype フォントの下付き文字を表示します。  
  
 ![OpenType の下付き文字を使用するテキスト](./media/opentype-font-features/opentype-subscripts.gif "OpenType の下付き文字を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して、パラティーノ Linotype フォントの<xref:System.Windows.Documents.Typography>添え字を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>上付き文字と下付き文字の装飾的な用途  
 上付き文字と下付き文字を使用して、大文字と小文字が混在したテキストに装飾的効果をつけることもできます。 次のテキストは、Palatino Linotype フォントの上付き文字と下付き文字を示したものです。 大文字には影響がないことに注目してください。  
  
 ![OpenType の上付き文字と下付き文字を使用するテキスト](./media/opentype-font-features/opentype-superscripts-subscripts.gif "OpenType の上付き文字と下付き文字を使用するテキスト")  

 次のマークアップの例は、オブジェクトのプロパティを使用して、フォントの上付き文字と<xref:System.Windows.Documents.Typography>下付き文字を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>
## <a name="capitals"></a>大文字  
 大文字は、大文字スタイルのグリフでテキストをレンダリングするタイポグラフィ形式のセットです。 通常、テキストをすべて大文字で表示すると、文字間隔が狭すぎるように見え、文字の印象と縦横比が重すぎるように感じられます。 OpenType では、小さな大文字、小さな大文字、タイトリング、および資本間隔など、多数の大文字スタイル形式がサポートされています。 これらのスタイル形式を使用して、英大文字の外観を変えることができます。  
  
 次のテキストは、Pescadero フォントの標準の大文字と、その後に "SmallCaps" および "AllSmallCaps" のスタイルをあてた文字を示したものです。 この場合、3 つの単語すべてに同じフォント サイズが使用されます。  
  
 ![OpenType の大文字を使用するテキスト](./media/opentype-font-features/opentype-capitals.gif "OpenType の大文字を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して、Pescadero フォントの大文字<xref:System.Windows.Documents.Typography>を定義する方法を示しています。 "SmallCaps" 形式を使用する場合は、先頭の大文字は無視されます。  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>タイトル用大文字  
 タイトル用大文字は、重みと縦横比が軽く、標準の大文字よりも洗練された印象を与えるように設計されています。 通常、大文字は、見出しとして大きなフォントサイズで使用されます。 次のテキストは、ペスカデロフォントの標準とタイトリングの大文字を表示します。 2 行目のテキストのステム幅が狭くなります。  
  
 ![OpenType のタイトル大文字を使用するテキスト](./media/opentype-font-features/opentype-titling-capitals.gif "OpenType のタイトル大文字を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して、ペスカデロ フォントの大文字を定義<xref:System.Windows.Documents.Typography>する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>大文字スペーシング  
 大文字スペーシングは、テキストをすべて大文字にする場合に間隔を広くする機能です。 大文字は、通常、小文字とブレンドするように設計されています。 大文字と小文字の間に魅力的に見える間隔と小文字が、すべての大文字を使用すると、あまりにもタイトに見える場合があります。 次のテキストは、ペスカデロ フォントの標準と大文字の間隔を示します。  
  
 ![OpenType の大文字スペーシングを使用するテキスト](./media/opentype-font-features/opentype-capital-spacing.gif "OpenType の大文字スペーシングを使用するテキスト")  

 次のマークアップの例は、オブジェクトのプロパティを使用して、Pescadero フォントの大文字<xref:System.Windows.Documents.Typography>と同じスペースを定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>
## <a name="ligatures"></a>合字  
 合字とは、2 つ以上のグリフを、より読みやすい、あるいはより魅力的なテキストにするために、1 つのグリフに形成したものです。 OpenType フォントは、次の 4 種類の合字をサポートします。  
  
- **標準合字**。 読みやすさを高めるように設計されています。 標準合字には、"fi"、"fl" および "ff" があります。  
  
- **コンテキスト合字**。 合字を構成する文字の間の結合を向上させることによって、読みやすさを高めるよう設計されています。  
  
- **随意合字**。 装飾を加える設計で、特に読みやすくなるようには設計されていません。  
  
- **歴史的合字**。 歴史的な記述に相応しい設計で、特に読みやすくなるようには設計されていません。  
  
 次のテキストは、Pericles フォントの標準合字グリフを示したものです。  
  
 ![OpenType の標準合字を使用するテキスト](./media/opentype-font-features/opentype-standard-ligatures.gif "OpenType の標準合字を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して Pericles フォントの標準合字グリフ<xref:System.Windows.Documents.Typography>を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 次のテキストは、Pericles フォントの随意合字グリフを示したものです。  
  
 ![OpenType の随意合字を使用するテキスト](./media/opentype-font-features/opentype-discretionary-ligatures.gif "OpenType の随意合字を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して Pericles フォントの随意合字グリフ<xref:System.Windows.Documents.Typography>を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 既定では、OpenType フォント[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]で標準合字が有効になります。 たとえば、Palatino Linotype フォントを使用する場合、標準合字 "fi"、"ff" および "fl" は組み合わせ文字グリフとして表示されます。 各標準合字の文字のペアが互いに接触していることに注意してください。  
  
 ![パラティーノ・リノタイプを使用した OpenType 標準合字を使用したテキスト](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "パラティーノ・リノタイプを使用した OpenType 標準合字を使用したテキスト")

 ただし、標準合字機能を無効にして、"ff" などの標準合字が、組み合わせ文字グリフとしてではなく、2 つの別々のグリフとして表示されるようにできます。  
  
 ![OpenType の無効な標準合字を使用するテキスト](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "OpenType の無効な標準合字を使用するテキスト")  

 次のマークアップの例は、オブジェクトのプロパティを使用して、パラティーノ Linotype フォントの標準合字<xref:System.Windows.Documents.Typography>グリフを無効にする方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>
## <a name="swashes"></a>飾り付き  
 飾り付きは装飾的なグリフで、カリグラフィを連想させる、手の込んだ装飾が使用されます。 次のテキストは、ペスカデロフォントの標準およびスワッシュグリフを表示します。  
  
 ![OpenType の標準グリフと飾り付きグリフを使用するテキスト](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "OpenType の標準グリフと飾り付きグリフを使用するテキスト")  

 飾り付きは、季節のご挨拶などの短いフレーズで装飾的な要素としてよく使用されます。 次のテキストでは、イベント名の大文字を強調するために、swasッシュを使用しています。  
  
 ![OpenType の飾り付きを使用するテキスト](./media/opentype-font-features/opentype-swashes.gif "OpenType の巻き髭を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して、フォントの swashes を定義する方法を<xref:System.Windows.Documents.Typography>示しています。  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>コンテキスト飾り付き  
 飾り付きグリフの特定の組み合わせでは、隣りあう文字の下に延びる部分が重なり合うなど、美しくない外観になる可能性があります。 コンテキスト スワッシュを使用すると、外観を向上させる代用のスワッシュ グリフを使用できます。 次のテキストは、コンテキスト スワッシュが適用される前後の同じ単語を示しています。  
  
 ![OpenType のコンテキスト飾り付きを使用するテキスト](./media/opentype-font-features/opentype-contextual-swashes.gif "OpenType のコンテキスト巻き髭を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して、Pescadero フォントのコンテキスト スワ<xref:System.Windows.Documents.Typography>ッシュを定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>
## <a name="alternates"></a>代替  
 代替文字は、標準的なグリフの代わりに使用できるグリフです。 次の例で使用されている Pericles フォントなどの OpenType フォントには、テキストに対して異なる外観を作成するために使用できる代替グリフを含めることができます。 次のテキストは、Pericles フォントの標準グリフを示したものです。  
  
 ![OpenType の標準グリフを使用するテキスト](./media/opentype-font-features/opentype-standard-glyphs.gif "OpenType の標準グリフを使用するテキスト")  

 Pericles OpenType フォントには、標準のグリフセットに対するスタイルの代替を提供する追加のグリフが含まれています。 次のテキストでは、スタイル代替グリフが表示されています。  
  
 ![OpenType のスタイル代替グリフを使用するテキスト](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "OpenType のスタイル代替グリフを使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して Pericles フォントのスタイルの代替グリフ<xref:System.Windows.Documents.Typography>を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 次のテキストは、Pericles フォントの他のいくつかのスタイルの代替グリフを表示します。  
  
 ![Pericles フォントの OpenType スタイル代替グリフを使用するテキスト](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Pericles フォントの OpenType スタイル代替グリフを使用するテキスト")

 次のマークアップの例では、これらの他のスタイル代替グリフを定義する方法を示します。  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>ランダムなコンテキスト代替  
 ランダムなコンテキスト代替は、単一文字に複数の代替グリフを提供します。 スクリプトタイプフォントを使用して実装すると、この機能は、外観がわずかに異なるランダムに選択された一連のグリフを使用して手書きをシミュレートできます。 次のテキストでは、Lindsey フォントに対してランダムなコンテキスト代替を使用しています。 文字 "a" の外観が少し異なっていることに注意してください。  
  
 ![OpenType のランダムなコンテキスト代替を使用するテキスト](./media/opentype-font-features/opentype-random-contextual-alternates.gif "OpenType のランダムなコンテキスト代替を使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して、Lindsey フォントのランダム コンテキスト<xref:System.Windows.Documents.Typography>代替を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>歴史的形式  
 歴史的形式は、過去に一般的であった表示形式です。 次のテキストは、パラティーノ・リノタイプフォントのグリフの歴史的形式を使用して、「ボストン、マサチューセッツ」というフレーズを表示します。  
  
 ![OpenType の歴史的形式を使用するテキスト](./media/opentype-font-features/opentype-historical-forms.gif "OpenType の履歴フォームを使用するテキスト")  

 次のマークアップの例は、オブジェクトのプロパティを使用して、パラティーノ Linotype フォントの<xref:System.Windows.Documents.Typography>履歴フォームを定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>
## <a name="numerical-styles"></a>数値スタイル  
 OpenType フォントでは、テキスト内の数値に使用できる数多くの機能をサポートします。  
  
### <a name="fractions"></a>小数  
 OpenType フォントは、スラッシュやスタックなどの分数のスタイルをサポートします。  
  
 次のテキストは、Palatino Linotype フォントの小数スタイルを示したものです。  
  
 ![OpenType の分数 (横) と分数 (縦) を使用するテキスト](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "OpenType の分数 (横) と分数 (縦) を使用するテキスト")  

 次のマークアップの例は、オブジェクトのプロパティを使用して、パラティーノ Linotype フォントの<xref:System.Windows.Documents.Typography>分数スタイルを定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>旧式スタイルの数字  
 OpenType フォントは、古いスタイルの数字形式をサポートしています。 この形式は、もはや標準ではなくなったスタイルで数字を表示するのに便利です。 次のテキストは、パラティーノ Linotype フォントの標準および古いスタイルの数字形式で 18 世紀の日付を表示します。  
  
 ![OpenType の古いスタイルの数字を使用するテキスト](./media/opentype-font-features/opentype-old-style-numerals.gif "OpenType の古いスタイルの数字を使用するテキスト")  

 次のテキストは、Palatino Linotype フォントの標準の数字と、旧式スタイルの数字を示したものです。  
  
 ![OpenType の旧式スタイルの数字セットを使用するテキスト](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "OpenType の古いスタイルの数字セットを使用するテキスト")  
  
 次のマークアップの例は、オブジェクトのプロパティを使用して、パラティーノ Linotype フォントの古いスタイルの<xref:System.Windows.Documents.Typography>数字を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>プロポーショナルと表形式の数字  
 OpenType フォントは、数値を使用する場合の幅の配置を制御する比例および表形式の図形機能をサポートします。 プロポーショナルの数字では、それぞれの数字は異なる幅を持つものとして扱われます。たとえば "1" は "5" より狭い幅です。 表形式の数値は、縦方向に整列するように等幅の数字として扱われ、財務タイプ情報の読みやすさが向上します。  
  
 次のテキストは、Miramonte フォントを使用して、最初の列に 2 つの比例図形を表示します。 数字の「5」と「1」の間の幅の違いに注意してください。 2 番目の列には、表形式の図形機能を使用して調整された幅を持つ同じ 2 つの数値が表示されます。  
  
 ![OpenType のプロポーショナルと表形式の数字を使用するテキスト](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "OpenType のプロポーショナルと表形式の数字を使用するテキスト")  

 次のマークアップの例は、オブジェクトのプロパティを使用して、Miramonte フォントの比例図形と<xref:System.Windows.Documents.Typography>表形式の図形を定義する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>スラッシュ付きゼロ  
 OpenType フォントは、スラッシュゼロの数字形式をサポートし、文字 "O" と数字 "0" の違いを強調します。 スラッシュ付きゼロは、財務およびビジネス情報における ID によく使用されます。  
  
 次のテキストは、Miramonte フォントを使用したサンプル注文識別子を示しています。 最初の行では、標準の数字を使用します。 2 行目では、大文字の "O" 文字とのコントラストを向上させるためにスラッシュゼロ数字を使用しました。  
  
 ![OpenType のスラッシュ付きのゼロを使用するテキスト](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "OpenType のスラッシュ付きのゼロを使用するテキスト")  

 次のマークアップの例は、オブジェクトのプロパティを使用して、Miramonte フォントのスラッシュゼロの数字を定義<xref:System.Windows.Documents.Typography>する方法を示しています。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>
## <a name="typography-class"></a>タイポグラフィ クラス  
 この<xref:System.Windows.Documents.Typography>オブジェクトは、OpenType フォントがサポートする機能のセットを公開します。 マークアップ<xref:System.Windows.Documents.Typography>のプロパティを設定することで、OpenType 機能を利用するドキュメントを簡単に作成できます。  
  
 次のテキストは、Pescadero フォントの標準の大文字と、その後に "SmallCaps" および "AllSmallCaps" のスタイルをあてた文字を示したものです。 この場合、3 つの単語すべてに同じフォント サイズが使用されます。  
  
 ![OpenType の大文字を使用するテキスト](./media/opentype-font-features/opentype-capitals.gif "OpenType の大文字を使用するテキスト")  

 次のマークアップの例は、オブジェクトのプロパティを使用して、Pescadero フォントの大文字<xref:System.Windows.Documents.Typography>を定義する方法を示しています。 "SmallCaps" 形式を使用する場合は、先頭の大文字は無視されます。  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 次のコード例では、前のマークアップの例と同じタスクを実行します。  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>タイポグラフィ クラスのプロパティ  
 次の表に、オブジェクトのプロパティ、値、および既定の<xref:System.Windows.Documents.Typography>設定を示します。  
  
|プロパティ|値|Default value|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji><xref:System.Windows.FontEastAsianLanguage.Jis83> <xref:System.Windows.FontEastAsianLanguage.Jis90> <xref:System.Windows.FontEastAsianLanguage.NlcKanji> <xref:System.Windows.FontEastAsianLanguage.Normal> &#124;&#124;&#124;を&#124;&#124; &#124;&#124;&#124;&#124;&#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> <xref:System.Windows.FontEastAsianLanguage.Jis04> <xref:System.Windows.FontEastAsianLanguage.Jis78> <xref:System.Windows.FontEastAsianLanguage.Traditional><xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full>&#124; <xref:System.Windows.FontEastAsianWidths.Half> <xref:System.Windows.FontEastAsianWidths.Quarter> <xref:System.Windows.FontEastAsianWidths.Normal> &#124;&#124;&#124;&#124; <xref:System.Windows.FontEastAsianWidths.Proportional><xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior>&#124; <xref:System.Windows.FontVariants.Normal> <xref:System.Windows.FontVariants.Subscript> <xref:System.Windows.FontVariants.Ordinal> &#124;&#124;&#124;&#124; <xref:System.Windows.FontVariants.Ruby><xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Documents.Typography>
- [オープンタイプ仕様](https://docs.microsoft.com/typography/opentype/spec/)
- [WPF のタイポグラフィ](typography-in-wpf.md)
- [OpenType フォント パックのサンプル](sample-opentype-font-pack.md)
- [アプリケーションでのフォントのパッケージング](packaging-fonts-with-applications.md)
