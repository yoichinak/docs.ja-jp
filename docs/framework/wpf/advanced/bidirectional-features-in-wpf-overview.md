---
title: WPF の双方向機能の概要
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: a3a991a841182438dca4ef0a4067d333180f4f60
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380177"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF の双方向機能の概要
その他の開発プラットフォームとは異なり[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]双方向コンテンツの迅速な開発をサポートする多くの機能、たとえば、データを同じドキュメント内まま混合の左から右、および右にします。 同時に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]双方向機能のアラビア語やヘブライ語を話すユーザーなどを必要とするユーザー用の優れたエクスペリエンスを作成します。  
  
 以降のセクションでは、多数の双方向機能と双方向コンテンツを最適に表示した例について説明します。 ほとんどのサンプルを使用して、[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]しておくべき概念を簡単に適用できますが、C#または Microsoft Visual Basic コードです。  

<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 コンテンツのフローの方向を定義する基本的なプロパティ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが<xref:System.Windows.FrameworkElement.FlowDirection%2A>します。 このプロパティは、2 つの列挙値のいずれかに設定できます<xref:System.Windows.FlowDirection.LeftToRight>または<xref:System.Windows.FlowDirection.RightToLeft>します。 プロパティがすべて使用できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素から継承する<xref:System.Windows.FrameworkElement>します。  
  
 次の例のフロー方向を設定する、<xref:System.Windows.Controls.TextBox>要素。  
  
 **左から右へ記述するフロー方向**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **右から左へ記述するフロー方向**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 次の図は、前のコードがどのように表示されるのかを示します。  
    
 ![さまざまなフロー方向を示す図。](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 内の要素を[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]ツリーは、継承、<xref:System.Windows.FrameworkElement.FlowDirection%2A>コンテナーから。 次の例では、<xref:System.Windows.Controls.TextBlock>内では、<xref:System.Windows.Controls.Grid>に存在する、<xref:System.Windows.Window>します。 設定、<xref:System.Windows.FrameworkElement.FlowDirection%2A>の<xref:System.Windows.Window>設定することの意味、<xref:System.Windows.Controls.Grid>と<xref:System.Windows.Controls.TextBlock>もします。  
  
 次の例では、設定<xref:System.Windows.FrameworkElement.FlowDirection%2A>します。  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 最上位レベル<xref:System.Windows.Window>が、 <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>でそれに含まれるすべての要素と同じ継承もあるため、<xref:System.Windows.FrameworkElement.FlowDirection%2A>します。 指定されたをオーバーライドする要素の<xref:System.Windows.FrameworkElement.FlowDirection%2A>など、2 つ目の明示的な方向変更を追加する必要があります<xref:System.Windows.Controls.TextBlock>を変更する前の例で<xref:System.Windows.FlowDirection.LeftToRight>します。 ない場合<xref:System.Windows.FrameworkElement.FlowDirection%2A>が定義されている既定の<xref:System.Windows.FlowDirection.LeftToRight>適用されます。  
  
 次の図は、前の例の出力を示しています。

 ![明示的なフロー方向の変更を示しています。 グラフィック。](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 などの多くの開発プラットフォーム[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]および Java は、双方向コンテンツ開発の特別なサポートを提供します。 などのマークアップ言語[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]コンテンツの作成者など、必要な任意の方向にテキストを表示するために必要なマークアップを与える、 [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 タグの"dir"を値として"rtl"または"ltr"を受け取る。 このタグはのような<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティが、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティはテキスト コンテンツのレイアウトをより高度な方法で動作し、テキスト以外のコンテンツに使用できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、 <xref:System.Windows.Documents.FlowDocument> 、柔軟性が[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]テキスト、テーブル、イメージ、およびその他の要素の組み合わせをホストできる要素です。 以下のセクションのサンプルでは、この要素を使用します。  
  
 テキストを追加、<xref:System.Windows.Documents.FlowDocument>複数の方法で実行できます。 簡単な方法は、<xref:System.Windows.Documents.Paragraph>テキストなどのグループのコンテンツに使用するブロック レベル要素であります。 テキストのサンプルを使用して、インライン レベルの要素を追加する<xref:System.Windows.Documents.Span>と<xref:System.Windows.Documents.Run>します。 <xref:System.Windows.Documents.Span> その他のインライン要素をグループ化するために使用されるインライン レベル フロー コンテンツ要素は、中、<xref:System.Windows.Documents.Run>インライン レベル フロー コンテンツ要素の書式設定されていないテキストを格納するためのものでは、します。 A<xref:System.Windows.Documents.Span>複数含めることができます<xref:System.Windows.Documents.Run>要素。  
  
 ドキュメントの最初の例には、共有名です。 ネットワークの数を持つドキュメントが含まれています。たとえば`\\server1\folder\file.ext`します。 このネットワーク リンクがアラビア語または英語のいずれのドキュメントにあっても、常に同じように表示する必要があります。 次の図を選択し、Span 要素を使用して、アラビア語で、リンクを示します<xref:System.Windows.FlowDirection.RightToLeft>ドキュメント。

 ![Span 要素の使用を示す図。](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 テキストなので<xref:System.Windows.FlowDirection.RightToLeft>、すべての特殊ななど、文字、"\\"、右から左へテキストを区切ります。 そのため、問題を解決するテキストに埋め込む必要がある個別に保持するためには、正しい順序で表示されていないリンクで、結果を<xref:System.Windows.Documents.Run>フロー<xref:System.Windows.FlowDirection.LeftToRight>します。 個別のではなく<xref:System.Windows.Documents.Run>問題を解決する方法の向上がより大きいアラビア語に使用頻度の低い英語のテキストを埋め込むためには、各言語の<xref:System.Windows.Documents.Span>します。  
  
 次の図は、Span 要素に埋め込まれた実行要素を使用して、これを示しています。

 ![Span 要素には、実行の要素を示しています。 グラフィックが埋め込まれます。](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 次の例を使用して<xref:System.Windows.Documents.Run>と<xref:System.Windows.Documents.Span>ドキュメント内の要素。  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span 要素  
 <xref:System.Windows.Documents.Span>要素は、フロー方向が異なるテキスト間の境界区切り記号としては機能します。  でも<xref:System.Windows.Documents.Span>同じフローの方向を持つ要素をことを意味する別の双方向スコープを持つと見なされます、<xref:System.Windows.Documents.Span>でコンテナーの要素が順序付けられた<xref:System.Windows.FlowDirection>、内のコンテンツのみ、<xref:System.Windows.Documents.Span>要素次の<xref:System.Windows.FlowDirection>の<xref:System.Windows.Documents.Span>します。  
  
 次の図は、いくつかのフロー方向を示しています。<xref:System.Windows.Controls.TextBlock>要素。  
    
 ![フロー方向が異なるテキスト ブロックを示しています。 グラフィック。](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 次の例は、使用する方法を示します、<xref:System.Windows.Documents.Span>と<xref:System.Windows.Documents.Run>前の図に示すように結果を生成する要素。  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 <xref:System.Windows.Controls.TextBlock>サンプルでは、要素、<xref:System.Windows.Documents.Span>要素のレイアウトに従って、<xref:System.Windows.FlowDirection>親が各内のテキストの<xref:System.Windows.Documents.Span>に従って独自の要素のフロー<xref:System.Windows.FlowDirection>します。 これは、ラテン語やアラビア語だけでなく、他のどの言語にも当てはまります。  
  
### <a name="adding-xmllang"></a>xml:lang の追加  
 次の図などの数値と算術式を使用する別の例を示しています。`"200.0+21.4=221.4"`します。 だけ、<xref:System.Windows.FlowDirection>設定されます。  
    
 ![FlowDirection のみを使用して数値を表示するグラフィック。](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 このアプリケーションのユーザーは残念ながら、出力が場合でも、<xref:System.Windows.FlowDirection>が正しい番号がないの形状にアラビア数字の形状になる必要があります。  
  
 XAML 要素を含めることができます、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]属性 (`xml:lang`) の各要素の言語を定義します。 XAML もサポートしています、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]言語の原則もそれにより`xml:lang`ツリーの親要素に適用される値の子要素によって使用されます。 前の例での言語が定義されていませんので、<xref:System.Windows.Documents.Run>要素または上のいずれかのレベルの要素の場合、既定`xml:lang`を使用したある`en-US`XAML の。 内部数字形成アルゴリズム[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ここでは英語での対応する言語では: 数字が選択されます。 アラビア語版を使用する数字を正しく表示`xml:lang`を設定する必要があります。  
  
 次の図で例を示します`xml:lang`を追加します。  
    
 ![右から左にフロー アラビア数字を示す図。](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 次の例では、追加`xml:lang`アプリケーションにします。  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 多くの言語が異なることに注意してください`xml:lang`対象となる地域に応じて値`"ar-SA"`と`"ar-EG"`アラビア語の 2 つのバリエーションを表します。 両方を定義する必要がある、前の例を示しています、`xml:lang`と<xref:System.Windows.FlowDirection>値。  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>非テキスト要素のある FlowDirection  
 <xref:System.Windows.FlowDirection> テキストがテキストの要素も他のほぼすべてのフローの方向にフローする方法だけでなく定義[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素。 次の図は、<xref:System.Windows.Controls.ToolBar>水平方向を使用する<xref:System.Windows.Media.LinearGradientBrush>右のグラデーションを左には、その背景を描画するためにします。  

 ![ツールバーを左右のグラデーションからを示しています。 グラフィック。](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 設定した後、<xref:System.Windows.FlowDirection>に<xref:System.Windows.FlowDirection.RightToLeft>だけでなく、<xref:System.Windows.Controls.ToolBar>ボタンが右から左があっても、配置された<xref:System.Windows.Media.LinearGradientBrush>によりそのオフセットが右から左にフローします。  
  
 次の図は、再構成された、<xref:System.Windows.Media.LinearGradientBrush>します。  
    
 ![ツールバーを右左のグラデーションからを示しますグラフィック。](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 次の例では、描画、 <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.Controls.ToolBar>します。 (描画左右から、削除、<xref:System.Windows.FlowDirection>属性を<xref:System.Windows.Controls.ToolBar>します。  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection の例外  
 いくつかのケースがある場所<xref:System.Windows.FlowDirection>期待どおりに動作しません。 ここでは、そのような例外を 2 つ取り上げて説明します。  
  
 **イメージ**  
  
 <xref:System.Windows.Controls.Image>イメージを表示するコントロールを表します。 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]で使える、<xref:System.Windows.Controls.Image.Source%2A>プロパティを定義する、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]の<xref:System.Windows.Controls.Image>を表示します。  
  
 その他とは異なり[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、要素、<xref:System.Windows.Controls.Image>を継承しません、<xref:System.Windows.FlowDirection>コンテナーから。 ただし場合、<xref:System.Windows.FlowDirection>明示的に設定されて<xref:System.Windows.FlowDirection.RightToLeft>、<xref:System.Windows.Controls.Image>水平方向に反転表示されます。 これは、双方向コンテンツの開発者にとって便利な機能として実装されています。場合によっては、イメージを左右反転して表示することで必要な効果が得られるためです。  
  
 次の図は、反転<xref:System.Windows.Controls.Image>します。  
    
 ![反転されたイメージを示しています。 グラフィック。](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 次の例を示しますが、<xref:System.Windows.Controls.Image>継承に失敗する、<xref:System.Windows.FlowDirection>から、<xref:System.Windows.Controls.StackPanel>含まれています。 **注**という名前のファイルがある必要があります**ms_logo.jpg** c:\この例を実行するドライブ。  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **注**ダウンロード ファイルに含まれているは、 **ms_logo.jpg**ファイル。 コードは、この .jpg ファイルがプロジェクト内ではなく、C:\ ドライブ上にあることを前提としています。 プロジェクト内のファイルを検索するためには、プロジェクト ファイルから C:\ドライブに .jpg をコピーするかコードを変更する必要があります。 この変更を行う`Source="file://c:/ms_logo.jpg"`に`Source="ms_logo.jpg"`します。  
  
 **パス**  
  
 加え、 <xref:System.Windows.Controls.Image>、もう 1 つの興味深い要素は<xref:System.Windows.Shapes.Path>します。 パスは、接続された一連の線と曲線を描画できるオブジェクトです。 同様の方法で動作、<xref:System.Windows.Controls.Image>に関するその<xref:System.Windows.FlowDirection>。 たとえば、 <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>の水平方向のミラーの<xref:System.Windows.FlowDirection.LeftToRight>いずれか。 ただしとは異なり、 <xref:System.Windows.Controls.Image>、<xref:System.Windows.Shapes.Path>継承その<xref:System.Windows.FlowDirection>コンテナーと 1 つからしなくても、明示的に指定します。  
  
 次の例では、3 本の線を使用して単純な矢印を描画します。 最初の矢印は、<xref:System.Windows.FlowDirection.RightToLeft>フローの方向から、<xref:System.Windows.Controls.StackPanel>その始点と終点が右側を起点として計測されるようにします。 2 番目の矢印は、明示的な<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>も右側にある開始します。 ただし、3 番目の矢印の起点は左側です。 参照の描画の詳細については<xref:System.Windows.Media.LineGeometry>と<xref:System.Windows.Media.GeometryGroup>します。  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 次の図では、前の例の出力を示しますを使用して描画する矢印の付いた、`Path`要素。

 ![パス要素を使用して描画する矢印を示す図。](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 <xref:System.Windows.Controls.Image>と<xref:System.Windows.Shapes.Path>方法の 2 つの例は[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用<xref:System.Windows.FlowDirection>します。 レイアウトの横にある[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、コンテナー内の特定の方向に要素<xref:System.Windows.FlowDirection>などの要素で使用できる<xref:System.Windows.Controls.InkPresenter>、表面にインクをレンダリングする<xref:System.Windows.Media.LinearGradientBrush>、<xref:System.Windows.Media.RadialGradientBrush>します。 右左の動作からを左右の動作からを模倣したコンテンツの必要がある場合またはその逆[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]その機能を提供します。  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>数字の置換  
 従来、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]の例の数値が格納されているために、異なるロケール間で統合されたこれらの数字の内部記憶域を維持しながら、同じ数字のさまざまな文化的な図形で表現できるようにして数字の置換がサポートされていますよく知られた 16 進値、0x40、0x41、表示、選択した言語は。  
  
 これを 1 つの言語に変換することがなく、数値を処理するアプリケーションを許可するが、たとえば、ユーザーが開くことができます、[!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]ローカライズされたアラビア語のスプレッドシート[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]で開く、アラビア語の形状の数字を参照してくださいヨーロッパ言語バージョン[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]と、同じ数字のヨーロッパ語表現を参照してください。 これは、コンマ区切りやパーセント記号などの他の記号でも必要です。これらの記号は、通常同じドキュメント内で数字を伴っているからです。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は引き続きこの機能を備え、置換を使用するタイミングと方法をユーザーがさらに制御できるようにこの機能のサポートが強化されています。 この機能はすべての言語向けに設計されていますが、アプリケーションが実行される可能性のあるカルチャが多岐にわたるために特定の言語に合わせて数字の形状を設定することがアプリケーション開発者にとって通常は問題となる双方向コンテンツに対して特に有用です。  
  
 数字の置換を制御するコア プロパティは[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>依存関係プロパティ。 <xref:System.Windows.Media.NumberSubstitution>クラスは、テキスト内の数字の表示方法を指定します。 その動作を定義する 3 つのパブリック プロパティがあります。 以下は、各プロパティの概要です。  
  
 **CultureSource:**  
  
 このプロパティは、数字のカルチャを決定する方法を指定します。 3 つの時間を要する<xref:System.Windows.Media.NumberCultureSource>列挙値。  
  
- オーバーライドします。数字カルチャの<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>プロパティ。  
  
- テキスト:数字カルチャは、テキスト ランのカルチャです。 マークアップで`xml:lang`、またはそのエイリアス`Language`プロパティ (<xref:System.Windows.FrameworkElement.Language%2A>または<xref:System.Windows.FrameworkContentElement.Language%2A>)。 派生したクラスの既定値はまた、<xref:System.Windows.FrameworkContentElement>します。 このようなクラスを含める<xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>、 <xref:System.Windows.Documents.Table?displayProperty=nameWithType>、<xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>など。  
  
- ユーザー:数字カルチャは、現在のスレッドのカルチャです。 このプロパティのすべてのサブクラスの既定値は、<xref:System.Windows.FrameworkElement>など<xref:System.Windows.Controls.Page>、<xref:System.Windows.Window>と<xref:System.Windows.Controls.TextBlock>します。  
  
 **CultureOverride**:  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>場合にのみプロパティが使用される、<xref:System.Windows.Media.NumberSubstitution.CultureSource%2A>プロパティに設定されて<xref:System.Windows.Media.NumberCultureSource.Override>それ以外の場合は無視されます。 このプロパティは数字カルチャを指定します。 値`null`既定値は EN-US として解釈されます。  
  
 **Substitution**:  
  
 このプロパティは、実行する数字の置換の種類を指定します。 次のいずれかになります<xref:System.Windows.Media.NumberSubstitutionMethod>列挙値。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>:数字カルチャのに基づいて置換方法を決定<xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType>プロパティ。 既定値です。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>:数字カルチャがアラビアまたはペルシャのカルチャの場合は、数字がコンテキストに依存するを指定します。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.European>:数値は常に、ヨーロッパ数字としてレンダリングされます。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>:数字を表示する国の数字を使用して、カルチャの規定に従い、数字カルチャの<xref:System.Globalization.CultureInfo.NumberFormat%2A>します。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>:数字を表示するには、数字カルチャの通常の数字を使用します。 ほとんどのカルチャでは、これと同じ<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>します。 ただし、<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>この値が結果のすべてのアラビア カルチャでアラビア数字が一部のアラビア カルチャでラテンの数字になります。  
  
 これらの値は双方向コンテンツ開発者にとってどういった意味があるのでしょうか。 ほとんどの場合、開発者が定義にのみ必要があります<xref:System.Windows.FlowDirection>と各テキストの言語[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素、たとえば`Language="ar-SA"`と<xref:System.Windows.Media.NumberSubstitution>ロジックに従って、正しい番号を表示する処理[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 次の例で、アラビア語および英語の番号を使用して、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]のアラビア語版で実行されるアプリケーション[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]します。  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 次の図は、アラビア語および英語の番号が表示されるアラビア語のバージョンの Windows で実行している場合に、前のサンプルの出力を示します。

 ![アラビア語と英語数字を示しています。 グラフィック。](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 <xref:System.Windows.FlowDirection>設定はここでは重要な<xref:System.Windows.FlowDirection>に<xref:System.Windows.FlowDirection.LeftToRight>代わりに、ヨーロッパ数字が生成されます。 以下のセクションでは、ドキュメント全体で数字の表示を統一する方法について説明します。 この例では、アラビア語版 Windows で実行されていなければ、すべての数字がヨーロッパ数字として表示されます。  
  
 **置換ルールの定義**  
  
 実際のアプリケーションでは、プログラムでの言語設定が必要となる場合があります。 設定するなど、`xml:lang`システムで使用されるものと同じにする属性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、またはおそらくアプリケーション状態に応じて言語を変更します。  
  
 する場合は、アプリケーションの状態に基づいて、変更のによって提供されるその他の機能を使用して、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。  
  
 まず、設定して、アプリケーション コンポーネントの`NumberSubstitution.CultureSource="Text"`します。 設定がから提供されないことを確認は、この設定を使用して、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のテキスト要素など、既定値として"User"が含まれない<xref:System.Windows.Controls.TextBlock>します。  
  
例:  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

対応するC#コードは、設定、`Language`プロパティ、たとえば、 `"ar-SA"`。  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

設定する必要がある場合、`Language`プロパティに現在のユーザーの UI 言語は、次のコードを使用します。  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 実行時に現在のスレッドで使用される現在のカルチャを表します。  
  
 最終的な[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]例を次の例のようになります。  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 最終的なC#例は、次のようになります。  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 次の図は、何のいずれかのプログラミング言語をアラビア数字を表示するウィンドウの外観を示します。
     
 ![アラビア数字を表示するグラフィック。](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **Substitution プロパティの使用**  
  
 数字の置換動作[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]テキスト要素の両方の言語に依存し、その<xref:System.Windows.FlowDirection>します。 場合、<xref:System.Windows.FlowDirection>左から右、ヨーロッパ数字をレンダリングします。 ただしアラビア語のテキストが付いてまたは"ar"に言語を設定する場合、<xref:System.Windows.FlowDirection>は<xref:System.Windows.FlowDirection.RightToLeft>、アラビア数字が代わりに表示されます。  
  
 ただし、たとえば、すべてのユーザーに対してヨーロッパ数字を表示するなどの、統一されたアプリケーションを作成する必要がある場合もあります。 またはにアラビア数字<xref:System.Windows.Documents.Table>特定のセル<xref:System.Windows.Style>します。 1 つ簡単に行う方法を使用している、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>プロパティ。  
  
 次の例では、最初の<xref:System.Windows.Controls.TextBlock>はありません、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>プロパティの設定、期待どおりに、アルゴリズムにアラビア数字が表示されます。 ただし、2 番目の<xref:System.Windows.Controls.TextBlock>置換がヨーロッパに設定されてアラビア数字は、既定値の置換をオーバーライドして、ヨーロッパ数字が表示されます。  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
