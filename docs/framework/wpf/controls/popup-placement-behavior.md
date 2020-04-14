---
title: ポップアップの配置動作
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 1c377e62ffd334638031baee4d4831ac5a31acf3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243259"
---
# <a name="popup-placement-behavior"></a>ポップアップの配置動作
コントロール<xref:System.Windows.Controls.Primitives.Popup>は、アプリケーション上に浮かぶ別のウィンドウにコンテンツを表示します。 コントロール、マウス、または画面に<xref:System.Windows.Controls.Primitives.Popup>対する相対位置は<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 、 、、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>および<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>のプロパティを使用して指定できます。  これらのプロパティは連携して動作し、柔軟に<xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
> また<xref:System.Windows.Controls.ToolTip>、<xref:System.Windows.Controls.ContextMenu>および クラスはこれら 5 つのプロパティを定義し、同様に動作します。  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>ポップアップの配置  
 の<xref:System.Windows.Controls.Primitives.Popup>配置は、画面全体に対して<xref:System.Windows.UIElement>、または画面全体を基準にして配置できます。  次の例では、<xref:System.Windows.Controls.Primitives.Popup>イメージに対する<xref:System.Windows.UIElement>相対 4 つのコントロールを作成します。 すべてのコントロールの<xref:System.Windows.Controls.Primitives.Popup>プロパティは<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>に`image1`設定されていますが、配置<xref:System.Windows.Controls.Primitives.Popup>プロパティの値は異なります。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 次の図は、イメージとコントロール<xref:System.Windows.Controls.Primitives.Popup>を示しています。  
  
 ![4 つのポップアップ コントロールを含む画像](./media/popup-placement-behavior/popup-placement-intro.png "4 つのポップアップを含む画像")
  
 この簡単な例では、 プロパティと<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを設定する方法を<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>示<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>しますが<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>、 、および プロパティを使用すると、<xref:System.Windows.Controls.Primitives.Popup>プロパティの位置を制御できます。  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>用語の定義: ポップアップの構造  
 以下の用語は、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 、 プロパティが相互に関連<xref:System.Windows.Controls.Primitives.Popup>する方法を理解するのに役立ちます。  
  
- [対象になるオブジェクト]  
  
- ターゲット領域  
  
- ターゲットの始点  
  
- ポップアップ配置ポイント  
  
 これらの用語は、関連付けられているコントロール<xref:System.Windows.Controls.Primitives.Popup>のさまざまな側面を参照する便利な方法を提供します。  
  
### <a name="target-object"></a>[対象になるオブジェクト]  
 *ターゲット オブジェクト*は、関連付けられている<xref:System.Windows.Controls.Primitives.Popup>要素です。 プロパティが<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>設定されている場合は、ターゲット オブジェクトを指定します。  が<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>設定されておらず、 に<xref:System.Windows.Controls.Primitives.Popup>親がある場合、親はターゲット オブジェクトです。  値がなく<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、親も存在しない場合、ターゲット オブジェクトはなく、<xref:System.Windows.Controls.Primitives.Popup>画面に対して相対的に位置付けられます。  
  
 次の例では、<xref:System.Windows.Controls.Primitives.Popup>の子である を<xref:System.Windows.Controls.Canvas>作成します。  この例では、 の<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティは<xref:System.Windows.Controls.Primitives.Popup>設定されません。 の既定値<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は です<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>。 <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 次の図は、<xref:System.Windows.Controls.Primitives.Popup>が<xref:System.Windows.Controls.Canvas>を基準にして配置されていることを示しています。  
  
 ![PlacementTarget がないポップアップ コントロール](./media/popup-placement-behavior/popup-placement-no-placement-target.png "配置ターゲットのないポップアップ。")  

 次の例では、<xref:System.Windows.Controls.Primitives.Popup>の子<xref:System.Windows.Controls.Canvas>である を作成しますが、今回<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>は`ellipse1`に設定されているので、ポップアップは の下<xref:System.Windows.Shapes.Ellipse>に表示されます。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 次の図は、<xref:System.Windows.Controls.Primitives.Popup>が<xref:System.Windows.Shapes.Ellipse>を基準にして配置されていることを示しています。  
  
 ![楕円を基準にして配置されるポップアップ](./media/popup-placement-behavior/popup-placement-with-placement-target.png "PlacementTarget があるポップアップ")
  
