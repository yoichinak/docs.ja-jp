---
title: WPF の双方向機能の概要
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 6cd16f4d5586dcee54152b430f14911f5a9c5682
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005128"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF の双方向機能の概要

他の開発プラットフォームとは異なり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、双方向のコンテンツの迅速な開発をサポートする多数の機能があります。たとえば、同じドキュメント内のデータを左から右へと右から左に混在させることができます。 同時に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、アラビア語やヘブライ語圏のユーザーなどの双方向の機能を必要とするユーザーに優れたエクスペリエンスを提供します。

以降のセクションでは、多数の双方向機能と双方向コンテンツを最適に表示した例について説明します。 ほとんどのサンプルでは XAML を使用しますが、または Microsoft C# Visual Basic コードに簡単に概念を適用できます。

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

@No__t 0 アプリケーションでコンテンツフローの方向を定義する基本プロパティは <xref:System.Windows.FrameworkElement.FlowDirection%2A> です。 このプロパティは、@no__t 0 または <xref:System.Windows.FlowDirection.RightToLeft> の2つの列挙値のいずれかに設定できます。 プロパティは、<xref:System.Windows.FrameworkElement> から継承されるすべての @no__t 0 要素で使用できます。

次の例では、<xref:System.Windows.Controls.TextBox> 要素のフロー方向を設定します。

**左から右へ記述するフロー方向**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**右から左へ記述するフロー方向**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

次の図は、前のコードがどのように表示されるのかを示します。

