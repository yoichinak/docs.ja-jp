---
title: パネルの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: d77ce78fe914bf300c5b33019d7cf67aa4ad74c3
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291448"
---
# <a name="panels-overview"></a>パネルの概要
@no__t 0 の要素は、要素のサイズと大きさ、位置、および子コンテンツの配置を制御するコンポーネントです。 @No__t-0 には、定義済みの <xref:System.Windows.Controls.Panel> 要素が多数用意されています。また、カスタム <xref:System.Windows.Controls.Panel> 要素を作成することもできます。  
  
 このトピックは次のセクションで構成されます。  
  
- [パネル クラス](#Panels_view_from_10000_feet)  
  
- [パネルの要素の一般的なメンバー](#Panels_declared_members)  
  
- [派生パネル要素](#Panels_derived_elements)  
  
- [ユーザー インターフェイス パネル](#Panels_main_UI_elements)  
  
- [入れ子になったパネル要素](#Panels_nested_panel_elements)  
  
- [カスタム パネル要素](#Panels_custom_panel_elements)  
  
- [ローカライズ/グローバリゼーション サポート](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>パネル クラス  
 <xref:System.Windows.Controls.Panel> は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でレイアウトをサポートするすべての要素の基本クラスです。 @No__t-0 の派生要素は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] とコードの要素を配置および整列するために使用されます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、多くの複雑なレイアウトを可能にする派生パネル実装の総合的なスイートが含まれます。 これらの派生クラスは、標準 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] シナリオのほとんどを可能にするプロパティとメソッドを公開します。 ニーズを満たす子配置動作を見つけられない開発者は、<xref:System.Windows.FrameworkElement.ArrangeOverride%2A> および <xref:System.Windows.FrameworkElement.MeasureOverride%2A> の各メソッドをオーバーライドすることにより、新しいレイアウトを作成できます。 カスタム レイアウト動作の詳細については、「[カスタム パネル要素](#Panels_custom_panel_elements)」を参照してください。  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>パネルの一般的なメンバー  
 すべての <xref:System.Windows.Controls.Panel> 要素は、<xref:System.Windows.FrameworkElement> (<xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.FrameworkElement.LayoutTransform%2A> を含む) で定義された基本サイズ設定および配置プロパティをサポートします。 @No__t-0 によって定義される配置プロパティの詳細については、「[配置、余白、パディングの概要](../advanced/alignment-margins-and-padding-overview.md)」を参照してください。  
  
 <xref:System.Windows.Controls.Panel> は、レイアウトを理解して使用するうえで重要な追加のプロパティを公開します。 @No__t-0 プロパティは、派生パネル要素の境界と <xref:System.Windows.Media.Brush> との間の領域を塗りつぶすために使用されます。 <xref:System.Windows.Controls.Panel.Children%2A> は、@no__t が構成されている要素の子コレクションを表します。 <xref:System.Windows.Controls.Panel.InternalChildren%2A> は、<xref:System.Windows.Controls.Panel.Children%2A> コレクションの内容と、データバインディングによって生成されるメンバーを表します。 どちらも、親 <xref:System.Windows.Controls.Panel> でホストされている子要素の @no__t 0 で構成されます。  
  
 また、Panel は、派生 <xref:System.Windows.Controls.Panel> のレイヤー順を実現するために使用できる @no__t 0 の添付プロパティも公開します。 より大きい <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> の値を持つパネルの @no__t 0 のコレクションのメンバーは、<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> の値が小さい方の前に表示されます。 これは、子が同じ座標空間を共有できるようにする <xref:System.Windows.Controls.Canvas> や <xref:System.Windows.Controls.Grid> などのパネルで特に便利です。  
  
 <xref:System.Windows.Controls.Panel> は、<xref:System.Windows.Controls.Panel.OnRender%2A> メソッドも定義します。このメソッドは、@no__t の既定のプレゼンテーション動作をオーバーライドするために使用できます。  
  
#### <a name="attached-properties"></a>アタッチされるプロパティ  
 派生パネル要素は、添付プロパティを広く活用しています。 添付プロパティは、従来の共通言語ランタイム (CLR) プロパティ "ラッパー" を持たない特殊な形式の依存関係プロパティです。 添付プロパティは、下記の例に見られるとおり、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 内に特殊な構文を持ちます。  
  
 添付プロパティの目的の 1 つは、親要素によって実際に定義されたプロパティの一意の値を子要素が格納できるようにすることです。 この機能の応用方法の 1 つは、子要素から親要素に [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] でどのように表示したいかを通知させることであり、これはアプリケーション レイアウトに非常に役立ちます。 詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>派生パネル要素  
 多くのオブジェクトは @no__t 0 から派生しますが、すべてのオブジェクトがルートレイアウトプロバイダーとして使用するためのものではありません。 アプリケーション @no__t の作成専用に設計された、6つの定義済みのパネルクラス (<xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Grid>、<xref:System.Windows.Controls.StackPanel>、@no__t、<xref:System.Windows.Controls.WrapPanel>) があります。  
  
 次の表に各パネル要素でカプセル化されているそれぞれの特殊機能を示します。  
  
|要素名|UI パネル?|説明|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|はい|@No__t-0 領域を基準とした相対的な座標によって子要素を明示的に配置できる領域を定義します。|  
|<xref:System.Windows.Controls.DockPanel>|はい|子要素を互いに水平方向または垂直方向に整列する領域を定義します。|  
|<xref:System.Windows.Controls.Grid>|はい|列と行で構成されている柔軟なグリッド領域を定義します。 @No__t 0 の子要素は、<xref:System.Windows.FrameworkElement.Margin%2A> プロパティを使用して正確に配置できます。|  
|<xref:System.Windows.Controls.StackPanel>|はい|子要素を水平方向または垂直方向の単一行に整列します。|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|いいえ|@No__t 0 のタブボタンのレイアウトを処理します。|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|いいえ|@No__t 0 コントロール内にコンテンツを配置します。|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|いいえ|<xref:System.Windows.Controls.Primitives.UniformGrid> を使用して、すべてのセルサイズが等しいグリッド内の子を配置します。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|いいえ|子コレクションを "仮想化" できるパネルに基本クラスを提供します。|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|はい|水平方向または垂直方向の単一行でコンテンツを整列し、仮想化します。|  
|<xref:System.Windows.Controls.WrapPanel>|はい|<xref:System.Windows.Controls.WrapPanel> の場合、子要素は左から右へ順に配置され、内容が格納ボックスの端の次の行に分割されます。 後続の順序は、<xref:System.Windows.Controls.WrapPanel.Orientation%2A> プロパティの値に応じて、上から下または右から左に順番に行われます。|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>ユーザー インターフェイス パネル  
 @No__t 0 で使用できるパネルクラスは6つあり、<xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Controls.DockPanel>、@no__t 4、<xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.VirtualizingStackPanel>、<xref:System.Windows.Controls.WrapPanel> の2つのシナリオを @no__t サポートするように最適化されています。 これらのパネル要素は使いやすく、用途が広く、ほとんどのアプリケーションに対する拡張性があります。  
  
 各派生 <xref:System.Windows.Controls.Panel> 要素は、サイズ変更の制約を別々に扱います。 水平方向または垂直方向のどちらかで @no__t 0 がどのように制約を処理するかを理解することで、レイアウトの予測可能性を高めることができます。  
  
|**パネル名**|**x 方向**|**y 方向**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|コンテンツに対する制約あり。|コンテンツに対する制約あり。|  
|<xref:System.Windows.Controls.DockPanel>|制約あり。|制約あり。|  
|<xref:System.Windows.Controls.StackPanel> (縦向き)|制約あり。|コンテンツに対する制約あり。|  
|<xref:System.Windows.Controls.StackPanel> (水平方向)|コンテンツに対する制約あり。|制約あり。|  
|<xref:System.Windows.Controls.Grid>|制約あり。|制約がありますが、<xref:System.Windows.GridUnitType.Auto> が行と列に適用される場合を除きます。|  
|<xref:System.Windows.Controls.WrapPanel>|コンテンツに対する制約あり。|コンテンツに対する制約あり。|  
  
 これらの各要素の詳細な説明と使用例を次に示します。  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Canvas  
 @No__t-0 要素を使用すると、 *x*座標と*y*座標の絶対値に応じてコンテンツを配置できます。 要素は一意の場所に描画できます。または、要素が同じ座標を占める場合、マークアップに表示される順序が要素の描画順序を決定します。  
  
 <xref:System.Windows.Controls.Canvas> は、任意の <xref:System.Windows.Controls.Panel> のレイアウトを最も柔軟にサポートします。 Height プロパティと Width プロパティは、キャンバスの領域を定義するために使用され、内の要素には親 <xref:System.Windows.Controls.Canvas> の領域を基準とした絶対座標が割り当てられます。 4つのアタッチされたプロパティである @no__t 0、<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType> では、@no__t 内のオブジェクトの配置を細かく制御できます。これにより、開発者は、画面上で要素を正確に配置して配置できます。  
  
#### <a name="cliptobounds-within-a-canvas"></a>キャンバス内の ClipToBounds  
 <xref:System.Windows.Controls.Canvas> は、独自に定義された <xref:System.Windows.FrameworkElement.Height%2A> および <xref:System.Windows.FrameworkElement.Width%2A> 以外の座標でも、画面上の任意の位置に子要素を配置できます。 さらに、<xref:System.Windows.Controls.Canvas> は、その子のサイズの影響を受けません。 その結果、子要素は、親の外接する四角形の外側にある他の要素をオーバーオーバーする可能性があり <xref:System.Windows.Controls.Canvas> です。 @No__t-0 の既定の動作では、親 <xref:System.Windows.Controls.Canvas> の境界の外側に子を描画することができます。 この動作が望ましくない場合は、<xref:System.Windows.UIElement.ClipToBounds%2A> プロパティを `true` に設定できます。 これにより、<xref:System.Windows.Controls.Canvas> が独自のサイズにクリップされます。 <xref:System.Windows.Controls.Canvas> は、子を境界の外側に描画できる唯一のレイアウト要素です。  
  
 この動作は、[Width のプロパティの比較のサンプル](https://go.microsoft.com/fwlink/?LinkID=160050)に図示されています。  
  
#### <a name="defining-and-using-a-canvas"></a>キャンバスの定義と使用  
 @No__t 0 は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] またはコードを使用するだけでインスタンス化できます。 次の例では <xref:System.Windows.Controls.Canvas> を使用してコンテンツを絶対に配置する方法を示します。 このコードでは、100 ピクセルの四角形を 3 つ生成します。 最初の四角形は赤色で、左上 (*x, y*) の位置が (0, 0) に指定されます。 2 番目の四角形は緑色で、左上の位置は (100, 100) となり、最初の四角形の右下になります。 3 番目の四角形は青色で、左上の位置は (50, 50) となるため、最初の四角形の右下の象限および 2 番目の四角形の左上の象限を囲む状態になります。 3 番目の四角形が最後にレイアウトされるため、他の 2 つの四角形の上に重なっているように見えます。つまり、重複している部分は 3 番目の四角形の色とみなされます。  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的なキャンバス要素: ](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 @No__t-0 要素は、子コンテンツ要素で設定された <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 添付プロパティを使用して、コンテナーの端に沿ってコンテンツを配置します。 @No__t-0 が <xref:System.Windows.Controls.Dock.Top> または <xref:System.Windows.Controls.Dock.Bottom> に設定されている場合は、子要素を互いに上または下に配置します。 @No__t-0 が <xref:System.Windows.Controls.Dock.Left> または <xref:System.Windows.Controls.Dock.Right> に設定されている場合、子要素は互いの左側または右側に配置されます。 @No__t-0 プロパティは、<xref:System.Windows.Controls.DockPanel> の子として追加された最後の要素の位置を決定します。  
  
 @No__t-0 を使用すると、一連のボタンなど、関連するコントロールのグループを配置できます。 または、これを使用して、Microsoft Outlook と同様の "ペイン" @no__t 0 を作成することもできます。  
  
#### <a name="sizing-to-content"></a>コンテンツに合わせたサイズの変更  
 @No__t-0 および <xref:System.Windows.FrameworkElement.Width%2A> プロパティが指定されていない場合は、そのコンテンツに対して <xref:System.Windows.Controls.DockPanel> のサイズが指定されます。 サイズは、子要素のサイズに合うように、増減させることができます。 ただし、これらのプロパティが指定されていて、次に指定された子要素の領域がなくなった場合、<xref:System.Windows.Controls.DockPanel> はその子要素またはそれ以降の子要素を表示せず、後続の子要素を測定しません。  
  
#### <a name="lastchildfill"></a>LastChildFill  
 既定では、<xref:System.Windows.Controls.DockPanel> 要素の最後の子は、残りの未割り当て領域を "塗りつぶし" します。 この動作が望ましくない場合は、<xref:System.Windows.Controls.DockPanel.LastChildFill%2A> プロパティを `false` に設定します。  
  
#### <a name="defining-and-using-a-dockpanel"></a>DockPanel の定義と使用  
 次の例では、<xref:System.Windows.Controls.DockPanel> を使用して領域をパーティション分割する方法を示します。 5つの @no__t 0 要素は、親 <xref:System.Windows.Controls.DockPanel> の子として追加されます。 各は、<xref:System.Windows.Controls.DockPanel> の異なる配置プロパティを使用して領域をパーティション分割します。 最後の要素が、残っている未割り当て領域の "塗り潰し" を実行します。  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な DockPanel シナリオ: ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>グリッド  
 @No__t-0 要素は、絶対位置と表形式のデータコントロールの機能をマージします。 @No__t 0 を使用すると、要素を簡単に配置したりスタイルを適用したりできます。 <xref:System.Windows.Controls.Grid> を使用すると、柔軟な行と列のグループ化を定義できます。また、複数の <xref:System.Windows.Controls.Grid> の要素間でサイズ設定情報を共有するためのメカニズムも提供されます。  
  
#### <a name="how-is-grid-different-from-table"></a>グリッドとテーブルを区別する方法  
 <xref:System.Windows.Documents.Table> および <xref:System.Windows.Controls.Grid> はいくつかの一般的な機能を共有しますが、それぞれが異なるシナリオに適しています。 @No__t 0 はフローコンテンツ内で使用するように設計されています (フローコンテンツの詳細については、「[フロードキュメントの概要](../advanced/flow-document-overview.md)」を参照してください)。 グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。 @No__t-0 の場合、@no__t は、改ページ位置の調整、列の折り返し、コンテンツの選択などのフローコンテンツの動作をサポートしますが、<xref:System.Windows.Controls.Grid> ではサポートされません。 一方、<xref:System.Windows.Controls.Grid> は、<xref:System.Windows.Documents.FlowDocument> の外部で最もよく使用されます。たとえば、<xref:System.Windows.Controls.Grid> などの多くの理由で @no__t、行と列のインデックスに基づいて要素が追加されます。 @No__t-0 要素は、子コンテンツのレイヤーを許可し、1つの "セル" 内に複数の要素を配置できるようにします。 <xref:System.Windows.Documents.Table> は、レイヤーをサポートしていません。 @No__t 0 の子要素は、"セル" の境界の領域を基準として絶対に配置できます。 <xref:System.Windows.Documents.Table> はこの機能をサポートしていません。 最後に、<xref:System.Windows.Controls.Grid> は <xref:System.Windows.Documents.Table> よりも軽量です。  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>列と行のサイズ変更動作  
 @No__t 0 内で定義された列と行では、残りの領域を均等に分散するために <xref:System.Windows.GridUnitType.Star> のサイズ変更を利用できます。 行または列の高さまたは幅として <xref:System.Windows.GridUnitType.Star> が選択されている場合、その列または行は使用可能な残りの領域の重み付け比率を受け取ります。 これは、列または行内のコンテンツのサイズに基づいて領域を均等に分散する <xref:System.Windows.GridUnitType.Auto> とは対照的です。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用する場合、この値は `*` または `2*` と表現されます。 最初のケースでは、行または列は使用可能なスペース領域を 1 回受け取り、2 番目のケースでは 2 回受け取ることになります。 この手法を組み合わせて、@no__t 0 および <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> @no__t の値を使用して領域を均等に分散することにより、レイアウト領域を画面領域の割合でパーティション分割することができます。 <xref:System.Windows.Controls.Grid> は、この方法で領域を分散できる唯一のレイアウトパネルです。  
  
#### <a name="defining-and-using-a-grid"></a>グリッドの定義と使用  
 次の例では、Windows の [スタート] メニューで使用可能な [実行] ダイアログボックスに表示されるのと同様の @no__t 0 をビルドする方法を示します。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的なグリッド要素: ](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 @No__t 0 を指定すると、割り当てられた方向に要素を "積み重ねる" ことができます。 既定のスタック方向は、縦です。 @No__t-0 プロパティを使用して、コンテンツフローを制御できます。  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel と DockPanel  
 @No__t-0 も "stack" 子要素を持つことができますが、<xref:System.Windows.Controls.DockPanel> と <xref:System.Windows.Controls.StackPanel> では、一部の使用シナリオでは同様の結果が生成されません。 たとえば、子要素の順序は <xref:System.Windows.Controls.DockPanel> ではなく、<xref:System.Windows.Controls.StackPanel> では影響を受ける可能性があります。 これは、<xref:System.Windows.Controls.StackPanel> が <xref:System.Double.PositiveInfinity> のスタックの方向にあるのに対し、<xref:System.Windows.Controls.DockPanel> では使用可能なサイズのみが測定されるためです。  
  
 この主な相違点を次の例に示します。  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 このイメージにはレンダリング動作の違いが見られます。  
  
 @no__t 0Screenshot ショット:StackPanel と System.windows.controls.dockpanel> スクリーンショット @ no__t-0(./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>StackPanel の定義と使用  
 次の例では、@no__t 0 を使用して、垂直方向に配置された一連のボタンを作成する方法を示します。 水平方向の配置の場合は、<xref:System.Windows.Controls.StackPanel.Orientation%2A> プロパティを <xref:System.Windows.Controls.Orientation.Horizontal> に設定します。  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な StackPanel 要素: ](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 また [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、データバインドされた子コンテンツを自動的に "仮想化" する <xref:System.Windows.Controls.StackPanel> 要素のバリエーションも提供します。 ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、要素のサブセットを多数のデータ項目から生成する手法を指します。 特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。 <xref:System.Windows.Controls.VirtualizingStackPanel> (@no__t によって提供される機能を使用) では、表示項目が計算され、<xref:System.Windows.Controls.ItemsControl> (<xref:System.Windows.Controls.ListBox> や <xref:System.Windows.Controls.ListView> など) の <xref:System.Windows.Controls.ItemContainerGenerator> と連動して、表示される項目の要素のみが作成されます。  
  
 @No__t-0 要素は、<xref:System.Windows.Controls.ListBox> などのコントロールの項目ホストとして自動的に設定されます。 データバインドされたコレクションをホストする場合、コンテンツは、<xref:System.Windows.Controls.ScrollViewer> の境界内にある限り、自動的に仮想化されます。 これにより、多くの子項目をホストする際のパフォーマンスが大幅に向上します。  
  
 次のマークアップは、<xref:System.Windows.Controls.VirtualizingStackPanel> を項目ホストとして使用する方法を示しています。 仮想化を実行するには、<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> 添付プロパティを `true` (既定値) に設定する必要があります。  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> を使用して、子要素を左から右へ順番に配置し、親コンテナーの端に到達したときにコンテンツを次の行に分割します。 コンテンツは水平方向または垂直方向に設定できます。 <xref:System.Windows.Controls.WrapPanel> は、単純なフロー @no__t シナリオに役立ちます。 また、子要素すべてに均等なサイズを適用する際にも使用できます。  
  
 次の例は、@no__t を作成して、コンテナーの端に達したときにラップする <xref:System.Windows.Controls.Button> コントロールを表示する方法を示しています。  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な WrapPanel 要素: ](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>入れ子になったパネル要素  
 @no__t 0 の要素は、複雑なレイアウトを生成するために、互いに入れ子にすることができます。 これは、1つの @no__t 0 が @no__t の一部に対して理想的であっても、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の異なる部分のニーズを満たしていない可能性がある場合に非常に便利です。  
  
 アプリケーションがサポートできる入れ子の量に決められた制限はありませんが、一般的に、目的のレイアウトに必要なパネルのみを使用するようアプリケーションを制限することをお勧めします。 多くの場合、レイアウトコンテナーとして柔軟性があるため、入れ子になったパネルの代わりに @no__t 0 要素を使用できます。 これにより、ツリーから不要な要素が排除され、アプリケーションのパフォーマンスが向上します。  
  
 次の例では、特定のレイアウトを実現するために、入れ子になった <xref:System.Windows.Controls.Panel> 要素を利用する @no__t 0 を作成する方法を示します。 この例では、@no__t 0 の要素を使用して [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の構造を指定し、入れ子になった <xref:System.Windows.Controls.StackPanel> 要素、<xref:System.Windows.Controls.Grid>、および @no__t を使用して、子要素を親 <xref:System.Windows.Controls.DockPanel> 内に正確に配置します。  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![入れ子になったパネルを利用する UI: ](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>カスタム パネル要素  
 @No__t-0 は柔軟なレイアウトコントロールの配列を提供しますが、カスタムレイアウト動作は、<xref:System.Windows.FrameworkElement.ArrangeOverride%2A> および <xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドをオーバーライドすることによっても実現できます。 このオーバーライド メソッド内で新しい配置動作を定義することにより、カスタムのサイズ変更と配置が実行されます。  
  
 同様に、派生クラスに基づくカスタムレイアウト動作 (<xref:System.Windows.Controls.Canvas> や <xref:System.Windows.Controls.Grid> など) を定義するには、<xref:System.Windows.FrameworkElement.ArrangeOverride%2A> および <xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドをオーバーライドします。  
  
 次のマークアップは、カスタム <xref:System.Windows.Controls.Panel> 要素を作成する方法を示しています。 この新しい <xref:System.Windows.Controls.Panel> は `PlotPanel` として定義されており、ハードコーディングされた*x*座標と*y*座標を使用した子要素の配置をサポートしています。 この例では、@no__t 0 の要素 (示されていません) がプロットポイント 50 (*x*) および 50 (*y*) に配置されています。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 より複雑なカスタム パネルの実装を確認するには、[カスタム コンテンツ折り返しパネルの作成のサンプル](https://go.microsoft.com/fwlink/?LinkID=159979)を参照してください。  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>ローカライズ/グローバリゼーション サポート  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、ローカライズ可能な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の作成を支援する多数の機能をサポートしています。  
  
 すべてのパネル要素は、<xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティをネイティブでサポートしています。これを使用すると、ユーザーのロケールまたは言語設定に基づいてコンテンツを動的に再フローできます。 詳細については、「 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 」を参照してください。  
  
 @No__t-0 プロパティは、アプリケーション開発者がローカライズされた [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のニーズを予測できるようにするためのメカニズムを提供します。 このプロパティの @no__t 0 の値を使用すると、親 <xref:System.Windows.Window> は常に動的にサイズを調整してコンテンツに適合し、人工の高さや幅の制限によって制約されません。  
  
 <xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Grid>、<xref:System.Windows.Controls.StackPanel> は、ローカライズ可能な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] に適しています。 ただし、コンテンツは完全に配置されるため、ローカライズが困難になるため、<xref:System.Windows.Controls.Canvas> は適していません。  
  
 ローカライズ可能なユーザーインターフェイス (Ui) を使用して @no__t 0 アプリケーションを作成する方法の詳細については、「[自動レイアウトの使用の概要](../advanced/use-automatic-layout-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: 初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF レイアウト ギャラリー サンプル](https://go.microsoft.com/fwlink/?LinkID=160054)
- [レイアウト](../advanced/layout.md)
- [WPF Controls Gallery Sample](https://go.microsoft.com/fwlink/?LinkID=160053)
- [配置、余白、パディングの概要](../advanced/alignment-margins-and-padding-overview.md)
- [カスタムコンテンツラッピングパネルサンプルの作成](https://go.microsoft.com/fwlink/?LinkID=159979)
- [添付プロパティの概要](../advanced/attached-properties-overview.md)
- [自動レイアウトの使用の概要](../advanced/use-automatic-layout-overview.md)
- [レイアウトとデザイン](../advanced/optimizing-performance-layout-and-design.md)