> [!NOTE]
> の<xref:System.Windows.Controls.ToolTip>場合、デフォルト値<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>です。  の<xref:System.Windows.Controls.ContextMenu>場合、デフォルト値<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>です。 これらの値については、後ほど「プロパティの連携のしくみ」で説明します。  
  
### <a name="target-area"></a>ターゲット領域  
 *ターゲット領域*は、画面上での相対的な領域<xref:System.Windows.Controls.Primitives.Popup>です。 前の例では、<xref:System.Windows.Controls.Primitives.Popup>はターゲット オブジェクトの境界に揃えられますが、ターゲット オブジェクトがある場合でも<xref:System.Windows.Controls.Primitives.Popup>、 が他の境界に揃えられる場合<xref:System.Windows.Controls.Primitives.Popup>があります。  プロパティが<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合、ターゲット領域はターゲット オブジェクトの境界と異なります。  
  
 次の例では、2 つの<xref:System.Windows.Controls.Canvas>オブジェクトを作成<xref:System.Windows.Shapes.Rectangle>し、<xref:System.Windows.Controls.Primitives.Popup>それぞれに を含む オブジェクトと を 1 つずつ含みます。  どちらの場合も、 の<xref:System.Windows.Controls.Primitives.Popup>ターゲット オブジェクトは<xref:System.Windows.Controls.Canvas>です。 最初<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Canvas>の の は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、セットを持<xref:System.Windows.Rect.X%2A>ち<xref:System.Windows.Rect.Y%2A>、<xref:System.Windows.Rect.Width%2A>プロパティ<xref:System.Windows.Rect.Height%2A>、、およびプロパティがそれぞれ 50、50、50、および 100 に設定されています。 2<xref:System.Windows.Controls.Primitives.Popup>番目<xref:System.Windows.Controls.Canvas>の のはセット<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>を持っていません。  その結果<xref:System.Windows.Controls.Primitives.Popup>、最初の要素は の<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>下に配置され<xref:System.Windows.Controls.Primitives.Popup>、2 番目<xref:System.Windows.Controls.Canvas>の要素は . それぞれに<xref:System.Windows.Controls.Canvas>は、最初<xref:System.Windows.Shapes.Rectangle><xref:System.Windows.Controls.Primitives.Popup>の の と同じ境界<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>を持つ が含まれています。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、アプリケーション内で可視要素を作成しません。この例では、<xref:System.Windows.Shapes.Rectangle>を表<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>す を作成します。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![PlacementRectangle がある (またはない) ポップアップ](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "配置長方形の有無にかかわらずポップアップ。")  

### <a name="target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイント  
 *ターゲットの始点*と*ポップアップ配置ポイント*は、それぞれターゲット領域とポップアップ上の基準点であり、配置に使用します。 プロパティと プロパティ<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>を使用して、ポップアップをターゲット領域からオフセットできます。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>ターゲットの<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>原点とポップアップ配置ポイントを基準にして、 と を基準にします。 プロパティの値によって<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、ターゲットの原点とポップアップの配置ポイントの位置が決まります。  
  
 を作成<xref:System.Windows.Controls.Primitives.Popup>し、 および<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティを 20 に設定する例を次に示します。  プロパティ<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は (既定値<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>) に設定されているので、ターゲットの原点はターゲット領域の左下隅、ポップアップ配置ポイントは<xref:System.Windows.Controls.Primitives.Popup>の左上隅です。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![ターゲットの始点の配置ポイントを含むポップアップ配置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "水平オフセットと垂直オフセットを持つポップアップ。")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>プロパティの連携のしくみ  
 の値 、 、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>および を一緒に考慮して、適切なターゲット領域、ターゲットの原点、ポップアップの配置ポイントを把握する必要があります。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>  たとえば、 の値<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>が<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>の場合、ターゲット オブジェクトは存在しません<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。 一方、が の<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>場合<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または 親はターゲット オブジェクト<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>を決定し、ターゲット領域を決定します。  
  
 次の表では、ターゲット オブジェクト、ターゲット領域、ターゲットの原点、ポップアップの配置ポイントについて説明し<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>各<xref:System.Windows.Controls.Primitives.PlacementMode>列挙値に使用するかどうか、および使用されるかどうかを示します。  
  
