---
title: ツリー
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: 696772da1ebee405493f2ff0e1481daf93d08ec7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187020"
---
# <a name="trees-in-wpf"></a>WPF のツリー
多くのテクノロジでは、要素とコンポーネントはツリー構造に編成されており、開発者はツリー内のオブジェクト ノードを直接操作してアプリケーションのレンダリングや動作に影響を与えます。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]また、複数のツリー構造メタファを使用して、プログラム要素間の関係を定義します。 ほとんどの場合、WPF 開発者は、オブジェクト ツリーのメタファーについて概念的に考えながら、コードでアプリケーションを作成したり、XAML でアプリケーションの一部を定義したりできますが、一般的な API ではなく、特定の API を呼び出すか、特定のマークアップを使用します。XML DOM で使用するオブジェクト ツリー操作 API などです。 WPF は、ツリー メタファ ビューを提供する<xref:System.Windows.LogicalTreeHelper> <xref:System.Windows.Media.VisualTreeHelper>2 つのヘルパー クラスと を公開します。 ビジュアル ツリーと論理ツリーという用語は、WPF のドキュメントでも使用されています。 このトピックでは、ビジュアル ツリーと論理ツリーが表す内容、このようなツリーとオブジェクト ツリー全体の概念と<xref:System.Windows.LogicalTreeHelper>の<xref:System.Windows.Media.VisualTreeHelper>関係、および導入と s について定義します。  

