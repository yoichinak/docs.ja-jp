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
ms.openlocfilehash: 5fe464f2b79fa1f7b0674c049110d32f2ad32335
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944819"
---
# <a name="panels-overview"></a>パネルの概要
<xref:System.Windows.Controls.Panel>要素は、要素のサイズと大きさ、位置、および子コンテンツの配置を制御するコンポーネントです。 に[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、いくつかの<xref:System.Windows.Controls.Panel>定義済み要素と、カスタム<xref:System.Windows.Controls.Panel>要素を作成する機能が用意されています。  
  
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
 <xref:System.Windows.Controls.Panel>は、で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]レイアウトサポートを提供するすべての要素の基本クラスです。 派生<xref:System.Windows.Controls.Panel>要素は、およびコードで[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]要素を配置および整列するために使用されます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、多くの複雑なレイアウトを可能にする派生パネル実装の総合的なスイートが含まれます。 これらの派生クラスは、標準 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] シナリオのほとんどを可能にするプロパティとメソッドを公開します。 ニーズを満たす子配置動作を見つけられない開発者は、メソッド<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>とメソッドをオーバーライドすることにより、 <xref:System.Windows.FrameworkElement.MeasureOverride%2A>新しいレイアウトを作成できます。 カスタム レイアウト動作の詳細については、「[カスタム パネル要素](#Panels_custom_panel_elements)」を参照してください。  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>パネルの一般的なメンバー  
 すべて<xref:System.Windows.Controls.Panel>の要素は、、、、、、および<xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Height%2A>を<xref:System.Windows.FrameworkElement.LayoutTransform%2A>含む、で定義された基本サイズ設定および配置プロパティをサポートしています。 <xref:System.Windows.FrameworkElement.Margin%2A> によっ<xref:System.Windows.FrameworkElement>て定義された配置プロパティの詳細については、「[配置、余白、パディングの概要](../advanced/alignment-margins-and-padding-overview.md)」を参照してください。  
  
 <xref:System.Windows.Controls.Panel>レイアウトを理解して使用するうえで重要な追加プロパティを公開します。 プロパティは、派生パネル要素の境界とを<xref:System.Windows.Media.Brush>使用して領域を塗りつぶすために使用されます。 <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Panel.Children%2A><xref:System.Windows.Controls.Panel>が構成されている要素の子コレクションを表します。 <xref:System.Windows.Controls.Panel.InternalChildren%2A><xref:System.Windows.Controls.Panel.Children%2A>コレクションの内容と、データバインディングによって生成されるメンバーを表します。 どちらも、親<xref:System.Windows.Controls.UIElementCollection> <xref:System.Windows.Controls.Panel>内でホストされる子要素ので構成されます。  
  
 また、Panel は<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> 、派生<xref:System.Windows.Controls.Panel>されたで階層の順序を実現するために使用できる添付プロパティも公開します。 値が大きい<xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>パネルのコレクションのメンバーは、値が小さい<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>方の前に表示されます。 これは、や<xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Grid>などのパネルで、子が同じ座標空間を共有できるようにする場合に特に便利です。  
  
 <xref:System.Windows.Controls.Panel>では<xref:System.Windows.Controls.Panel.OnRender%2A> <xref:System.Windows.Controls.Panel>、の既定のプレゼンテーション動作をオーバーライドするために使用できるメソッドも定義されています。  
  
#### <a name="attached-properties"></a>アタッチされるプロパティ  
 派生パネル要素は、添付プロパティを広く活用しています。 添付プロパティは、従来の共通言語ランタイム (CLR) プロパティ "ラッパー" を持たない特殊な形式の依存関係プロパティです。 添付プロパティは、下記の例に見られるとおり、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 内に特殊な構文を持ちます。  
  
 添付プロパティの目的の 1 つは、親要素によって実際に定義されたプロパティの一意の値を子要素が格納できるようにすることです。 この機能の応用方法の 1 つは、子要素から親要素に [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] でどのように表示したいかを通知させることであり、これはアプリケーション レイアウトに非常に役立ちます。 詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>派生パネル要素  
 多くのオブジェクトは<xref:System.Windows.Controls.Panel>から派生しますが、それらのすべてがルートレイアウトプロバイダーとして使用するためのものではありません。 <xref:System.Windows.Controls.Canvas>アプリケーション<xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.WrapPanel>の作成専用に設計された、6つの定義済みのパネルクラス (、、、、、) があります。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
 次の表に各パネル要素でカプセル化されているそれぞれの特殊機能を示します。  
  
|要素名|UI パネル?|説明|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|[はい]|<xref:System.Windows.Controls.Canvas>領域を基準に相対的に子要素を相対的に配置できる領域を定義します。|  
|<xref:System.Windows.Controls.DockPanel>|[はい]|子要素を互いに水平方向または垂直方向に整列する領域を定義します。|  
|<xref:System.Windows.Controls.Grid>|[はい]|列と行で構成されている柔軟なグリッド領域を定義します。 の<xref:System.Windows.Controls.Grid>子要素は、 <xref:System.Windows.FrameworkElement.Margin%2A>プロパティを使用して正確に配置できます。|  
|<xref:System.Windows.Controls.StackPanel>|[はい]|子要素を水平方向または垂直方向の単一行に整列します。|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|いいえ|のタブボタン<xref:System.Windows.Controls.TabControl>のレイアウトを処理します。|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|いいえ|コントロール内にコンテンツ<xref:System.Windows.Controls.ToolBar>を配置します。|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|いいえ|<xref:System.Windows.Controls.Primitives.UniformGrid>は、すべてのセルサイズが等しいグリッド内の子を配置するために使用されます。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|いいえ|子コレクションを "仮想化" できるパネルに基本クラスを提供します。|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|[はい]|水平方向または垂直方向の単一行でコンテンツを整列し、仮想化します。|  
|<xref:System.Windows.Controls.WrapPanel>|[はい]|<xref:System.Windows.Controls.WrapPanel>子要素を左から右へ順に配置し、内容を格納ボックスの端の次の行に分割します。 後続の順序付けは、 <xref:System.Windows.Controls.WrapPanel.Orientation%2A>プロパティの値に応じて、上から下または右から左に順番に行われます。|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>ユーザー インターフェイス パネル  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で使用できるパネルクラスは6つあり、、、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel>、 <xref:System.Windows.Controls.Canvas>、 <xref:System.Windows.Controls.DockPanel>および<xref:System.Windows.Controls.WrapPanel>の各シナリオをサポートするために最適化されています。 これらのパネル要素は使いやすく、用途が広く、ほとんどのアプリケーションに対する拡張性があります。  
  
 各派生<xref:System.Windows.Controls.Panel>要素は、サイズ変更の制約を別々に扱います。 水平方向また<xref:System.Windows.Controls.Panel>は垂直方向のどちらの方法で制約を処理するかを理解することで、レイアウトの予測可能性を高めることができます。  
  
|**パネル名**|**x 方向**|**y 方向**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|コンテンツに対する制約あり。|コンテンツに対する制約あり。|  
|<xref:System.Windows.Controls.DockPanel>|制約あり。|制約あり。|  
|<xref:System.Windows.Controls.StackPanel>(縦向き)|制約あり。|コンテンツに対する制約あり。|  
|<xref:System.Windows.Controls.StackPanel>(水平方向)|コンテンツに対する制約あり。|制約あり。|  
|<xref:System.Windows.Controls.Grid>|制約あり。|制約あり (行と列<xref:System.Windows.GridUnitType.Auto>に適用される場合を除く)|  
|<xref:System.Windows.Controls.WrapPanel>|コンテンツに対する制約あり。|コンテンツに対する制約あり。|  
  
 これらの各要素の詳細な説明と使用例を次に示します。  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>キャンバス  
 要素<xref:System.Windows.Controls.Canvas>は、 *x*座標と*y*座標の絶対値に応じてコンテンツを配置できるようにします。 要素は一意の場所に描画できます。または、要素が同じ座標を占める場合、マークアップに表示される順序が要素の描画順序を決定します。  
  
 <xref:System.Windows.Controls.Canvas>は、任意<xref:System.Windows.Controls.Panel>のの柔軟なレイアウトサポートを提供します。 Height プロパティと Width プロパティは、キャンバスの領域を定義するために使用され、内の要素には親<xref:System.Windows.Controls.Canvas>の領域を基準とした絶対座標が割り当てられます。 4つのアタッチ<xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>さ<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>れ<xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType>た<xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>プロパティ、、、およびでは<xref:System.Windows.Controls.Canvas>、内のオブジェクトの配置を細かく制御できます。これにより、開発者は、画面上で要素を正確に配置および整列できます。  
  
#### <a name="cliptobounds-within-a-canvas"></a>キャンバス内の ClipToBounds  
 <xref:System.Windows.Controls.Canvas>は、独自に定義さ<xref:System.Windows.FrameworkElement.Height%2A>れたおよび<xref:System.Windows.FrameworkElement.Width%2A>の外にある座標でも、画面上の任意の位置に子要素を配置できます。 さらに<xref:System.Windows.Controls.Canvas> 、は子のサイズの影響を受けません。 その結果、子要素は、親<xref:System.Windows.Controls.Canvas>の外接する四角形の外側にある他の要素にオーバードローする可能性があります。 の<xref:System.Windows.Controls.Canvas>既定の動作では、子が親<xref:System.Windows.Controls.Canvas>の境界の外側に描画されることを許可します。 この動作が望ましくない場合は<xref:System.Windows.UIElement.ClipToBounds%2A> 、プロパティをに`true`設定できます。 これに<xref:System.Windows.Controls.Canvas>より、が独自のサイズにクリップされます。 <xref:System.Windows.Controls.Canvas>は、子を境界の外側に描画できる唯一のレイアウト要素です。  
  
 この動作は、[Width のプロパティの比較のサンプル](https://go.microsoft.com/fwlink/?LinkID=160050)に図示されています。  
  
#### <a name="defining-and-using-a-canvas"></a>キャンバスの定義と使用  
 は<xref:System.Windows.Controls.Canvas> 、またはコードを使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]するだけでインスタンス化できます。 次の例は、を使用<xref:System.Windows.Controls.Canvas>してコンテンツを絶対に配置する方法を示しています。 このコードでは、100 ピクセルの四角形を 3 つ生成します。 最初の四角形は赤色で、左上 (*x, y*) の位置が (0, 0) に指定されます。 2 番目の四角形は緑色で、左上の位置は (100, 100) となり、最初の四角形の右下になります。 3 番目の四角形は青色で、左上の位置は (50, 50) となるため、最初の四角形の右下の象限および 2 番目の四角形の左上の象限を囲む状態になります。 3 番目の四角形が最後にレイアウトされるため、他の 2 つの四角形の上に重なっているように見えます。つまり、重複している部分は 3 番目の四角形の色とみなされます。  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的なキャンバス要素: ](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 要素<xref:System.Windows.Controls.DockPanel>は、子<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>コンテンツ要素で設定されている添付プロパティを使用して、コンテナーの端に沿ってコンテンツを配置します。 が<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>または<xref:System.Windows.Controls.Dock.Top> に設定されている場合は、子要素を互いに上または下に<xref:System.Windows.Controls.Dock.Bottom>配置します。 が<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>または<xref:System.Windows.Controls.Dock.Left> に<xref:System.Windows.Controls.Dock.Right>設定されている場合は、子要素が互いの左側または右側に配置されます。 プロパティ<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>は、 <xref:System.Windows.Controls.DockPanel>の子として追加された最後の要素の位置を決定します。  
  
 を使用<xref:System.Windows.Controls.DockPanel>すると、一連のボタンなど、関連するコントロールのグループを配置できます。 または、これを使用して、Microsoft Outlook と[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]同様の "ペイン" を作成することもできます。  
  
#### <a name="sizing-to-content"></a>コンテンツに合わせたサイズの変更  
 <xref:System.Windows.FrameworkElement.Height%2A>プロパティと<xref:System.Windows.FrameworkElement.Width%2A>プロパティが指定されて<xref:System.Windows.Controls.DockPanel>いない場合、のコンテンツにサイズが調整されます。 サイズは、子要素のサイズに合うように、増減させることができます。 ただし、これらのプロパティが指定されていて、次に指定された子<xref:System.Windows.Controls.DockPanel>要素の領域がなくなった場合、はその子要素または後続の子要素を表示せず、後続の子要素を測定しません。  
  
#### <a name="lastchildfill"></a>LastChildFill  
 既定では、 <xref:System.Windows.Controls.DockPanel>要素の最後の子は、残りの未割り当て領域を "塗りつぶし" します。 この動作が望ましくない場合は、 <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>プロパティをに`false`設定します。  
  
#### <a name="defining-and-using-a-dockpanel"></a>DockPanel の定義と使用  
 次の例は、 <xref:System.Windows.Controls.DockPanel>を使用して領域をパーティション分割する方法を示しています。 5 <xref:System.Windows.Controls.Border>つの要素が親<xref:System.Windows.Controls.DockPanel>の子として追加されます。 各は、の異なる配置プロパティを<xref:System.Windows.Controls.DockPanel>使用して、領域をパーティション分割します。 最後の要素が、残っている未割り当て領域の "塗り潰し" を実行します。  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な DockPanel シナリオ: ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>グリッド  
 要素<xref:System.Windows.Controls.Grid>は、絶対位置と表形式のデータコントロールの機能をマージします。 を<xref:System.Windows.Controls.Grid>使用すると、要素を簡単に配置したりスタイルを適用したりできます。 <xref:System.Windows.Controls.Grid>では、柔軟な行と列のグループ化を定義できます。また、複数<xref:System.Windows.Controls.Grid>の要素間でサイズ情報を共有するためのメカニズムを提供することもできます。  
  
#### <a name="how-is-grid-different-from-table"></a>グリッドとテーブルを区別する方法  
 <xref:System.Windows.Documents.Table>と<xref:System.Windows.Controls.Grid>はいくつかの一般的な機能を共有しますが、それぞれが異なるシナリオに最適です。 は<xref:System.Windows.Documents.Table> 、フローコンテンツ内で使用するように設計されています (フローコンテンツの詳細については、「[フロードキュメントの概要](../advanced/flow-document-overview.md)」を参照してください)。 グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。 内では<xref:System.Windows.Documents.Table> <xref:System.Windows.Controls.Grid> 、は、改ページ位置、列の折り返し、コンテンツの選択などのフローコンテンツの動作をサポートしますが、ではサポートされません。 <xref:System.Windows.Documents.FlowDocument> 一方、は、行と列のインデックスに基づい<xref:System.Windows.Documents.FlowDocument>て要素を追加<xref:System.Windows.Controls.Grid>するなど、 <xref:System.Windows.Documents.Table>さまざまな理由で、の外部で最もよく使用されます。<xref:System.Windows.Controls.Grid> 要素<xref:System.Windows.Controls.Grid>は子コンテンツのレイヤーを許可し、1つの "セル" 内に複数の要素を配置できるようにします。 <xref:System.Windows.Documents.Table>は、レイヤー化をサポートしていません。 の子要素は<xref:System.Windows.Controls.Grid> 、"セル" の境界の領域を基準として絶対に配置できます。 <xref:System.Windows.Documents.Table>では、この機能はサポートされていません。 最後に<xref:System.Windows.Controls.Grid> 、は<xref:System.Windows.Documents.Table>よりも軽量です。  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>列と行のサイズ変更動作  
 で定義されている<xref:System.Windows.Controls.Grid>列と行で<xref:System.Windows.GridUnitType.Star>は、残りの領域を均等に分散するためにサイズ変更を利用できます。 行<xref:System.Windows.GridUnitType.Star>または列の高さまたは幅としてが選択されている場合、その列または行は使用可能な残りの領域の重み付け比率を受け取ります。 これは、列また<xref:System.Windows.GridUnitType.Auto>は行内のコンテンツのサイズに基づいて領域を均等に分散するとは対照的です。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用する場合、この値は `*` または `2*` と表現されます。 最初のケースでは、行または列は使用可能なスペース領域を 1 回受け取り、2 番目のケースでは 2 回受け取ることになります。 この手法を組み合わせて、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>の`Stretch`値を使用して領域を均等に分散することにより、レイアウト領域を画面領域の割合でパーティション分割することができます。 <xref:System.Windows.Controls.Grid>は、この方法で領域を分散できる唯一のレイアウトパネルです。  
  
#### <a name="defining-and-using-a-grid"></a>グリッドの定義と使用  
 次の例では、Windows の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [スタート] メニューにある [実行] ダイアログにあるのと同様のをビルドする方法を示します。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的なグリッド要素: ](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 を<xref:System.Windows.Controls.StackPanel>使用すると、割り当てられた方向に要素を "積み重ねる" ことができます。 既定のスタック方向は、縦です。 プロパティ<xref:System.Windows.Controls.StackPanel.Orientation%2A>は、コンテンツフローを制御するために使用できます。  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel と DockPanel  
 では、子要素を "積み重ねる" <xref:System.Windows.Controls.DockPanel>こと<xref:System.Windows.Controls.StackPanel>もできますが、一部の使用シナリオでは類似した結果が生成されません。 <xref:System.Windows.Controls.DockPanel> たとえば、子要素の順序はでのサイズ<xref:System.Windows.Controls.DockPanel>に影響することがあり<xref:System.Windows.Controls.StackPanel>ますが、には影響しません。 これは、 <xref:System.Windows.Controls.StackPanel>が<xref:System.Double.PositiveInfinity>スタックの方向にあるのに対し<xref:System.Windows.Controls.DockPanel> 、は使用可能なサイズのみを測定するためです。  
  
 この主な相違点を次の例に示します。  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 このイメージにはレンダリング動作の違いが見られます。  
  
 ![スクリーンStackPanel と System.windows.controls.dockpanel> スクリーン]ショット(./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>StackPanel の定義と使用  
 次の例は、を使用し<xref:System.Windows.Controls.StackPanel>て、垂直方向に配置された一連のボタンを作成する方法を示しています。 水平方向の配置の場合<xref:System.Windows.Controls.StackPanel.Orientation%2A>は、 <xref:System.Windows.Controls.Orientation.Horizontal>プロパティをに設定します。  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な StackPanel 要素: ](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]また、は、 <xref:System.Windows.Controls.StackPanel>データバインドされた子コンテンツを自動的に "仮想化する" 要素のバリエーションも提供します。 ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、要素のサブセットを多数のデータ項目から生成する手法を指します。 特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。 <xref:System.Windows.Controls.VirtualizingStackPanel><xref:System.Windows.Controls.VirtualizingPanel>(によって提供される機能を使用) によって、 <xref:System.Windows.Controls.ItemsControl>表示可能な項目が計算され、 <xref:System.Windows.Controls.ListBox>から (または<xref:System.Windows.Controls.ListView>など) のを使用して、 <xref:System.Windows.Controls.ItemContainerGenerator>表示される項目の要素のみが作成されます。  
  
 要素は、 <xref:System.Windows.Controls.ListBox>などのコントロールの項目ホストとして自動的に設定されます。 <xref:System.Windows.Controls.VirtualizingStackPanel> データバインドコレクションをホストする場合、コンテンツがの<xref:System.Windows.Controls.ScrollViewer>境界内にある限り、コンテンツは自動的に仮想化されます。 これにより、多くの子項目をホストする際のパフォーマンスが大幅に向上します。  
  
 次のマークアップは、を<xref:System.Windows.Controls.VirtualizingStackPanel>項目ホストとして使用する方法を示しています。 仮想<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>化を実行するには`true` 、添付プロパティを (既定値) に設定する必要があります。  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>は、子要素を左から右へ順に配置し、親コンテナーの端に到達したときに次の行にコンテンツを分割するために使用されます。 コンテンツは水平方向または垂直方向に設定できます。 <xref:System.Windows.Controls.WrapPanel>は、単純なフロー [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]のシナリオに役立ちます。 また、子要素すべてに均等なサイズを適用する際にも使用できます。  
  
 次の例は、を作成し<xref:System.Windows.Controls.WrapPanel>て、 <xref:System.Windows.Controls.Button>コンテナーの端に達したときにラップするコントロールを表示する方法を示しています。  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な WrapPanel 要素: ](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>入れ子になったパネル要素  
 <xref:System.Windows.Controls.Panel>要素は、複雑なレイアウトを生成するために、互いに入れ子にすることができます。 これは、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の一部に対して理想<xref:System.Windows.Controls.Panel>的なものの、の異なる部分[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のニーズを満たしていない場合に非常に便利です。  
  
 アプリケーションがサポートできる入れ子の量に決められた制限はありませんが、一般的に、目的のレイアウトに必要なパネルのみを使用するようアプリケーションを制限することをお勧めします。 多くの場合、レイアウト<xref:System.Windows.Controls.Grid>コンテナーとして柔軟性があるため、入れ子になったパネルの代わりに要素を使用できます。 これにより、ツリーから不要な要素が排除され、アプリケーションのパフォーマンスが向上します。  
  
 次の例では、特定の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]レイアウトを実現するため<xref:System.Windows.Controls.Panel>に、入れ子になった要素を活用するを作成する方法を示します。 この場合、要素を<xref:System.Windows.Controls.DockPanel>使用して構造体を指定[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid>し、入れ子<xref:System.Windows.Controls.StackPanel>になった要素、 <xref:System.Windows.Controls.Canvas>を使用して、子要素を親内に正確に配置します。  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![入れ子になったパネルを利用する UI: ](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>カスタム パネル要素  
 に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は柔軟なレイアウトコントロールの配列が用意されていますが、メソッド<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>と<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドをオーバーライドすることによってカスタムレイアウト動作を実現することもできます。 このオーバーライド メソッド内で新しい配置動作を定義することにより、カスタムのサイズ変更と配置が実行されます。  
  
 同様に、派生クラス<xref:System.Windows.Controls.Canvas> (や<xref:System.Windows.Controls.Grid>など) に基づくカスタムレイアウト動作は、メソッド<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>および<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドをオーバーライドすることによって定義できます。  
  
 次のマークアップは、カスタム<xref:System.Windows.Controls.Panel>要素を作成する方法を示しています。 とし<xref:System.Windows.Controls.Panel>て定義さ`PlotPanel`れたこの新しいは、ハードコーディングされた*x*座標と*y*座標を使用した子要素の配置をサポートしています。 この例では、 <xref:System.Windows.Shapes.Rectangle> (示されていない) 要素はプロットポイント 50 (*x*) および 50 (*y*) に位置しています。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 より複雑なカスタム パネルの実装を確認するには、[カスタム コンテンツ折り返しパネルの作成のサンプル](https://go.microsoft.com/fwlink/?LinkID=159979)を参照してください。  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>ローカライズ/グローバリゼーション サポート  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、ローカライズ可能な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の作成を支援する多数の機能をサポートしています。  
  
 すべてのパネル要素は、 <xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティをネイティブでサポートしています。これを使用すると、ユーザーのロケールまたは言語設定に基づいてコンテンツを動的に再フローできます。 詳細については、「 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 」を参照してください。  
  
 プロパティ<xref:System.Windows.Window.SizeToContent%2A>は、アプリケーション開発者がローカライズ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]されたのニーズを予測できるようにするメカニズムを提供します。 <xref:System.Windows.SizeToContent.WidthAndHeight> 親<xref:System.Windows.Window>は、このプロパティの値を使用して、コンテンツに応じて動的にサイズが調整され、人工の高さまたは幅の制限によって制約されることはありません。  
  
 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid>、および<xref:System.Windows.Controls.StackPanel>はローカライズ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]可能なすべての選択肢です。 <xref:System.Windows.Controls.Canvas>では、コンテンツが絶対に配置されるため、ローカライズが困難になるため、これは適切な選択ではありません。  
  
 ローカライズ可能な [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] を備えた [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法の詳細については、「[自動レイアウトの使用の概要](../advanced/use-automatic-layout-overview.md)」を参照してください。  
  
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