|PlacementMode|[対象になるオブジェクト]|ターゲット領域|ターゲットの始点|ポップアップ配置ポイント|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|適用不可。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> は無視されます。|画面、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>は画面に対して相対的です。|ターゲット領域の左上隅。|の左上隅です<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|適用不可。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> は無視されます。|画面、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>は画面に対して相対的です。|ターゲット領域の左上隅。|の左上隅です<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対値です。|ターゲット領域の左下隅。|の左上隅です<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対値です。|ターゲット領域の中央。|の中心<xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対値です。|によって定義されます<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|によって定義されます<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対値です。|ターゲット領域の左上隅。|の右上隅の<xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|適用不可。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> は無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> は無視されます。|ターゲット領域の左下隅。|の左上隅です<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|適用不可。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> は無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> は無視されます。|ターゲット領域の左上隅。|の左上隅です<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対値です。|ターゲット領域の左上隅。|の左上隅です<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対値です。|ターゲット領域の左上隅。|の左上隅です<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対値です。|ターゲット領域の右上隅。|の左上隅です<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対値です。|ターゲット領域の左上隅。|の左下隅。 <xref:System.Windows.Controls.Primitives.Popup>|  
  
 次の図は、各<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.PlacementMode>値の 、ターゲット領域、ターゲットの原点、およびポップアップの配置ポイントを示しています。 各図では、ターゲット領域は黄色、は青<xref:System.Windows.Controls.Primitives.Popup>です。  
  
 ![Absolute または AbsolutePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-absolute.png "配置は絶対点または絶対点です。")
  
 ![Bottom 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-bottom.png "配置は下です。")
  
 ![Center 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-center.png "配置は中央です。")
  
 ![Left 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-left.png "配置は左です。")
  
 ![Mouse 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-mouse.png "配置はマウスです。")  
  
 ![MousePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-mousepoint.png "配置はマウスポイントです。")  
  
 ![Relative または RelativePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-relative.png "配置は相対ポイントまたは相対点です。")
  
 ![Right 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-right.png "配置は正しい。")
  
 ![Top 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-top.png "配置は[上]です。")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>ポップアップが画面の端と重なった場合  
 セキュリティ上の理由から<xref:System.Windows.Controls.Primitives.Popup>、画面の端に を隠すことはできません。 画面の端が検出されると、次の<xref:System.Windows.Controls.Primitives.Popup>3 つのいずれかが発生します。  
  
- ポップアップは、画面の端に沿って自分自身を再調整し、. <xref:System.Windows.Controls.Primitives.Popup>  
  
- ポップアップは別のポップアップ配置ポイントを使用します。  
  
- ポップアップは別のターゲットの始点とポップアップ配置ポイントを使用します。  
  
 これらのオプションについては、このセクションの後半で詳しく説明します。  
  
 画面の端を<xref:System.Windows.Controls.Primitives.Popup>検出したときの動作は、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティの値とポップアップがどの画面エッジに遭遇するかによって異なります。 次の表は、値ごとに<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.PlacementMode>画面の端が検出された場合の動作をまとめたものです。  
  
