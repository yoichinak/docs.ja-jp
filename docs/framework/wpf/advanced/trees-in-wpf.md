---
title: WPF のツリー
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: 1b1763f2fcad60da757a3d6ff23dc289e7506ead
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966091"
---
# <a name="trees-in-wpf"></a>WPF のツリー
多くのテクノロジでは、要素とコンポーネントはツリー構造で構成されており、開発者はツリー内のオブジェクトノードを直接操作して、アプリケーションのレンダリングや動作に影響を与えます。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]では、プログラム要素間の関係を定義するために、いくつかのツリー構造のメタファが使用されます。 ほとんどの場合、WPF 開発者は、オブジェクトツリーの比喩について概念的に考えると同時に、コードでアプリケーションを作成したり、アプリケーションの一部を XAML で定義したりできますが、特定の API を呼び出すか、特定のマークアップを使用して汎用的なものではありません。などのオブジェクトツリー操作 API は、XML DOM でを使用する場合があります。 WPF は、 <xref:System.Windows.LogicalTreeHelper>ツリーの比喩ビューと<xref:System.Windows.Media.VisualTreeHelper>を提供する2つのヘルパークラスを公開します。 これらの同じツリーが特定の主要な WPF 機能の動作を理解するのに役立ちます。そのため、ビジュアルツリーと論理ツリーは WPF ドキュメントでも使用されます。 このトピックでは、ビジュアルツリーと論理ツリーが表す内容を定義し、そのようなツリーがオブジェクトツリー全体の<xref:System.Windows.LogicalTreeHelper>概念<xref:System.Windows.Media.VisualTreeHelper>にどのように関連しているかを説明します。およびは、とを紹介します。  