![さまざまなフロー方向を示すグラフィック。](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

@No__t 0 ツリー内の要素は、そのコンテナーから <xref:System.Windows.FrameworkElement.FlowDirection%2A> を継承します。 次の例では、<xref:System.Windows.Controls.TextBlock> は、<xref:System.Windows.Window> に存在する <xref:System.Windows.Controls.Grid> の内部にあります。 @No__t-1 の <xref:System.Windows.FrameworkElement.FlowDirection%2A> を設定すると、<xref:System.Windows.Controls.Grid> および @no__t にも設定されます。

次の例は <xref:System.Windows.FrameworkElement.FlowDirection%2A> の設定を示しています。

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

最上位レベル <xref:System.Windows.Window> は <xref:System.Windows.FlowDirection.RightToLeft> の @ no__t であるため、その中に含まれるすべての要素も同じ <xref:System.Windows.FrameworkElement.FlowDirection%2A> を継承します。 要素が指定された @no__t をオーバーライドするには、前の例の2番目の <xref:System.Windows.Controls.TextBlock> のように、<xref:System.Windows.FlowDirection.LeftToRight> に変更する明示的な方向の変更を追加する必要があります。 @No__t 0 が定義されていない場合は、既定の <xref:System.Windows.FlowDirection.LeftToRight> が適用されます。

次の図は、前の例の出力を示しています。

![明示的なフロー方向の変更を示すグラフィック。](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

HTML、@no__t 0、Java などの多くの開発プラットフォームでは、双方向のコンテンツ開発に特別なサポートを提供しています。 HTML などのマークアップ言語では、必要な方向にテキストを表示するために必要なマークアップがコンテンツライターに与えられます。たとえば、HTML 4.0 タグでは、"rtl" または "ltr" を値として受け取ります。 このタグは <xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティに似ていますが、<xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティは、テキストコンテンツをレイアウトするためのより高度な方法で動作し、テキスト以外のコンテンツに使用できます。

@No__t-0 の場合、<xref:System.Windows.Documents.FlowDocument> は、テキスト、テーブル、画像、およびその他の要素の組み合わせをホストできる汎用性のある [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素です。 以下のセクションのサンプルでは、この要素を使用します。

@No__t-0 にテキストを追加する方法は、1つの方法で行うことができます。 これを行う簡単な方法は、テキストなどのコンテンツをグループ化するために使用されるブロックレベルの要素である @no__t 0 を使用することです。 インラインレベルの要素にテキストを追加するには、サンプルで <xref:System.Windows.Documents.Span> および <xref:System.Windows.Documents.Run> を使用します。 <xref:System.Windows.Documents.Span> は、他のインライン要素をグループ化するために使用されるインラインレベルのフローコンテンツ要素です。 @no__t 1 は、書式設定されていないテキストの実行を格納するためのインラインレベルのフローコンテンツ要素です。 @No__t-0 には複数の <xref:System.Windows.Documents.Run> 要素を含めることができます。

最初のドキュメントの例には、多数のネットワーク共有名を持つドキュメントが含まれています。たとえば `\\server1\folder\file.ext` のようになります。 このネットワーク リンクがアラビア語または英語のいずれのドキュメントにあっても、常に同じように表示する必要があります。 次の図は、Span 要素の使用方法を示しています。このリンクは、アラビア @no__t 0 のドキュメントに記載されています。

![Span 要素の使用方法を示すグラフィック。](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

テキストは @no__t 0 であるため、"\\" などのすべての特殊文字は、右から左の順序でテキストを区切ります。 その結果、リンクが正しい順序で表示されなくなるため、問題を解決するには、別の @no__t 0 のフローを保持するためにテキストを埋め込む必要があります <xref:System.Windows.FlowDirection.LeftToRight>。 言語ごとに個別の <xref:System.Windows.Documents.Run> にするのではなく、よく使用される英語のテキストを、より大きなアラビア語の <xref:System.Windows.Documents.Span> に埋め込むことをお勧めします。

次の図は、Span 要素に埋め込まれた Run 要素を使用してこれを示しています。

![Span 要素に埋め込まれている Run 要素を示すグラフィック。](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

次の例では、ドキュメントで <xref:System.Windows.Documents.Run> および <xref:System.Windows.Documents.Span> 要素を使用する方法を示します。

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Span 要素

@No__t-0 要素は、フロー方向が異なるテキスト間の境界区切り記号として機能します。  同じフロー方向の @no__t 0 の要素でも、異なる双方向のスコープを持つと見なされます。つまり、<xref:System.Windows.Documents.Span> の要素がコンテナーの <xref:System.Windows.FlowDirection> で順序付けられていることを意味し、<xref:System.Windows.Documents.Span> 要素内のコンテンツのみがの @no__t の @no__ に従いt-5。

次の図は、複数の @no__t 0 要素のフロー方向を示しています。

![フロー方向が異なるテキストブロックを示すグラフィック。](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

次の例は、<xref:System.Windows.Documents.Span> と <xref:System.Windows.Documents.Run> の要素を使用して、前の図に示した結果を生成する方法を示しています。

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

このサンプルの @no__t 0 要素では、<xref:System.Windows.Documents.Span> 要素は親の <xref:System.Windows.FlowDirection> に従ってレイアウトされますが、各 <xref:System.Windows.Documents.Span> 要素内のテキストは、それぞれの @no__t に従ってフローします。 これは、ラテン語やアラビア語だけでなく、他のどの言語にも当てはまります。

### <a name="adding-xmllang"></a>xml:lang の追加

次の図は、数値と算術式 (`"200.0+21.4=221.4"` など) を使用する別の例を示しています。 @No__t-0 のみが設定されていることに注意してください。

![System.windows.flowdirection> のみを使用して数値を表示するグラフィック。](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

このアプリケーションのユーザーは、出力によってがっかりします。 @no__t 0 が正しい場合でも、数字はアラビア数字として整形されています。

XAML 要素には、各要素の言語を定義する @no__t 0 属性 (`xml:lang`) を含めることができます。 XAML では、ツリー内の親要素に適用される `xml:lang` の値が子要素によって使用される @no__t 0 言語の原則もサポートしています。 前の例では、<xref:System.Windows.Documents.Run> 要素または最上位レベルの要素に対して言語が定義されていなかったため、既定の `xml:lang` が使用されていました。これは、XAML では `en-US` です。 @No__t-0 の内部数値整形アルゴリズムでは、対応する言語 (この場合は英語) の数値が選択されます。 アラビア数字が正しく表示されるようにするには `xml:lang` を設定する必要があります。

次の図は @no__t 0 が追加された例を示しています。

![右から左に記述されるアラビア数字を示すグラフィック。](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

次の例では、アプリケーションに `xml:lang` を追加します。

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

多くの言語では、対象となる地域に応じて @no__t 0 の値が異なることに注意してください。たとえば、`"ar-SA"`、`"ar-EG"` はアラビア語の2つのバリエーションを表します。 前の例では、`xml:lang` と <xref:System.Windows.FlowDirection> の両方の値を定義する必要があることを示しています。

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>非テキスト要素のある FlowDirection

<xref:System.Windows.FlowDirection> は、テキスト要素内のテキストフローだけでなく、ほぼすべての他の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素のフロー方向も定義します。 次の図は、水平方向の <xref:System.Windows.Media.LinearGradientBrush> を使用して、左から右へのグラデーションで背景を描画する @no__t 0 を示しています。

![左から右へのグラデーションが表示されたツールバーを示すグラフィック。](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

@No__t-0 を <xref:System.Windows.FlowDirection.RightToLeft> に設定すると、<xref:System.Windows.Controls.ToolBar> のボタンだけが右から左に配置されます。ただし、<xref:System.Windows.Media.LinearGradientBrush> では、右から左にフローするようにオフセットを調整します。

次の図は <xref:System.Windows.Media.LinearGradientBrush> の再調整を示しています。

![右から左にグラデーションが表示されたツールバーを示すグラフィック。](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

次の例では、@no__t 0 の @ no__t-1 を描画します。 (左から右に描画するには、<xref:System.Windows.Controls.ToolBar> の <xref:System.Windows.FlowDirection> 属性を削除します。

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>FlowDirection の例外

@No__t-0 が想定どおりに動作しないケースがいくつかあります。 ここでは、そのような例外を 2 つ取り上げて説明します。

**[イメージ]**

@No__t-0 は、イメージを表示するコントロールを表します。 XAML では、表示する <xref:System.Windows.Controls.Image> の @no__t を定義する @no__t 0 プロパティと共に使用できます。

他の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素とは異なり、<xref:System.Windows.Controls.Image> はコンテナーから <xref:System.Windows.FlowDirection> を継承しません。 ただし、@no__t 0 が明示的に <xref:System.Windows.FlowDirection.RightToLeft> に設定されている場合、@no__t 2 が水平方向に反転して表示されます。 これは、双方向コンテンツの開発者にとって便利な機能として実装されています。場合によっては、イメージを左右反転して表示することで必要な効果が得られるためです。

次の図は、<xref:System.Windows.Controls.Image> の反転を示しています。

![反転された画像を示す図。](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

次の例では、<xref:System.Windows.Controls.Image> は、それを含む <xref:System.Windows.Controls.StackPanel> から <xref:System.Windows.FlowDirection> を継承できません。

> [!NOTE]
> C:\ に ms_logo という名前のファイルが必要**です。** この例を実行するドライブです。

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> ダウンロードファイルには、 **ms_logo**ファイルが含まれています。 コードは、この .jpg ファイルがプロジェクト内ではなく、C:\ ドライブ上にあることを前提としています。 プロジェクト内のファイルを検索するためには、プロジェクト ファイルから C:\ドライブに .jpg をコピーするかコードを変更する必要があります。 この変更を行うには、-0 を `Source="ms_logo.jpg"` に @no__t ます。

**パス**

@No__t-0 に加えて、もう1つの興味深い要素は <xref:System.Windows.Shapes.Path> です。 パスは、接続された一連の線と曲線を描画できるオブジェクトです。 これは、その @no__t に関する @no__t 0 と同様の方法で動作します。たとえば、<xref:System.Windows.FlowDirection.RightToLeft> @ no__t は <xref:System.Windows.FlowDirection.LeftToRight> 1 の水平方向のミラーです。 ただし、<xref:System.Windows.Controls.Image> とは異なり、<xref:System.Windows.Shapes.Path> はコンテナーからその @no__t を継承し、1つを明示的に指定する必要はありません。

次の例では、3 本の線を使用して単純な矢印を描画します。 最初の矢印は、始点と終点が右側のルートから測定されるように、<xref:System.Windows.Controls.StackPanel> からの @no__t 0 のフロー方向を継承します。 2番目の矢印は、明示的な <xref:System.Windows.FlowDirection.RightToLeft> @ no__t-1 も右側で開始します。 ただし、3 番目の矢印の起点は左側です。 描画の詳細については、「<xref:System.Windows.Media.LineGeometry>」と「<xref:System.Windows.Media.GeometryGroup>」を参照してください。

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

次の図は、`Path` 要素を使用して描画された矢印を持つ前の例の出力を示しています。

![Path 要素を使用して描画された矢印を示すグラフィック。](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

@No__t-0 と <xref:System.Windows.Shapes.Path> は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が <xref:System.Windows.FlowDirection> を使用する方法の2つの例です。 コンテナー内の特定の方向に [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素をレイアウトする場合、<xref:System.Windows.FlowDirection> は、画面にインク @no__t @no__t をレンダリングする <xref:System.Windows.Controls.InkPresenter> などの要素で使用できます。 左から右への動作を模倣するコンテンツに対して右から左の動作が必要な場合、またはその逆の場合は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] によってこの機能が提供されます。

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>数字の置換

従来、Windows では数字の置換がサポートされています。これにより、さまざまなカルチャを同じ数字で表現できるようになり、数字の内部ストレージを異なるロケール間で統合できるようになりました。たとえば、数値はよく知られている16進値0x40、0x41。ただし、選択した言語に従って表示されます。

これにより、アプリケーションで数値を処理できるようになりましたが、1つの言語から別の言語に変換する必要はありません。たとえば、ローカライズされたアラビア語ウィンドウでは @no__t 0 のスプレッドシートを開き、アラビア語では数値を表示できますが、ヨーロッパでは開くことができます。Windows のバージョンと、同じ数値の欧州表現を参照してください。 これは、コンマ区切りやパーセント記号などの他の記号でも必要です。これらの記号は、通常同じドキュメント内で数字を伴っているからです。

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は引き続きこの機能を備え、置換を使用するタイミングと方法をユーザーがさらに制御できるようにこの機能のサポートが強化されています。 この機能はすべての言語向けに設計されていますが、アプリケーションが実行される可能性のあるカルチャが多岐にわたるために特定の言語に合わせて数字の形状を設定することがアプリケーション開発者にとって通常は問題となる双方向コンテンツに対して特に有用です。

@No__t-0 での数値置換の動作を制御するコアプロパティは、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A> の依存関係プロパティです。 @No__t-0 クラスは、テキスト内の数字を表示する方法を指定します。 その動作を定義する 3 つのパブリック プロパティがあります。 各プロパティの概要を次に示します。

**CultureSource:**

このプロパティは、数字のカルチャを決定する方法を指定します。 これは、3つの @no__t 0 列挙値のいずれかをとります。

- オーバーライド数値カルチャは @no__t 0 のプロパティの値です。

- 本文数値カルチャは、テキストランのカルチャです。 マークアップでは、これは `xml:lang` またはそのエイリアス `Language` プロパティ (<xref:System.Windows.FrameworkElement.Language%2A> または <xref:System.Windows.FrameworkContentElement.Language%2A>) になります。 また、<xref:System.Windows.FrameworkContentElement> から派生するクラスの既定値です。 このようなクラスには、<xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>、<xref:System.Windows.Documents.Table?displayProperty=nameWithType>、<xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> などがあります。

- ユーザー:数値カルチャは、現在のスレッドのカルチャです。 このプロパティは、<xref:System.Windows.Controls.Page>、<xref:System.Windows.Window>、<xref:System.Windows.Controls.TextBlock> などの @no__t 0 のすべてのサブクラスの既定値です。

**CultureOverride**:

@No__t-0 プロパティは、<xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> プロパティが <xref:System.Windows.Media.NumberCultureSource.Override> に設定されている場合にのみ使用され、それ以外の場合は無視されます。 このプロパティは数字カルチャを指定します。 値 `null` (既定値) は en-us として解釈されます。

**Substitution**:

このプロパティは、実行する数字の置換の種類を指定します。 次のいずれかの <xref:System.Windows.Media.NumberSubstitutionMethod> 列挙値を取得します。

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>:置換メソッドは、数値カルチャの @no__t 0 プロパティに基づいて決定されます。 既定値です。

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>:数字カルチャがアラビア語またはペルシャ語のカルチャである場合は、数字がコンテキストに依存することを指定します。

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>:数値は常にヨーロッパの数字としてレンダリングされます。

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>:数字は、カルチャの <xref:System.Globalization.CultureInfo.NumberFormat%2A> によって指定された、数字カルチャの national 数字を使用してレンダリングされます。

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>:数値は、数字カルチャに対して従来の数字を使用してレンダリングされます。 ほとんどのカルチャでは、これは <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> と同じです。 ただし、<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> の場合、一部のアラビアカルチャではラテン数字が使用されますが、この値はすべてのアラビアカルチャでアラビア数字になります。

これらの値は双方向コンテンツ開発者にとってどういった意味があるのでしょうか。 ほとんどの場合、開発者は <xref:System.Windows.FlowDirection> と各テキスト [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素の言語 (たとえば `Language="ar-SA"`) を定義するだけで済みます。また、@no__t 3 ロジックは、正しい @no__t に従って数値を表示します。 次の例では、アラビア語版の Windows で実行されている @no__t 0 アプリケーションでアラビア数字と英語番号を使用する方法を示します。

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

アラビア語と英語の数字が表示されたアラビア語版の Windows で実行している場合は、前の例の出力を次の図に示します。

![アラビア数字と英語番号を示すグラフィック。](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

この場合、<xref:System.Windows.FlowDirection> が重要でした。これは、代わりに <xref:System.Windows.FlowDirection> を <xref:System.Windows.FlowDirection.LeftToRight> に設定すると、ヨーロッパの数字が生成されるためです。 以下のセクションでは、ドキュメント全体で数字の表示を統一する方法について説明します。 この例では、アラビア語版 Windows で実行されていなければ、すべての数字がヨーロッパ数字として表示されます。

**置換ルールの定義**

実際のアプリケーションでは、プログラムでの言語設定が必要となる場合があります。 たとえば、`xml:lang` 属性を、システムの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] で使用されている属性と同じになるように設定したり、アプリケーションの状態に応じて言語を変更したりすることができます。

アプリケーションの状態に基づいて変更を行う場合は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] によって提供される他の機能を使用してください。

最初に、アプリケーションコンポーネントの @no__t を0に設定します。 この設定を使用すると、既定値として "User" を持つテキスト要素 (<xref:System.Windows.Controls.TextBlock> など) の設定が [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] から取得されないようにします。

以下に例を示します。

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

対応C#するコードで、たとえば、`Language` プロパティを `"ar-SA"` に設定します。

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

@No__t-0 プロパティを現在のユーザーの UI 言語に設定する必要がある場合は、次のコードを使用します。

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> は、実行時に現在のスレッドによって使用されている現在のカルチャを表します。

最終的な XAML の例は、次の例のようになります。

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

最後C#の例は次のようになります。

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

次の図は、いずれかのプログラミング言語でのウィンドウの外観を示しています。アラビア数字が表示されています。

![アラビア数字を表示するグラフィック。](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**Substitution プロパティの使用**

@No__t-0 での数値置換の動作は、テキスト要素の言語とその <xref:System.Windows.FlowDirection> の両方によって異なります。 @No__t-0 が左から右にある場合は、ヨーロッパの数字が表示されます。 ただし、その前にアラビア語のテキストが付いている場合、または言語が "ar" に設定されており、<xref:System.Windows.FlowDirection> が <xref:System.Windows.FlowDirection.RightToLeft> の場合は、代わりにアラビア数字が表示されます。

ただし、たとえば、すべてのユーザーに対してヨーロッパ数字を表示するなどの、統一されたアプリケーションを作成する必要がある場合もあります。 特定の <xref:System.Windows.Style> を持つ @no__t 0 のセルでは、アラビア数字が使用されます。 これを行う簡単な方法の1つは、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A> プロパティを使用することです。

次の例では、最初の <xref:System.Windows.Controls.TextBlock> には <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> プロパティが設定されていないため、アルゴリズムではアラビア数字が想定どおりに表示されます。 ただし、2番目の <xref:System.Windows.Controls.TextBlock> の場合、置換はヨーロッパに設定され、アラビア数字の既定の置換が上書きされ、ヨーロッパの数字が表示されます。

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