|PlacementMode|上端|下端|左端|右端|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|上端に揃えます。|ポップアップの配置ポイントが、 の左下隅に<xref:System.Windows.Controls.Primitives.Popup>変わります。|左端に揃えます。|ポップアップの配置ポイントが、 の右上隅に<xref:System.Windows.Controls.Primitives.Popup>変わります。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|上端に揃えます。|ターゲットの原点がターゲット領域の左上隅に変わり、ポップアップの配置ポイントが<xref:System.Windows.Controls.Primitives.Popup>の左下隅に変わります。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|上端に揃えます。|下端に揃えます。|ターゲットの原点がターゲット領域の右上隅に変わり、ポップアップの配置ポイントが<xref:System.Windows.Controls.Primitives.Popup>の左上隅に変わります。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|上端に揃えます。|ターゲットの原点がターゲット領域の左上隅 (マウス ポインタの境界) に変わり、ポップアップの配置ポイントが<xref:System.Windows.Controls.Primitives.Popup>の左下隅に変わります。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|上端に揃えます。|ポップアップの配置ポイントが、 の左下隅に<xref:System.Windows.Controls.Primitives.Popup>変わります。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|上端に揃えます。|ポップアップの配置ポイントが、 の左下隅に<xref:System.Windows.Controls.Primitives.Popup>変わります。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|上端に揃えます。|下端に揃えます。|左端に揃えます。|ターゲットの原点がターゲット領域の左上隅に変わり、ポップアップの配置ポイントが<xref:System.Windows.Controls.Primitives.Popup>の右上隅に変わります。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|ターゲットの原点がターゲット領域の左下隅に変わり、ポップアップの配置ポイントが<xref:System.Windows.Controls.Primitives.Popup>の左上隅に変わります。 実際には、これは とき<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>と同じです<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
  
### <a name="aligning-to-the-screen-edge"></a>画面の端への配置  
 全体<xref:System.Windows.Controls.Primitives.Popup>が画面に表示されるように、自分自身を再配置することで、画面の<xref:System.Windows.Controls.Primitives.Popup>端に整列することができます。  この場合、ターゲットの原点とポップアップの配置ポイントの間の距離が、 および<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>の値と異なる場合があります。 <xref:System.Windows.Controls.Primitives.PlacementMode.Center><xref:System.Windows.Controls.Primitives.PlacementMode.Relative><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>が 、または の場合<xref:System.Windows.Controls.Primitives.Popup>は、画面の端ごとに位置合わせされます。 <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>  たとえば、 <xref:System.Windows.Controls.Primitives.Popup> a が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>100 に<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>設定されていると<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>します。  画面の下端で<xref:System.Windows.Controls.Primitives.Popup>の全体または一部が非表示になっている場合<xref:System.Windows.Controls.Primitives.Popup>、画面の下端に沿って再配置され、ターゲットの原点とポップアップの配置ポイント間の垂直距離は 100 未満になります。 これを次の図で示します。  
  
 ![画面の端に揃えて配置されたポップアップ](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "ポップアップは、画面の端に揃えて配置されます。")
  