<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>WPF のツリー  
 の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]最も完全なツリー構造は、オブジェクトツリーです。 で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アプリケーションページを定義し、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を読み込むと、マークアップ内の要素の入れ子の関係に基づいてツリー構造が作成されます。 アプリケーションまたはアプリケーションの一部をコードで定義した場合、特定のオブジェクトのコンテンツモデルを実装するプロパティのプロパティ値の割り当て方法に基づいて、ツリー構造が作成されます。 で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、完全なオブジェクトツリーが概念化され、そのパブリック API (論理ツリーとして、およびビジュアルツリー) にレポートできる方法が2つあります。 論理ツリーとビジュアルツリーの違いは必ずしも重要であるとは限りませんが、特定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のサブシステムで問題が発生し、マークアップまたはコードで行った選択に影響することがあります。  
  
 論理ツリーまたはビジュアルツリーを直接操作しているわけではありませんが、ツリーの相互作用の概念を理解することは、WPF をテクノロジとして理解するうえで役に立ちます。 WPF は、いくつかの種類のツリーの比喩と考えることも重要です。これは、での[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティの継承とイベントルーティングのしくみを理解する上で重要です。  
  
> [!NOTE]
> オブジェクトツリーは実際の API よりも概念が多いため、概念を考えるもう1つの方法はオブジェクトグラフです。 実際には、ツリーの比喩が分割される、実行時のオブジェクト間のリレーションシップがあります。 それにもかかわらず、特に XAML で定義された UI の場合、ツリーの比喩は、この一般的な概念を参照するときにほとんどの WPF ドキュメントがオブジェクトツリーという用語を使用することに関係しています。  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>論理ツリー  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、これらの要素を返すオブジェクトのプロパティを設定することによって、UI 要素にコンテンツを追加します。 たとえば、 <xref:System.Windows.Controls.ListBox>コントロールに項目を追加するには、その<xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティを操作します。 これにより、 <xref:System.Windows.Controls.ItemCollection> <xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティ値であるに項目を配置します。 同様に、オブジェクト<xref:System.Windows.Controls.DockPanel>をに追加するには、 <xref:System.Windows.Controls.Panel.Children%2A>プロパティ値を操作します。 ここでは、 <xref:System.Windows.Controls.UIElementCollection>にオブジェクトを追加します。 コード例については[、「方法:要素を動的](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms752374(v=vs.100))に追加します。  
  
 で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Controls.ListBox>は、またはのコントロールまたは<xref:System.Windows.Controls.DockPanel>その他の UI 要素にリスト項目を配置するときに<xref:System.Windows.Controls.ItemsControl.Items%2A> 、次の例のように、明示的または暗黙的にプロパティと<xref:System.Windows.Controls.Panel.Children%2A>プロパティも使用します。  
  
 [!code-xaml[TreeOvwsSupport#AllCode](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 この XAML をドキュメントオブジェクトモデルの下で XML として処理していて、タグを暗黙的に (有効な場合は) 除外すると、結果の XML DOM ツリーにとその他の暗黙的な`<ListBox.Items>`項目の要素が含まれるようになります。 ただし、XAML では、マークアップを読み取り、オブジェクトに書き込むときに、このような処理は行われませ`ListBox.Items`ん。結果として得られるオブジェクトグラフには、が含まれません。 ただし<xref:System.Windows.Controls.ListBox> 、を<xref:System.Windows.Controls.ListBox>含むと<xref:System.Windows.Controls.ItemCollection>いう名前`Items`のプロパティがあります。このプロパティは、XAMLの処理時に初期化されますが、空になります。<xref:System.Windows.Controls.ItemCollection> 次に、のコンテンツ<xref:System.Windows.Controls.ListBox>として存在する各子オブジェクト要素が、パーサーに<xref:System.Windows.Controls.ItemCollection>よるへ`ItemCollection.Add`の呼び出しによってに追加されます。 このように、XAML をオブジェクトツリーに処理する例では、作成されたオブジェクトツリーが基本的に論理ツリーであるという一見のように見えます。  
  
 ただし、論理ツリーは、XAML の暗黙的な構文項目が考慮されていない場合でも、実行時にアプリケーション UI に存在するオブジェクトグラフ全体ではありません。主な理由は、ビジュアルとテンプレートです。 たとえば、を考えて<xref:System.Windows.Controls.Button>みます。 論理ツリーは、 <xref:System.Windows.Controls.Button>オブジェクトとその文字列`Content`も報告します。 ただし、実行時のオブジェクトツリーには、このボタンが追加されています。 特に、特定<xref:System.Windows.Controls.Button>のコントロールテンプレートが適用されたため、ボタンは画面に表示されるだけです。 実行時に論理ツリーを表示している場合でも、適用<xref:System.Windows.Controls.Border>されたテンプレート (ビジュアルボタンの周囲に濃い灰色のテンプレート定義など) から取得したビジュアルは、論理ツリーでは報告されません。表示されている UI を参照し、次に論理ツリーを読み取ります)。 テンプレートビジュアルを検索するには、代わりにビジュアルツリーを調べる必要があります。  
  
 構文と、作成されたオブジェクトグラフ、および xaml の暗黙的な構文の対応については、「 [xaml 構文の詳細](xaml-syntax-in-detail.md)」または「 [xaml の概要 (WPF)](xaml-overview-wpf.md)」を参照してください。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>論理ツリーの目的  
 論理ツリーは、コンテンツモデルが可能な子オブジェクトを簡単に反復処理できるようにし、コンテンツモデルを拡張できるようにするためのものです。 また、論理ツリーは、論理ツリー内のすべてのオブジェクトが読み込まれるときなど、特定の通知のためのフレームワークを提供します。 基本的に、論理ツリーは、フレームワークレベルでの実行時のオブジェクトグラフの近似値です。ビジュアルは除外されますが、独自の実行時アプリケーションの構成に対する多くのクエリ操作には適しています。  
  
 さらに、静的リソース参照と動的リソース参照の両方が解決されます。その<xref:System.Windows.FrameworkElement.Resources%2A>ためには、最初に要求しているオブジェクトのコレクションの論理ツリーを<xref:System.Windows.FrameworkElement>上方向に検索し、次に論理ツリーを続行し、それぞれのチェックボックスをオンにします (または、<xref:System.Windows.FrameworkContentElement>)`Resources` が<xref:System.Windows.ResourceDictionary>含まれている別の値 (そのキーを含む可能性があります)。 論理ツリーは、論理ツリーとビジュアルツリーの両方が存在する場合に、リソース検索に使用されます。 リソースディクショナリと参照の詳細については、「 [XAML リソース](xaml-resources.md)」を参照してください。  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>論理ツリーの構成  
 論理ツリーは、wpf フレームワークレベルで定義されます。これは、論理ツリー操作に最も関連する wpf ベース要素がまたは<xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>のいずれかであることを意味します。 ただし、実際に<xref:System.Windows.LogicalTreeHelper> API を使用しているかどうかを確認できるので、論理ツリーに<xref:System.Windows.FrameworkElement>はまた<xref:System.Windows.FrameworkContentElement>はではないノードが含まれる場合があります。 たとえば、論理ツリーは、文字列で<xref:System.Windows.Controls.TextBlock.Text%2A>ある<xref:System.Windows.Controls.TextBlock>の値を報告します。  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>論理ツリーの上書き  
 高度なコントロールの作成者は、一般的なオブジェクトまたはコンテンツモデルが論理ツリー内のオブジェクトを追加または削除する方法を定義するいくつかの Api をオーバーライドすることにより、論理ツリーをオーバーライドできます。 論理ツリーを上書きする方法の例については、「[論理ツリーの上書き](how-to-override-the-logical-tree.md)」を参照してください。  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>プロパティ値の継承  
 プロパティ値の継承は、ハイブリッドツリーを介して動作します。 プロパティの<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>継承を有効にするプロパティを含む実際のメタデータは、WPF <xref:System.Windows.FrameworkPropertyMetadata>フレームワークレベルのクラスです。 したがって、元の値を保持する親と、その値を継承する子オブジェクトの両方<xref:System.Windows.FrameworkElement>が<xref:System.Windows.FrameworkContentElement>またはである必要があり、両方とも論理ツリーの一部である必要があります。 ただし、プロパティの継承をサポートする既存の WPF プロパティについては、プロパティ値の継承は、論理ツリーに存在しない介在するオブジェクトを介して perpetuate できます。 これは主に、テンプレート要素で、テンプレート化されたインスタンスで設定されている継承されたプロパティ値を使用する場合、またはより高いレベルのページレベルの構成で、論理ツリー内で上位に設定する場合に関連します。 プロパティ値の継承をこのような境界を越えて一貫して機能させるには、継承プロパティを添付プロパティとして登録する必要があります。また、プロパティを使用してカスタム依存関係プロパティを定義する場合は、このパターンに従う必要があります。継承動作。 プロパティの継承に使用される正確なツリーは、実行時でも、ヘルパークラスのユーティリティメソッドで完全には期待できません。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>ビジュアルツリー  
 論理ツリーの概念に加えて、のビジュアルツリー [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の概念もあります。 ビジュアルツリーには、 <xref:System.Windows.Media.Visual>基本クラスによって表されるビジュアルオブジェクトの構造が記述されています。 コントロールのテンプレートを作成するときは、そのコントロールに適用されるビジュアルツリーを定義または再定義します。 ビジュアルツリーは、パフォーマンスと最適化の理由により、描画を低レベルで制御する開発者にとっても重要です。 従来[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のアプリケーションプログラミングの一部としてビジュアルツリーが公開されると、ルーティングイベントのイベントルートは、論理ツリーではなく、ほとんどの場合、ビジュアルツリーに沿って移動します。 このはらみのルーティングイベントの動作は、コントロールの作成者でない限り、すぐには表示されない場合があります。 ビジュアルツリーを介してイベントをルーティングすると、ビジュアルレベルでコンポジションを実装するコントロールによって、イベントを処理したり、イベントセッターを作成したりできます。  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>ツリー、コンテンツ要素、およびコンテンツホスト  
 コンテンツ要素 (から<xref:System.Windows.ContentElement>派生するクラス) は、ビジュアルツリーの一部ではなく、から<xref:System.Windows.Media.Visual>継承されず、ビジュアル表現もありません。 を UI <xref:System.Windows.ContentElement>に表示するには、を、論理ツリーの参加要素であるコンテンツホスト<xref:System.Windows.Media.Visual>でホストする必要があります。 通常、このようなオブジェクト<xref:System.Windows.FrameworkElement>はです。 コンテンツホストがコンテンツの "ブラウザー" のようなものであり、ホストが制御する画面領域内にそのコンテンツを表示する方法を選択するという概念があります。 コンテンツがホストされている場合、ビジュアルツリーに通常関連付けられている特定のツリープロセスでコンテンツを参加させることができます。 通常、host <xref:System.Windows.FrameworkElement>クラスには、ホストされている<xref:System.Windows.ContentElement>コンテンツが true ビジュアルツリーの一部ではない場合でも、コンテンツ論理ツリーのサブノードを介して、イベントルートにホストされるを追加する実装コードが含まれます。 これは、 <xref:System.Windows.ContentElement>がそれ自体以外の任意の要素にルーティングするルーティングイベントをソースに送信できるようにするために必要です。  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>ツリートラバーサル  
 クラス<xref:System.Windows.LogicalTreeHelper>には、論理<xref:System.Windows.LogicalTreeHelper.GetParent%2A>ツリートラ<xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A>バーサルの、、およびの各メソッドが<xref:System.Windows.LogicalTreeHelper.GetChildren%2A>用意されています。 ほとんどの場合、既存のコントロールの論理ツリーを走査する必要はありません。これらのコントロールは`Add`、論理上の子要素を、インデクサーなどのコレクションアクセスをサポートする専用のコレクションプロパティとして常に公開するからです。などなど。 ツリートラバーサルは、主に、、コレクションプロパティが既に定義されて<xref:System.Windows.Controls.ItemsControl>いる、または<xref:System.Windows.Controls.Panel>独自のコレクションを提供する予定のコントロールパターンから派生しないことを選択するコントロールの作成者によって使用されるシナリオです。プロパティのサポート。  
  
 ビジュアルツリーでは、 <xref:System.Windows.Media.VisualTreeHelper>ビジュアルツリートラバーサルのヘルパークラスもサポートされています。 ビジュアルツリーは、コントロール固有のプロパティによって簡単に公開され<xref:System.Windows.Media.VisualTreeHelper>ないため、プログラミングシナリオに必要な場合は、ビジュアルツリーを走査するためにクラスを使用することをお勧めします。 詳しくは、「[WPF グラフィックス レンダリングの概要](../graphics-multimedia/wpf-graphics-rendering-overview.md)」をご覧ください。  
  
> [!NOTE]
> 適用されているテンプレートのビジュアルツリーを調べることが必要になる場合があります。 この手法を使用する場合は注意が必要です。 テンプレートを定義するコントロールのビジュアルツリーを走査している場合でも、コントロールのコンシューマーはインスタンスの<xref:System.Windows.Controls.Control.Template%2A>プロパティを設定することによっていつでもテンプレートを変更できます。また、エンドユーザーは、適用されるテンプレートにシステムテーマ。  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>"ツリー" としてのルーティングイベントのルート  
 前述のように、特定のルーティングイベントのルートは、ビジュアルおよび論理ツリー表現をハイブリッドにした、ツリーの1つの事前に定義されたパスに沿って移動します。 イベントルートは、ルーティングイベントとバブルルーティングイベントのどちらであるかに応じて、ツリー内の上下方向に移動できます。 イベントルートの概念には、実際にルーティングするイベントを発生させずにイベントルートを "ウォーク" するために使用できるヘルパークラスが直接サポートされていません。 ルート<xref:System.Windows.EventRoute>を表すクラスがありますが、そのクラスのメソッドは一般に内部でのみ使用されます。  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>リソースディクショナリとツリー  
 ページで定義され`Resources`ているすべてのリソースディクショナリの参照は、基本的に論理ツリーになります。 論理ツリーに含まれていないオブジェクトは、キー付きリソースを参照できますが、リソース参照シーケンスは、そのオブジェクトが論理ツリーに接続されているポイントから開始されます。 WPF では、論理ツリーノードだけがを`Resources` <xref:System.Windows.ResourceDictionary>含むプロパティを持つことができるため、ビジュアルツリーを走査してからキー付きリソース<xref:System.Windows.ResourceDictionary>を検索する利点はありません。  
  
 ただし、リソースルックアップは、直接の論理ツリーの範囲を超えて拡張することもできます。 アプリケーションマークアップの場合、リソースルックアップは、アプリケーションレベルのリソースディクショナリに続き、次に、静的なプロパティまたはキーとして参照されるテーマサポートとシステム値に進みます。 また、リソース参照が動的である場合は、テーマの論理ツリーの外側のシステム値を参照することもできます。 リソースディクショナリと参照ロジックの詳細については、「 [XAML Resources](xaml-resources.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [入力の概要](input-overview.md)
- [WPF グラフィックス レンダリングの概要](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [ルーティング イベントの概要](routed-events-overview.md)
- [オブジェクト ツリーに存在しないオブジェクト要素の初期化](initialization-for-object-elements-not-in-an-object-tree.md)
- [WPF アーキテクチャ](wpf-architecture.md)