<a name="element_tree"></a>
## <a name="trees-in-wpf"></a>WPF のツリー  
 最も完全なツリー構造[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]はオブジェクトツリーです。 でアプリケーション ページを定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]し、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を読み込むと、マークアップ内の要素の入れ子関係に基づいてツリー構造が作成されます。 アプリケーションまたはアプリケーションの一部をコードで定義する場合、特定のオブジェクトのコンテンツ モデルを実装するプロパティのプロパティ値を割り当てる方法に基づいてツリー構造が作成されます。 では[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、完全なオブジェクト ツリーを概念化し、そのパブリック API に報告する方法として、論理ツリーとビジュアル ツリーの 2 つがあります。 論理ツリーとビジュアル ツリーの区別は必ずしも重要ではありませんが、特定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のサブシステムで問題が発生し、マークアップやコードで行う選択に影響を与えることがあります。  
  
 論理ツリーまたはビジュアル ツリーを直接操作する必要はなくても、ツリーの相互作用の概念を理解することは、WPF をテクノロジとして理解するのに役立ちます。 WPF をある種のツリー メタファとして考えることは、 プロパティ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の継承とイベント ルーティングのしくみを理解するうえでも重要です。  
  
> [!NOTE]
> オブジェクト ツリーは実際の API よりも概念のほうが多いため、この概念を考えるもう 1 つの方法はオブジェクト グラフです。 実際には、実行時にツリーのメタファーが分解されるオブジェクト間の関係があります。 ただし、特に XAML で定義された UI では、ツリーメタファは、ほとんどの WPF ドキュメントがこの一般的な概念を参照するときにオブジェクト ツリーという用語を使用するほどの関連性があります。  
  
<a name="logical_tree"></a>
## <a name="the-logical-tree"></a>論理ツリー  
 では[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、それらの要素をバックするオブジェクトのプロパティを設定することで、UI 要素にコンテンツを追加します。 たとえば、コントロールのプロパティを<xref:System.Windows.Controls.ListBox>操作して、コントロールに<xref:System.Windows.Controls.ItemsControl.Items%2A>項目を追加します。 これにより、プロパティ値<xref:System.Windows.Controls.ItemCollection>であるに項目を<xref:System.Windows.Controls.ItemsControl.Items%2A>配置します。 同様に、<xref:System.Windows.Controls.DockPanel>にオブジェクトを追加するには、その<xref:System.Windows.Controls.Panel.Children%2A>プロパティ値を操作します。 ここでは、オブジェクトを に追加します<xref:System.Windows.Controls.UIElementCollection>。 コード例については、「[方法 : 動的に要素を追加する 」](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms752374(v=vs.100))を参照してください。  
  
 では[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、 または コントロールまたはその他の<xref:System.Windows.Controls.ListBox>UI 要素に<xref:System.Windows.Controls.DockPanel>リスト項目を配置する場合、次<xref:System.Windows.Controls.ItemsControl.Items%2A>の<xref:System.Windows.Controls.Panel.Children%2A>例のように、 プロパティと プロパティを明示的または暗黙的に使用します。  
  
 [!code-xaml[TreeOvwsSupport#AllCode](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 この XAML をドキュメント オブジェクト モデルの下で XML として処理し、コメント アウトされたタグを暗黙的 (これは合法) として含めていた場合、結果の XML DOM`<ListBox.Items>`ツリーには、その他の暗黙的な項目の要素が含まれます。 しかし、XAML は、マークアップを読み取ってオブジェクトに書き込むときにそのように処理しません`ListBox.Items`。 ただし、XAML が<xref:System.Windows.Controls.ListBox>処理されるときに`Items`は初期化<xref:System.Windows.Controls.ItemCollection><xref:System.Windows.Controls.ItemCollection>されますが、空であるを含むという名前の<xref:System.Windows.Controls.ListBox>プロパティがあります。 次に、 のコンテンツとして存在する各子オブジェクト<xref:System.Windows.Controls.ListBox>要素が、<xref:System.Windows.Controls.ItemCollection>パーサー呼び出`ItemCollection.Add`しに追加されます。 オブジェクト ツリーに XAML を処理するこの例は、作成されたオブジェクト ツリーが基本的に論理ツリーである例です。  
  
 ただし、論理ツリーは、XAML の暗黙的な構文項目が因数化されていても、実行時にアプリケーション UI に存在するオブジェクト グラフ全体ではありません。その主な理由は、ビジュアルとテンプレートです。 たとえば、 を考<xref:System.Windows.Controls.Button>えてみます。 論理ツリーはオブジェクト<xref:System.Windows.Controls.Button>とその文字列`Content`を報告します。 しかし、このボタンには、実行時オブジェクトツリーにはさらに多くのボタンがあります。 特に、特定<xref:System.Windows.Controls.Button>のコントロール テンプレートが適用されたため、ボタンは画面に表示されます。 適用されたテンプレート (ビジュアル ボタンの周囲のダーク グレーのテンプレート<xref:System.Windows.Controls.Border>で定義されたテンプレートなど) から取得されたビジュアルは、実行時に論理ツリーを見ている場合でも (表示される UI からの入力イベントの処理や論理ツリーの読み取りなど)、論理ツリーには報告されません。 テンプレート ビジュアルを見つけるには、代わりにビジュアル ツリーを調べる必要があります。  
  
 作成されたオブジェクト グラフ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]に構文をマップする方法と XAML の暗黙的な構文の詳細については[、「XAML 構文の詳細](xaml-syntax-in-detail.md)」または[「XAML の概要 (WPF)」](xaml-overview-wpf.md)を参照してください。  
  
<a name="tree_property_inheritance_event_routing"></a>
### <a name="the-purpose-of-the-logical-tree"></a>論理ツリーの目的  
 論理ツリーは、コンテンツ モデルが子オブジェクトを簡単に反復処理できるように存在し、コンテンツ モデルを拡張できるようにします。 また、論理ツリーは、論理ツリー内のすべてのオブジェクトがロードされる場合など、特定の通知のフレームワークを提供します。 基本的に、論理ツリーはフレームワーク レベルでのランタイム オブジェクト グラフの概算であり、ビジュアルは除外されますが、独自のランタイム アプリケーションの構成に対する多くのクエリ操作には適切です。  
  
 さらに、静的リソース参照と動的リソース参照の両方が、最初の要求オブジェクトのコレクションの<xref:System.Windows.FrameworkElement.Resources%2A>論理ツリーを上方に見て、論理ツリーを上に移動して、その<xref:System.Windows.FrameworkElement>キーを<xref:System.Windows.FrameworkContentElement>含む別`Resources`の<xref:System.Windows.ResourceDictionary>値をそれぞれ (または) にチェックすることで解決されます。 論理ツリーは、論理ツリーとビジュアル ツリーの両方が存在する場合に、リソースルックアップに使用されます。 リソース ディクショナリと検索の詳細については[、「XAML リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)」を参照してください。  
  
<a name="composition"></a>
### <a name="composition-of-the-logical-tree"></a>論理ツリーの構成  
 論理ツリーは WPF フレームワーク レベルで定義されます<xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkContentElement>。 ただし、実際に<xref:System.Windows.LogicalTreeHelper>API を使用しているかどうかがわかるように、論理ツリーには、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>でなくてもノードが含まれている場合があります。 たとえば、論理ツリーは、文字列である<xref:System.Windows.Controls.TextBlock.Text%2A>a<xref:System.Windows.Controls.TextBlock>の値を報告します。  
  
<a name="override_logical_tree"></a>
### <a name="overriding-the-logical-tree"></a>論理ツリーのオーバーライド  
 コントロールの作成者は、一般的なオブジェクトまたはコンテンツ モデルが論理ツリー内でオブジェクトを追加または削除する方法を定義する複数の API をオーバーライドすることにより、論理ツリーをオーバーライドできます。 論理ツリーをオーバーライドする方法の例については、「[論理ツリーのオーバーライド](how-to-override-the-logical-tree.md)」を参照してください。  
  
<a name="pvi"></a>
### <a name="property-value-inheritance"></a>プロパティ値の継承  
 プロパティ値の継承は、ハイブリッド ツリーを通じて実行されます。 プロパティの継承を有効にする<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>プロパティを含む実際のメタデータは、WPF<xref:System.Windows.FrameworkPropertyMetadata>フレームワーク レベルのクラスです。 したがって、元の値を保持する親と、その値を継承する子オブジェクトの両方が<xref:System.Windows.FrameworkElement>or<xref:System.Windows.FrameworkContentElement>である必要があり、どちらも論理ツリーの一部である必要があります。 ただし、プロパティの継承をサポートする既存の WPF プロパティの場合、プロパティ値の継承は、論理ツリーに含まれていない間のオブジェクトを通じて永続化できます。 主に、テンプレート要素がテンプレート化されたインスタンスまたはページレベルの構成の上位レベルで設定された継承されたプロパティ値を使用し、論理ツリーで高いレベルに使用する場合に関係します。 プロパティ値の継承がこのような境界を越えて一貫して機能するには、継承するプロパティを添付プロパティとして登録する必要があります。継承動作。 プロパティの継承に使用される正確なツリーは、実行時であっても、ヘルパー クラス ユーティリティ メソッドによって完全に予測することはできません。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。  
  
<a name="two_trees"></a>
## <a name="the-visual-tree"></a>ビジュアルツリー  
 論理ツリーの概念に加えて、 のビジュアル ツリーの概念もあります[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 ビジュアル ツリーは、基本クラスで表されるビジュアル オブジェクトの構造<xref:System.Windows.Media.Visual>を記述します。 コントロールのテンプレートを作成する場合、そのコントロールに適用されるビジュアル ツリーを定義または再定義します。 ビジュアル ツリーは、パフォーマンスと最適化の理由から描画を低レベルで制御する開発者にとっても興味深いものです。 従来[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のアプリケーション プログラミングの一部としてビジュアル ツリーが公開されている 1 つは、ルーティング イベントのイベント ルートが、論理ツリーではなくビジュアル ツリーに沿って移動する場合です。 このルーティング イベント動作の微妙な動作は、コントロールの作成者でない限り、すぐには明らかではないかもしれません。 ビジュアル ツリーを介したイベントのルーティングにより、ビジュアル レベルでのコンポジションを実装するコントロールが、イベントを処理したり、イベント セッターを作成したりできます。  
  
<a name="trees_content"></a>
## <a name="trees-content-elements-and-content-hosts"></a>ツリー、コンテンツ要素、およびコンテンツ ホスト  
 コンテンツ要素 ( から<xref:System.Windows.ContentElement>派生するクラス ) はビジュアル ツリーの一部ではありません。これらのオブジェクトは、継承<xref:System.Windows.Media.Visual>せず、ビジュアル表現も持っていません。 UI に表示するには、 a <xref:System.Windows.ContentElement> <xref:System.Windows.Media.Visual>と論理ツリーの両方の要素であるコンテンツ ホストで ホストする必要があります。 通常、このようなオブジェクトは<xref:System.Windows.FrameworkElement>. コンテンツ ホストがコンテンツの "ブラウザ" に似たような概念を持ち、ホストが制御する画面領域内でそのコンテンツを表示する方法を選択できます。 コンテンツがホストされると、コンテンツは、通常はビジュアル ツリーに関連付けられている特定のツリー プロセスの参加要素にすることができます。 一般に<xref:System.Windows.FrameworkElement>、ホスト クラスには、ホストされる<xref:System.Windows.ContentElement>コンテンツが実際のビジュアル ツリーの一部ではない場合でも、コンテンツ論理ツリーのサブノードを通じてイベント ルートにホストされる任意の要素を追加する実装コードが含まれます。 これは、自身以外の<xref:System.Windows.ContentElement>要素にルーティングするルーティング イベントをソースとして指定するために必要です。  
  
<a name="tree_traversal"></a>
## <a name="tree-traversal"></a>ツリートラバーサル  
 この<xref:System.Windows.LogicalTreeHelper>クラスには<xref:System.Windows.LogicalTreeHelper.GetChildren%2A>、論理<xref:System.Windows.LogicalTreeHelper.GetParent%2A>ツリー走査<xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A>用の メソッド 、、およびメソッドが用意されています。 ほとんどの場合、これらのコントロールは、ほとんどの場合、インデクサーなどの`Add`コレクション アクセスをサポートする専用のコレクション プロパティとして論理子要素を公開するため、既存のコントロールの論理ツリーを走査する必要はありません。 ツリー トラバーサルは主に、コレクション プロパティが既に定義されているなどの<xref:System.Windows.Controls.ItemsControl><xref:System.Windows.Controls.Panel>目的のコントロール パターンから派生しないことを選択し、独自のコレクション プロパティ サポートを提供するコントロール作成者によって使用されるシナリオです。  
  
 ビジュアル ツリーでは、ビジュアル ツリートラバーサルのヘルパー<xref:System.Windows.Media.VisualTreeHelper>クラスもサポートしています。 ビジュアル ツリーは、コントロール固有のプロパティを使用して便利に公開されないので<xref:System.Windows.Media.VisualTreeHelper>、プログラミング シナリオに必要な場合は、クラスがビジュアル ツリーを走査する方法として推奨されます。 詳しくは、「[WPF グラフィックス レンダリングの概要](../graphics-multimedia/wpf-graphics-rendering-overview.md)」をご覧ください。  
  
> [!NOTE]
> 適用されたテンプレートのビジュアル ツリーを調べる必要がある場合があります。 この手法を使用する場合は注意が必要です。 テンプレートを定義するコントロールのビジュアル ツリーを走査する場合でも、コントロールのコンシューマーは、インスタンスに<xref:System.Windows.Controls.Control.Template%2A>プロパティを設定することでテンプレートを常に変更でき、エンド ユーザーもシステム テーマを変更することで適用されたテンプレートに影響を与えることができます。  
  
<a name="routes"></a>
## <a name="routes-for-routed-events-as-a-tree"></a>ルーティング イベントのルートを "ツリー" として  
 前述のように、特定のルーティング イベントのルートは、ビジュアルツリー表現と論理ツリー表現のハイブリッドであるツリーの 1 つの定義済みのパスに沿って移動します。 イベント ルートは、トンネルルーティング イベントかバブル ルーティング イベントかに応じて、ツリー内の上方向または下方向に移動できます。 イベント ルートの概念には、実際にルーティングするイベントを発生させるのとは無関係に、イベント ルートを "ウォーク" するために使用できる直接サポートヘルパー クラスはありません。 ルートを表すクラスがありますが、<xref:System.Windows.EventRoute>そのクラスのメソッドは一般に内部使用専用です。  
  
<a name="resourcesandtrees"></a>
## <a name="resource-dictionaries-and-trees"></a>リソース ディクショナリとツリー  
 ページで定義されているすべての`Resources`リソース ディクショナリの検索は、基本的に論理ツリーを走査します。 論理ツリーにないオブジェクトはキー指定されたリソースを参照できますが、リソース検索シーケンスは、そのオブジェクトが論理ツリーに接続されている位置から始まります。 WPF では、論理ツリー ノードだけが`Resources`を含むプロパティ<xref:System.Windows.ResourceDictionary>を持つことができるので、ビジュアル ツリーを走査してキー付きリソースを探しても<xref:System.Windows.ResourceDictionary>何のメリットもありません。  
  
 ただし、リソース参照は、直接の論理ツリーを超えて拡張することもできます。 アプリケーション マークアップの場合、リソース検索はアプリケーション レベルのリソース ディクショナリに続き、静的プロパティまたはキーとして参照されるテーマ サポートとシステム値に続きます。 また、リソース参照が動的である場合、テーマ自体はテーマ論理ツリーの外部でシステム値を参照できます。 リソース ディクショナリと参照ロジックの詳細については[、「XAML リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [入力の概要](input-overview.md)
- [WPF グラフィックス レンダリングの概要](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [ルーティング イベントの概要](routed-events-overview.md)
- [オブジェクト ツリーに存在しないオブジェクト要素の初期化](initialization-for-object-elements-not-in-an-object-tree.md)
- [WPF アーキテクチャ](wpf-architecture.md)