### <a name="changing-the-popup-alignment-point"></a>ポップアップ配置ポイントの変更  
 が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、または<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>の場合、ポップアップの位置合わせポイントは、画面の下部または右端に表示されたときに変更されます。 <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint> <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>  
  
 次の図は、下の画面の端が の全体または一部を<xref:System.Windows.Controls.Primitives.Popup>非表示にしたときに、ポップアップ配置ポイントが<xref:System.Windows.Controls.Primitives.Popup>の左下隅であることを示しています。  
  
 ![画面の下端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "ポップアップは画面の下端に遭遇し、ポップアップの配置ポイントを変更します。")  

 次の図は、右画面の<xref:System.Windows.Controls.Primitives.Popup>端で 非表示になっている場合、ポップアップ配置ポイントが の右上隅であることを示しています<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の端による新しいポップアップ配置ポイント](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "ポップアップは画面の右端に表示され、ポップアップの配置ポイントが変更されます。")
  
 画面の<xref:System.Windows.Controls.Primitives.Popup>下部と右の端に遭遇した場合、ポップアップの配置ポイントは の右下隅になります<xref:System.Windows.Controls.Primitives.Popup>。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイントの変更  
 が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A><xref:System.Windows.Controls.Primitives.PlacementMode.Left> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、、、<xref:System.Windows.Controls.Primitives.PlacementMode.Right>または<xref:System.Windows.Controls.Primitives.PlacementMode.Top>、またはの場合、<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>特定の画面エッジが検出されると、ターゲットの原点とポップアップの配置ポイントが変化します。  位置を変更する画面の端は、<xref:System.Windows.Controls.Primitives.PlacementMode>値によって異なります。  
  
 次の図は、下の<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>画面<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>の端<xref:System.Windows.Controls.Primitives.Popup>が見つかった場合、ターゲットの原点がターゲット領域の左上隅、ポップアップ配置ポイントが の左下隅であることを示<xref:System.Windows.Controls.Primitives.Popup>しています。  
  
 ![画面の下端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "[配置] は [下] で、ポップアップは画面の下端に表示されます。")
  
 次<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>の図は<xref:System.Windows.Controls.Primitives.PlacementMode.Left>、左画面の端が<xref:System.Windows.Controls.Primitives.Popup>見つかった場合、ターゲットの原点がターゲット領域の右上隅、ポップアップ配置ポイントが の左上隅であることを示<xref:System.Windows.Controls.Primitives.Popup>しています。  
  
 ![画面の左端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "[配置] は [左] で、ポップアップは画面の左端に表示されます。")  
  
 次の図は、右画面<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>の<xref:System.Windows.Controls.Primitives.PlacementMode.Right>端が<xref:System.Windows.Controls.Primitives.Popup>見つかった場合、ターゲットの原点がターゲット領域の左上隅、ポップアップ配置ポイントが の右上隅であることを示<xref:System.Windows.Controls.Primitives.Popup>しています。  
  
 ![画面の右端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "配置が右、ポップアップが画面の右端に遭遇します。")  

 次の図は、上画面<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>の<xref:System.Windows.Controls.Primitives.PlacementMode.Top>端が<xref:System.Windows.Controls.Primitives.Popup>見つかった場合、ターゲットの原点がターゲット領域の左下隅、ポップアップ配置ポイントが の左上隅であることを示<xref:System.Windows.Controls.Primitives.Popup>しています。  
  
 ![画面の上端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "配置が [上] になり、ポップアップが画面の上端に表示されます。")  
  
 次<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>の図は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、下の画面の端<xref:System.Windows.Controls.Primitives.Popup>が見つかった場合、ターゲットの原点がターゲット領域の左上隅 (マウス ポインターの境界) であり、ポップアップ配置ポイントが の左下隅であることを示<xref:System.Windows.Controls.Primitives.Popup>しています。  
  
 ![画面の端に近いマウスによる新しい配置ポイント](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "配置はマウスで、ポップアップは画面の下端に遭遇します。")
  
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 ターゲットの原点とポップアップの配置ポイントをカスタマイズするには、プロパティを<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>に<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>設定します。 次に、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>可能な配置ポイントと基本軸のセットを (優先順に) 返すデリゲート<xref:System.Windows.Controls.Primitives.Popup>を定義します。 の最大部分を示す点<xref:System.Windows.Controls.Primitives.Popup>が選択されます。  の位置<xref:System.Windows.Controls.Primitives.Popup>は、画面の端に隠<xref:System.Windows.Controls.Primitives.Popup>れている場合に自動的に調整されます。 例については、「[方法 : ポップアップのカスタム位置を指定する](how-to-specify-a-custom-popup-position.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [ポップアップの配置のサンプル](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
