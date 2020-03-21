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
ms.openlocfilehash: 7810bfbf4f5bedf51e0797a4b9017f589e0b0a8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187580"
---
# <a name="panels-overview"></a>パネルの概要
<xref:System.Windows.Controls.Panel>要素は、要素のサイズとサイズ、位置、子コンテンツの配置などの要素のレンダリングを制御するコンポーネントです。 には[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、カスタム要素を構築する<xref:System.Windows.Controls.Panel>機能と同様に、いくつかの定義済み<xref:System.Windows.Controls.Panel>要素が用意されています。  
  
 このトピックの内容は次のとおりです。  
  
- [パネル クラス](#Panels_view_from_10000_feet)  
  
- [パネルの要素の一般的なメンバー](#Panels_declared_members)  
  
- [派生パネル要素](#Panels_derived_elements)  
  
- [ユーザー インターフェイス パネル](#Panels_main_UI_elements)  
  
- [入れ子になったパネル要素](#Panels_nested_panel_elements)  
  
- [カスタム パネル要素](#Panels_custom_panel_elements)  
  
- [ローカライズ/グローバリゼーション サポート](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>パネル クラス  
 <xref:System.Windows.Controls.Panel>は、 でレイアウトをサポートするすべての要素の基本クラス[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。 派生<xref:System.Windows.Controls.Panel>要素は、要素を配置および配置するために[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]使用され、コードを配置します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、多くの複雑なレイアウトを可能にする派生パネル実装の総合的なスイートが含まれます。 これらの派生クラスは、標準 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] シナリオのほとんどを可能にするプロパティとメソッドを公開します。 必要に応じて子配置動作を見つけることができない開発者は、<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドと<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドをオーバーライドして新しいレイアウトを作成できます。 カスタム レイアウト動作の詳細については、「[カスタム パネル要素](#Panels_custom_panel_elements)」を参照してください。  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>パネルの一般的なメンバー  
 すべての<xref:System.Windows.Controls.Panel>要素は、 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、 、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、 、 <xref:System.Windows.FrameworkElement.Margin%2A>、 など によって<xref:System.Windows.FrameworkElement.LayoutTransform%2A>定義される基本サイズ変更および配置プロパティをサポートします。 で定義される<xref:System.Windows.FrameworkElement>位置プロパティの詳細については、「[配置、余白、およびパディングの概要](../advanced/alignment-margins-and-padding-overview.md)」を参照してください。  
  
 <xref:System.Windows.Controls.Panel>は、レイアウトを理解し、使用する上で非常に重要な追加のプロパティを公開します。 プロパティ<xref:System.Windows.Controls.Panel.Background%2A>は、派生パネル要素の境界間の領域を<xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A>は、で構成される要素の子<xref:System.Windows.Controls.Panel>コレクションを表します。 <xref:System.Windows.Controls.Panel.InternalChildren%2A><xref:System.Windows.Controls.Panel.Children%2A>は、コレクションの内容と、データ バインディングによって生成されたメンバーを表します。 どちらも親内で<xref:System.Windows.Controls.UIElementCollection>ホストされる子要素の 1<xref:System.Windows.Controls.Panel>つから成ります。  
  
 Panel では、派生<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType><xref:System.Windows.Controls.Panel>で階層化順序を実現するために使用できる添付プロパティも公開されます。 より高い<xref:System.Windows.Controls.Panel.Children%2A><xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>値を持つパネルのコレクションのメンバーは、値が小さい<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>方のメンバーの前に表示されます。 これは、子が同じ座標空間を<xref:System.Windows.Controls.Canvas>共有<xref:System.Windows.Controls.Grid>できるようにするパネルなどで特に便利です。  
  
 <xref:System.Windows.Controls.Panel>メソッドも<xref:System.Windows.Controls.Panel.OnRender%2A>定義します。 <xref:System.Windows.Controls.Panel>  
  
#### <a name="attached-properties"></a>アタッチされるプロパティ  
 派生パネル要素は、添付プロパティを広く活用しています。 添付プロパティは、従来の共通言語ランタイム (CLR) プロパティ "ラッパー" を持たない特殊な形式の依存関係プロパティです。 添付プロパティは、下記の例に見られるとおり、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 内に特殊な構文を持ちます。  
  
 添付プロパティの目的の 1 つは、親要素によって実際に定義されたプロパティの一意の値を子要素が格納できるようにすることです。 この機能の応用方法の 1 つは、子要素から親要素に [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] でどのように表示したいかを通知させることであり、これはアプリケーション レイアウトに非常に役立ちます。 詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>派生パネル要素  
 多くのオブジェクトは<xref:System.Windows.Controls.Panel>から派生していますが、すべてのオブジェクトがルート レイアウト プロバイダとして使用されるわけではありません。 <xref:System.Windows.Controls.Canvas>アプリケーション[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の作成専用に設計された<xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid>6 <xref:System.Windows.Controls.StackPanel><xref:System.Windows.Controls.VirtualizingStackPanel>つの定義済<xref:System.Windows.Controls.WrapPanel>みパネル クラス ( 、 、 、 、、および ) があります。  
  
 次の表に各パネル要素でカプセル化されているそれぞれの特殊機能を示します。  
  
|要素名|UI パネル?|説明|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|はい|領域に対する相対座標によって子要素を明示的に配置できる領域を定義<xref:System.Windows.Controls.Canvas>します。|  
|<xref:System.Windows.Controls.DockPanel>|はい|子要素を互いに水平方向または垂直方向に整列する領域を定義します。|  
|<xref:System.Windows.Controls.Grid>|はい|列と行で構成されている柔軟なグリッド領域を定義します。 の子要素は<xref:System.Windows.Controls.Grid>、プロパティを使用して正確<xref:System.Windows.FrameworkElement.Margin%2A>に配置できます。|  
|<xref:System.Windows.Controls.StackPanel>|はい|子要素を水平方向または垂直方向の単一行に整列します。|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|いいえ|のタブ ボタンのレイアウトを処理<xref:System.Windows.Controls.TabControl>します。|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|いいえ|コントロール内のコンテンツを<xref:System.Windows.Controls.ToolBar>配置します。|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|いいえ|<xref:System.Windows.Controls.Primitives.UniformGrid>は、すべてのセル サイズが等しいグリッド内の子を配置するために使用されます。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|いいえ|子コレクションを "仮想化" できるパネルに基本クラスを提供します。|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|はい|水平方向または垂直方向の単一行でコンテンツを整列し、仮想化します。|  
|<xref:System.Windows.Controls.WrapPanel>|はい|<xref:System.Windows.Controls.WrapPanel>子要素を左から右に連続した位置に配置し、内容を含むボックスの端の次の行に分割します。 プロパティの値に応じて、順序が上から下または右から左に順番に実行<xref:System.Windows.Controls.WrapPanel.Orientation%2A>されます。|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>ユーザー インターフェイス パネル  
 で使用できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]6 つのパネル クラスは、シナリオ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]をサポートするために<xref:System.Windows.Controls.Canvas>最適化<xref:System.Windows.Controls.DockPanel>されています<xref:System.Windows.Controls.Grid><xref:System.Windows.Controls.WrapPanel>: <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel>、 、 、 、および . これらのパネル要素は使いやすく、用途が広く、ほとんどのアプリケーションに対する拡張性があります。  
  
 派生<xref:System.Windows.Controls.Panel>要素はそれぞれ、サイズ変更制約を異なる方法で扱います。 水平方向または垂直方向<xref:System.Windows.Controls.Panel>に制約を処理する方法を理解すると、レイアウトの予測が容易になります。  
  
|**パネル名**|**x 方向**|**y 方向**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|コンテンツに対する制約あり。|コンテンツに対する制約あり。|  
|<xref:System.Windows.Controls.DockPanel>|制約あり。|制約あり。|  
|<xref:System.Windows.Controls.StackPanel>(垂直方向)|制約あり。|コンテンツに対する制約あり。|  
|<xref:System.Windows.Controls.StackPanel>(水平方向)|コンテンツに対する制約あり。|制約あり。|  
|<xref:System.Windows.Controls.Grid>|制約あり。|行と列に適用される<xref:System.Windows.GridUnitType.Auto>場合を除き、制約|  
|<xref:System.Windows.Controls.WrapPanel>|コンテンツに対する制約あり。|コンテンツに対する制約あり。|  
  
 これらの各要素の詳細な説明と使用例を次に示します。  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>キャンバス  
 この<xref:System.Windows.Controls.Canvas>要素は、絶対*x 座標*と y*座標*に従ってコンテンツの位置決めを可能にします。 要素は一意の場所に描画できます。または、要素が同じ座標を占める場合、マークアップに表示される順序が要素の描画順序を決定します。  
  
 <xref:System.Windows.Controls.Canvas>は、任意のレイアウトサポートを最<xref:System.Windows.Controls.Panel>も柔軟に提供します。 [高さ] プロパティと [幅] プロパティはキャンバスの領域を定義するために使用され、内部の要素には親<xref:System.Windows.Controls.Canvas>の領域に対する絶対座標が割り当てられます。 の 4<xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>つの<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>添付<xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType>プロパティ<xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>、 、および の使用により<xref:System.Windows.Controls.Canvas>、 内のオブジェクトの配置を細かく制御できるため、開発者は、画面上で要素を正確に配置および配置できます。  
  
#### <a name="cliptobounds-within-a-canvas"></a>キャンバス内の ClipToBounds  
 <xref:System.Windows.Controls.Canvas>子要素は、定義<xref:System.Windows.FrameworkElement.Height%2A>されたと の外部にある座標であっても、画面上の任意の位置に配置できます<xref:System.Windows.FrameworkElement.Width%2A>。 さらに、<xref:System.Windows.Controls.Canvas>その子の大きさの影響を受けません。 その結果、子要素が親<xref:System.Windows.Controls.Canvas>の外接する四角形の外にある他の要素を上に描画することが可能です。 a<xref:System.Windows.Controls.Canvas>の既定の動作では、子を親<xref:System.Windows.Controls.Canvas>の境界外に描画できるようにします。 この動作が望ましくない場合は、<xref:System.Windows.UIElement.ClipToBounds%2A>プロパティを に`true`設定できます。 これにより、<xref:System.Windows.Controls.Canvas>独自のサイズにクリップされます。 <xref:System.Windows.Controls.Canvas>は、子を境界の外に描画できる唯一のレイアウト要素です。  
  
 この動作は、[Width のプロパティの比較のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)に図示されています。  
  
#### <a name="defining-and-using-a-canvas"></a>キャンバスの定義と使用  
 を<xref:System.Windows.Controls.Canvas>使用して、またはコードを使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]して、単にインスタンス化することができます。 次の例は、コンテンツを絶対<xref:System.Windows.Controls.Canvas>に配置する方法を示しています。 このコードでは、100 ピクセルの四角形を 3 つ生成します。 最初の四角形は赤色で、左上 (*x, y*) の位置が (0, 0) に指定されます。 2 番目の四角形は緑色で、左上の位置は (100, 100) となり、最初の四角形の右下になります。 3 番目の四角形は青色で、左上の位置は (50, 50) となるため、最初の四角形の右下の象限および 2 番目の四角形の左上の象限を囲む状態になります。 3 番目の四角形が最後にレイアウトされるため、他の 2 つの四角形の上に重なっているように見えます。つまり、重複している部分は 3 番目の四角形の色とみなされます。  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![一般的なキャンバス要素。](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel  
 要素<xref:System.Windows.Controls.DockPanel>は、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>子コンテンツ要素で設定された添付プロパティを使用して、コンテナの端に沿ってコンテンツを配置します。 または<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType><xref:System.Windows.Controls.Dock.Bottom>に<xref:System.Windows.Controls.Dock.Top>設定すると、子要素が互いの上下に配置されます。 または<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType><xref:System.Windows.Controls.Dock.Right>に<xref:System.Windows.Controls.Dock.Left>設定すると、子要素は互いに左右に配置されます。 プロパティ<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>は、子要素として追加される最後の要素の位置を決定<xref:System.Windows.Controls.DockPanel>します。  
  
 を使用<xref:System.Windows.Controls.DockPanel>して、一連のボタンなど、関連するコントロールのグループを配置できます。 または、Outlook に見られるような "Paned"[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を作成することもできます。  
  
#### <a name="sizing-to-content"></a>コンテンツに合わせたサイズの変更  
 プロパティと<xref:System.Windows.FrameworkElement.Height%2A><xref:System.Windows.FrameworkElement.Width%2A>プロパティが指定されていない場合は<xref:System.Windows.Controls.DockPanel>、そのコンテンツにサイズが設定されます。 サイズは、子要素のサイズに合うように、増減させることができます。 ただし、これらのプロパティが指定され、次に指定された子要素の余地がなくなった場合、<xref:System.Windows.Controls.DockPanel>その子要素または後続の子要素は表示されず、後続の子要素は測定されません。  
  
#### <a name="lastchildfill"></a>LastChildFill  
 既定では、<xref:System.Windows.Controls.DockPanel>要素の最後の子は、残りの未割り当て領域を "埋める" 。 この動作が望ましくない場合は、プロパティ<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>を`false`に設定します。  
  
#### <a name="defining-and-using-a-dockpanel"></a>DockPanel の定義と使用  
 次の例は、 を使用して領域を<xref:System.Windows.Controls.DockPanel>パーティション分割する方法を示しています。 5<xref:System.Windows.Controls.Border>つの要素が親<xref:System.Windows.Controls.DockPanel>の子として追加されます。 それぞれがパーティション空間の異なる位置プロパティ<xref:System.Windows.Controls.DockPanel>を使用します。 最後の要素が、残っている未割り当て領域の "塗り潰し" を実行します。  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![一般的な DockPanel シナリオ。](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>グリッド  
 要素<xref:System.Windows.Controls.Grid>は、絶対位置指定と表形式のデータ コントロールの機能をマージします。 A<xref:System.Windows.Controls.Grid>を使用すると、要素を簡単に配置し、スタイルを設定できます。 <xref:System.Windows.Controls.Grid>では、行と列のグループ化を柔軟に定義でき、複数<xref:System.Windows.Controls.Grid>の要素間でサイジング情報を共有するメカニズムも提供できます。  
  
#### <a name="how-is-grid-different-from-table"></a>グリッドとテーブルを区別する方法  
 <xref:System.Windows.Documents.Table>共通<xref:System.Windows.Controls.Grid>の機能を共有しますが、それぞれのシナリオに最適です。 A<xref:System.Windows.Documents.Table>はフロー コンテンツ内で使用するように設計されています (フロー コンテンツの詳細については、「[フロー ドキュメントの概要](../advanced/flow-document-overview.md)」を参照)。 グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。 <xref:System.Windows.Documents.FlowDocument>内では、<xref:System.Windows.Documents.Table>ページネーション、列のリフロー、コンテンツ選択などのフローコンテンツの動作をサポートしますが<xref:System.Windows.Controls.Grid>、a はサポートしません。 一<xref:System.Windows.Controls.Grid>方、行と列のインデックスに基づく<xref:System.Windows.Documents.FlowDocument>要素の追加など<xref:System.Windows.Controls.Grid>、<xref:System.Windows.Documents.Table>多くの理由から、A は使用するのが最適です。 この<xref:System.Windows.Controls.Grid>要素を使用すると、子コンテンツの階層化が可能になり、1 つの "セル" 内に複数の要素が存在できます。 <xref:System.Windows.Documents.Table>は、レイヤ化をサポートしていません。 子要素は<xref:System.Windows.Controls.Grid>、"セル" 境界の領域に対して絶対に位置指定できます。 <xref:System.Windows.Documents.Table>この機能はサポートされていません。 最後に、 <xref:System.Windows.Controls.Grid> a は<xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>列と行のサイズ変更動作  
 内で定義された列と<xref:System.Windows.Controls.Grid>行は、サイズ<xref:System.Windows.GridUnitType.Star>変更を利用して、残りのスペースを比例的に分散させることができます。 行<xref:System.Windows.GridUnitType.Star>または列の高さまたは幅として選択すると、その列または行は、残りの使用可能なスペースの重み付けされた比率を受け取ります。 これは、列または行<xref:System.Windows.GridUnitType.Auto>内のコンテンツのサイズに基づいて均等にスペースを分配する のとは対照的です。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用する場合、この値は `*` または `2*` と表現されます。 最初のケースでは、行または列は使用可能なスペース領域を 1 回受け取り、2 番目のケースでは 2 回受け取ることになります。 この手法を組み合わせて、領域をその値<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>`Stretch`と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>比例的に分散させることにより、画面領域の割合でレイアウト空間を分割することが可能です。 <xref:System.Windows.Controls.Grid>は、この方法でスペースを分散できる唯一のレイアウト パネルです。  
  
#### <a name="defining-and-using-a-grid"></a>グリッドの定義と使用  
 次の例は、Windows の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)][スタート] メニューで使用できる [ファイル名を指定して実行] ダイアログ ボックスに表示されるようなビルド方法を示しています。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![一般的なグリッド要素。](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 A<xref:System.Windows.Controls.StackPanel>を使用すると、割り当てられた方向に要素を"積み重ねる"ことが可能です。 既定のスタック方向は、縦です。 この<xref:System.Windows.Controls.StackPanel.Orientation%2A>プロパティを使用して、コンテンツ フローを制御できます。  
  
#### <a name="stackpanel-vs-dockpanel"></a>スタックパネル対ドックパネル  
 子<xref:System.Windows.Controls.DockPanel>要素を "スタック" することも<xref:System.Windows.Controls.DockPanel>可能<xref:System.Windows.Controls.StackPanel>ですが、一部の使用シナリオでは類似した結果を生成しません。 たとえば、子要素の順序は、 の<xref:System.Windows.Controls.DockPanel>サイズには影響しません。 <xref:System.Windows.Controls.StackPanel> これは、で<xref:System.Windows.Controls.StackPanel>積み重ねる方向のメジャーに<xref:System.Double.PositiveInfinity>対<xref:System.Windows.Controls.DockPanel>して、使用可能なサイズのみを測定するためです。  
  
 この主な相違点を次の例に示します。  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 このイメージにはレンダリング動作の違いが見られます。  
  
 ![スクリーンショット: StackPanel と DockPanel のスクリーンショット](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>StackPanel の定義と使用  
 を使用して、垂直方向<xref:System.Windows.Controls.StackPanel>に配置されたボタンのセットを作成する方法を次の例に示します。 水平位置の場合は、プロパティ<xref:System.Windows.Controls.StackPanel.Orientation%2A>を<xref:System.Windows.Controls.Orientation.Horizontal>に設定します。  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![一般的な StackPanel 要素。](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]また、データ バインド子<xref:System.Windows.Controls.StackPanel>コンテンツを自動的に 「仮想化」する要素のバリエーションも提供します。 ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、要素のサブセットを多数のデータ項目から生成する手法を指します。 特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。 <xref:System.Windows.Controls.VirtualizingStackPanel>( によって提供される<xref:System.Windows.Controls.VirtualizingPanel>機能を通じて ) は、<xref:System.Windows.Controls.ItemContainerGenerator>表示可能<xref:System.Windows.Controls.ItemsControl>な項目を<xref:System.Windows.Controls.ListBox>計算<xref:System.Windows.Controls.ListView>し、 ( または など ) から 、 を使用して、可視項目の要素のみを作成します。  
  
 要素<xref:System.Windows.Controls.VirtualizingStackPanel>は、 などのコントロールの items ホストとして自動的に<xref:System.Windows.Controls.ListBox>設定されます。 データ バインド コレクションをホストする場合、コンテンツが<xref:System.Windows.Controls.ScrollViewer>の範囲内にある限り、コンテンツは自動的に仮想化されます。 これにより、多くの子項目をホストする際のパフォーマンスが大幅に向上します。  
  
 次のマークアップは、アイテム ホストとして<xref:System.Windows.Controls.VirtualizingStackPanel>を使用する方法を示しています。 仮想化<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>を行うには、添付プロパティ`true`を (既定) に設定する必要があります。  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>は、親コンテナの端に達したときにコンテンツを次の行に分割して、子要素を左から右に連続した位置に配置するために使用されます。 コンテンツは水平方向または垂直方向に設定できます。 <xref:System.Windows.Controls.WrapPanel>は、単純なフロー[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]シナリオに役立ちます。 また、子要素すべてに均等なサイズを適用する際にも使用できます。  
  
 コンテナーの端に到達したときにラップ<xref:System.Windows.Controls.WrapPanel>するコントロールを表示<xref:System.Windows.Controls.Button>するを作成する方法を次の例に示します。  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![一般的な WrapPanel 要素。](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>入れ子になったパネル要素  
 <xref:System.Windows.Controls.Panel>要素は、複雑なレイアウトを生成するために、互いにネストすることができます。 これは、の<xref:System.Windows.Controls.Panel>一部に最適ですが[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、の別の部分のニーズを満たしていない状況で非常に便利です。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
 アプリケーションがサポートできる入れ子の量に決められた制限はありませんが、一般的に、目的のレイアウトに必要なパネルのみを使用するようアプリケーションを制限することをお勧めします。 多くの場合、レイアウト<xref:System.Windows.Controls.Grid>コンテナとしての柔軟性により、要素はネストされたパネルの代わりに使用できます。 これにより、ツリーから不要な要素が排除され、アプリケーションのパフォーマンスが向上します。  
  
 次の例は、入れ子になった[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]<xref:System.Windows.Controls.Panel>要素を利用して特定のレイアウトを実現する を作成する方法を示しています。 この特定のケースでは、<xref:System.Windows.Controls.DockPanel>要素を使用して構造体[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を提供し、入<xref:System.Windows.Controls.StackPanel>れ子になった<xref:System.Windows.Controls.Grid>要素、a、および a<xref:System.Windows.Controls.Canvas>を使用して親<xref:System.Windows.Controls.DockPanel>の内部に子要素を正確に配置します。  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![入れ子になったパネルを利用する UI。](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>カスタム パネル要素  
 柔軟[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]なレイアウト コントロールの配列を提供する一方で、カスタム レイアウトの動作は、 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドと メソッドをオーバーライドすることによっても実現できます。 このオーバーライド メソッド内で新しい配置動作を定義することにより、カスタムのサイズ変更と配置が実行されます。  
  
 同様に、派生クラスに基づくカスタム レイアウト動作<xref:System.Windows.Controls.Canvas>(<xref:System.Windows.Controls.Grid>や など ) は<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>それらのメソッドをオーバーライドして定義できます。  
  
 次のマークアップは、カスタム<xref:System.Windows.Controls.Panel>要素を作成する方法を示しています。 として定義<xref:System.Windows.Controls.Panel>されたこの新`PlotPanel`しいは、ハードコーディングされた*x 座標*と*y 座標*を使用して子要素の位置決めをサポートします。 この例では<xref:System.Windows.Shapes.Rectangle>、(図示しない)要素がプロットポイント50(x)、50(y)*y*に配置されます。*x*  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 より複雑なカスタム パネルの実装を確認するには、[カスタム コンテンツ折り返しパネルの作成のサンプル](https://go.microsoft.com/fwlink/?LinkID=159979)を参照してください。  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>ローカライズ/グローバリゼーション サポート  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、ローカライズ可能な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の作成を支援する多数の機能をサポートしています。  
  
 すべてのパネル要素は、ユーザーの<xref:System.Windows.FrameworkElement.FlowDirection%2A>ロケールまたは言語設定に基づいてコンテンツを動的に再フローするために使用できるプロパティをネイティブにサポートします。 詳細については、<xref:System.Windows.FrameworkElement.FlowDirection%2A> を参照してください。  
  
 この<xref:System.Windows.Window.SizeToContent%2A>プロパティは、アプリケーション開発者がローカライズされた[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のニーズを予測できるようにするメカニズムを提供します。 このプロパティ<xref:System.Windows.SizeToContent.WidthAndHeight>の値を使用すると、親<xref:System.Windows.Window>はコンテンツに合わせて常に動的にサイズを調整し、人工的な高さや幅の制限によって制約されません。  
  
 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid>、<xref:System.Windows.Controls.StackPanel>および、ローカライズ可能なに適した選択肢[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 <xref:System.Windows.Controls.Canvas>しかし、コンテンツは絶対に配置されるため、ローカライズが困難になるため、良い選択ではありません。  
  
 ローカライズ可能なユーザー[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インターフェイス (UI) を使用したアプリケーションの作成の詳細については、「[自動レイアウトの概要を使用](../advanced/use-automatic-layout-overview.md)する 」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: 初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF レイアウト ギャラリー サンプル](https://go.microsoft.com/fwlink/?LinkID=160054)
- [レイアウト](../advanced/layout.md)
- [WPF コントロール ギャラリーのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [配置、余白、パディングの概要](../advanced/alignment-margins-and-padding-overview.md)
- [カスタム コンテンツ折り返しパネルの作成のサンプル](https://go.microsoft.com/fwlink/?LinkID=159979)
- [添付プロパティの概要](../advanced/attached-properties-overview.md)
- [自動レイアウトの使用の概要](../advanced/use-automatic-layout-overview.md)
- [レイアウトとデザイン](../advanced/optimizing-performance-layout-and-design.md)
