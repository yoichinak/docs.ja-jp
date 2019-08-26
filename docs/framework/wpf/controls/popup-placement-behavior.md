---
title: ポップアップの配置動作
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: ca984aa724cf3f076d6073aa8b8179abfb91d26c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951732"
---
# <a name="popup-placement-behavior"></a>ポップアップの配置動作
コントロール<xref:System.Windows.Controls.Primitives.Popup>は、アプリケーションにフローティングする別のウィンドウにコンテンツを表示します。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup> 、、、およびの各プロパティを使用して、コントロール、マウス、または画面に対して相対的なの位置を指定できます。<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>  これらのプロパティは、 <xref:System.Windows.Controls.Primitives.Popup>の位置を柔軟に指定できるように連携して機能します。  
  
> [!NOTE]
> また<xref:System.Windows.Controls.ToolTip> 、 <xref:System.Windows.Controls.ContextMenu>クラスとクラスは、これらの5つのプロパティを定義し、同様に動作します。  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>ポップアップの配置  
 の<xref:System.Windows.Controls.Primitives.Popup>配置は、 <xref:System.Windows.UIElement>または画面全体に対して相対的に行うことができます。  次の例では<xref:System.Windows.Controls.Primitives.Popup> 、 <xref:System.Windows.UIElement>(この場合はイメージ) に対して相対的な4つのコントロールを作成します。 すべての<xref:System.Windows.Controls.Primitives.Popup>コントロールには、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティがに`image1`設定され<xref:System.Windows.Controls.Primitives.Popup>ていますが、それぞれの配置プロパティの値が異なります。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 次の図は、イメージと<xref:System.Windows.Controls.Primitives.Popup>コントロールを示しています。  
  
 ![4 つのポップアップコントロールを含むイメージ](./media/popup-placement-behavior/popup-placement-intro.png "4 つのポップアップを含むイメージ")    
  
 この簡単な例では、プロパティ<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>と<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを設定する方法を<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>示してい<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>ますが、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、、 <xref:System.Windows.Controls.Primitives.Popup>およびの各プロパティを使用すると、が配置されている場所をより細かく制御できます。  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>用語の定義:ポップアップの構造  
 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>の各<xref:System.Windows.Controls.Primitives.Popup>プロパティが相互にどのように関連しているかを理解するには、次の用語が役立ちます。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>  
  
- ターゲット オブジェクト  
  
- ターゲット領域  
  
- ターゲットの始点  
  
- ポップアップ配置ポイント  
  
 これらの用語は、 <xref:System.Windows.Controls.Primitives.Popup>とそれに関連付けられているコントロールのさまざまな側面を参照するための便利な方法を提供します。  
  
### <a name="target-object"></a>ターゲット オブジェクト  
 *ターゲットオブジェクト*は、 <xref:System.Windows.Controls.Primitives.Popup>が関連付けられている要素です。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティが設定されている場合は、対象のオブジェクトを指定します。  が<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 設定<xref:System.Windows.Controls.Primitives.Popup>されておらず、に親がある場合、親はターゲットオブジェクトです。  値がなく<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 、親も存在しない場合、対象オブジェクト<xref:System.Windows.Controls.Primitives.Popup>はなく、は画面に対して相対的に配置されます。  
  
 <xref:System.Windows.Controls.Primitives.Popup> 次<xref:System.Windows.Controls.Canvas>の例では、の子であるを作成します。  この例では、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup>でプロパティを設定しません。 の<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>既定値は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>であるため<xref:System.Windows.Controls.Primitives.Popup> 、はの<xref:System.Windows.Controls.Canvas>下に表示されます。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 次の図は、 <xref:System.Windows.Controls.Primitives.Popup>が<xref:System.Windows.Controls.Canvas>に対して相対的に配置されていることを示しています。  
  
 ![移動操作がないポップアップコントロール](./media/popup-placement-behavior/popup-placement-no-placement-target.png "ショートカットがありません。")  

 次の例では<xref:System.Windows.Controls.Primitives.Popup> 、 <xref:System.Windows.Controls.Canvas>の子であるを作成しますが、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>今回はに`ellipse1`設定されるため、ポップアップは<xref:System.Windows.Shapes.Ellipse>の下に表示されます。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 次の図は、 <xref:System.Windows.Controls.Primitives.Popup>が<xref:System.Windows.Shapes.Ellipse>に対して相対的に配置されていることを示しています。  
  
 ![楕円の相対位置に配置されたポップアップ](./media/popup-placement-behavior/popup-placement-with-placement-target.png "ショートカットターゲットを含むポップアップ")    
  
> [!NOTE]
> の既定<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>値は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>です。 <xref:System.Windows.Controls.ToolTip>  の既定<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>値は<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>です。 <xref:System.Windows.Controls.ContextMenu> これらの値については、後ほど「プロパティの連携のしくみ」で説明します。  
  
### <a name="target-area"></a>ターゲット領域  
 *ターゲット領域*は、 <xref:System.Windows.Controls.Primitives.Popup>が基準とする画面上の領域です。 前の例<xref:System.Windows.Controls.Primitives.Popup>では、はターゲットオブジェクトの境界に合わせてアラインされていますが<xref:System.Windows.Controls.Primitives.Popup> 、にはターゲットオブジェクトがある場合<xref:System.Windows.Controls.Primitives.Popup>でも、が他の境界にアラインされている場合があります。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>プロパティが設定されている場合、ターゲット領域はターゲットオブジェクトの境界とは異なります。  
  
 次の例では<xref:System.Windows.Controls.Canvas> 、 <xref:System.Windows.Shapes.Rectangle>と<xref:System.Windows.Controls.Primitives.Popup>を含む2つのオブジェクトを作成します。  どちらの場合も、のターゲットオブジェクト<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>はです。 最初<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Rect.Width%2A> <xref:System.Windows.Rect.Height%2A> <xref:System.Windows.Rect.Y%2A>ののは、セットを持ち、、 <xref:System.Windows.Rect.X%2A>、、およびの各プロパティはそれぞれ50、50、50、100に設定されています。 <xref:System.Windows.Controls.Canvas> 2番目<xref:System.Windows.Controls.Canvas>の<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>には、セットがありません。 <xref:System.Windows.Controls.Primitives.Popup>  <xref:System.Windows.Controls.Primitives.Popup>その結果、最初のはの<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>下に配置され、 <xref:System.Windows.Controls.Primitives.Popup> 2 番目の<xref:System.Windows.Controls.Canvas>はの下に配置されます。 また<xref:System.Windows.Controls.Canvas> 、それぞれ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>に<xref:System.Windows.Shapes.Rectangle>は、最初<xref:System.Windows.Controls.Primitives.Popup>のと同じ境界を持つが含まれています。  は、アプリケーション<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>に表示される要素を作成しないことに注意して<xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ください。この例では、を表すを作成します。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![ショートカットの有無を含むポップアップ](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "ショートカットの有無を含むポップアップ。")  

### <a name="target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイント  
 *ターゲットの始点*と*ポップアップ配置ポイント*は、それぞれターゲット領域とポップアップ上の基準点であり、配置に使用します。 プロパティ<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティを使用して、ターゲット領域からポップアップをオフセットできます。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>は、ターゲットの起点とポップアップの配置ポイントを基準としています。 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティの値によって、ターゲットの元とポップアップの配置ポイントが配置されている場所が決まります。  
  
 次の例では<xref:System.Windows.Controls.Primitives.Popup> 、を作成<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>し<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 、プロパティとプロパティを20に設定します。  プロパティが (既定値<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ) に設定されているため、ターゲットの起点はターゲット領域の左下隅、ポップアップ配置ポイントはの左上隅<xref:System.Windows.Controls.Primitives.Popup>になります。 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![ターゲットの配信元の配置ポイントを含むポップアップ配置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "System.windows.controls.primitives.iscrollinfo.horizontaloffset と system.windows.controls.primitives.popup.verticaloffset を使用したポップアップ。")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>プロパティの連携のしくみ  
 、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>およびの値は、正しいターゲット領域、ターゲットの始点、およびポップアップ配置ポイントを確認するために、まとめて考慮する必要<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>があります。  たとえば、の<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>値が<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>である場合、対象オブジェクトが存在<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>せず、が無視され、ターゲット領域がマウスポインターの境界になります。 一方<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 、が<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>の場合、または親はターゲットオブジェクトを決定し、ターゲット領域を決定します。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>  
  
 次の表では、ターゲットオブジェクト、ターゲット領域、ターゲットの始点、およびポップアップの配置ポイント<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>に<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ついて説明し<xref:System.Windows.Controls.Primitives.PlacementMode> 、各列挙値にとが使用されるかどうかを示します。  
  
|PlacementMode|ターゲット オブジェクト|ターゲット領域|ターゲットの始点|ポップアップ配置ポイント|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|適用できません。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>は無視されます。|画面。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、画面に対して相対的です。|ターゲット領域の左上隅。|の左上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|適用できません。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>は無視されます。|画面。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、画面に対して相対的です。|ターゲット領域の左上隅。|の左上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲットオブジェクト。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、対象オブジェクトに対する相対パスです。|ターゲット領域の左下隅。|の左上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲットオブジェクト。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、対象オブジェクトに対する相対パスです。|ターゲット領域の中央。|の<xref:System.Windows.Controls.Primitives.Popup>中央。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲットオブジェクト。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、対象オブジェクトに対する相対パスです。|によっ<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>て定義されます。|によっ<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>て定義されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲットオブジェクト。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、対象オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|の右上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|適用できません。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>は無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>は無視されます。|ターゲット領域の左下隅。|の左上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|適用できません。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>は無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>は無視されます。|ターゲット領域の左上隅。|の左上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲットオブジェクト。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、対象オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|の左上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲットオブジェクト。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、対象オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|の左上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲットオブジェクト。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、対象オブジェクトに対する相対パスです。|ターゲット領域の右上隅。|の左上隅<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親。|ターゲットオブジェクト。設定さ<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>れている場合は。  は<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、対象オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|の左下隅<xref:System.Windows.Controls.Primitives.Popup>。|  
  
 次の図は、 <xref:System.Windows.Controls.Primitives.Popup>各<xref:System.Windows.Controls.Primitives.PlacementMode>値の、ターゲット領域、ターゲットの始点、およびポップアップの配置ポイントを示しています。 各図形では、ターゲット領域は黄色、 <xref:System.Windows.Controls.Primitives.Popup>は青になります。  
  
 ![Absolute または AbsolutePoint placement を使用したポップアップ](./media/popup-placement-behavior/popup-placement-absolute.png "Placement は Absolute または AbsolutePoint です。")    
  
 ![下に配置]されるポップアップ(./media/popup-placement-behavior/popup-placement-bottom.png "Placement は Bottom です。")   
  
 ![中央配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-center.png "Placement は Center です。")    
  
 ![左側の配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-left.png "配置は残されています。")   
  
 ![マウスの配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-mouse.png "Placement は Mouse です。")  
  
 ![MousePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-mousepoint.png "配置は MousePoint です。")  
  
 ![相対または RelativePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-relative.png "Placement は相対または RelativePoint です。")    
  
 ![右側の配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-right.png "Placement は Right です。")    
  
 ![Top 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-top.png "Placement は Top です。")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>ポップアップが画面の端と重なった場合  
 セキュリティ上の理由から<xref:System.Windows.Controls.Primitives.Popup> 、を画面の端で非表示にすることはできません。 次の3つのうちの1つ<xref:System.Windows.Controls.Primitives.Popup>は、が画面の端に遭遇したときに発生します。  
  
- ポップアップは、が<xref:System.Windows.Controls.Primitives.Popup>見えなくなる画面の端に沿って再配置されます。  
  
- ポップアップは別のポップアップ配置ポイントを使用します。  
  
- ポップアップは別のターゲットの始点とポップアップ配置ポイントを使用します。  
  
 これらのオプションについては、このセクションの後半で詳しく説明します。  
  
 画面の端が<xref:System.Windows.Controls.Primitives.Popup>検出されたときの動作は、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティの値とポップアップが検出する画面の端によって異なります。 次の表は、が各<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.PlacementMode>値に対して画面の端を検出した場合の動作をまとめたものです。  
  
|PlacementMode|上端|下端|左端|右端|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|上端に揃えます。|ポップアップ配置ポイントがの<xref:System.Windows.Controls.Primitives.Popup>左下隅に変わります。|左端に揃えます。|ポップアップ配置ポイントがの右上隅<xref:System.Windows.Controls.Primitives.Popup>に変わります。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|上端に揃えます。|ターゲットの原点が、ターゲット領域の左上隅に変わり、ポップアップ配置ポイントがの左下隅<xref:System.Windows.Controls.Primitives.Popup>に変わります。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|上端に揃えます。|下端に揃えます。|ターゲットの原点が、ターゲット領域の右上隅に変わり、ポップアップ配置ポイントがの<xref:System.Windows.Controls.Primitives.Popup>左上隅に変わります。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|上端に揃えます。|ターゲットの原点が、 <xref:System.Windows.Controls.Primitives.Popup>ターゲット領域の左上隅 (マウスポインターの境界) に変わり、ポップアップの配置ポイントがの左下隅に変わりますが、|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|上端に揃えます。|ポップアップ配置ポイントがの<xref:System.Windows.Controls.Primitives.Popup>左下隅に変わります。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|上端に揃えます。|ポップアップ配置ポイントがの<xref:System.Windows.Controls.Primitives.Popup>左下隅に変わります。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|上端に揃えます。|下端に揃えます。|左端に揃えます。|ターゲットの原点が、ターゲット領域の左上隅に変わり、ポップアップ配置ポイントがの右上隅<xref:System.Windows.Controls.Primitives.Popup>に変わります。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|ターゲットの原点が、ターゲット領域の左下隅に変わり、ポップアップ配置ポイントがの左上隅<xref:System.Windows.Controls.Primitives.Popup>に変わります。 実際には、は、が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>の場合と同じです。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
  
### <a name="aligning-to-the-screen-edge"></a>画面の端への配置  
 は<xref:System.Windows.Controls.Primitives.Popup> 、画面上に全体<xref:System.Windows.Controls.Primitives.Popup>が表示されるように再配置することで、画面の端に合わせることができます。  この場合、ターゲットの始点とポップアップの配置ポイント間の距離は、およびの<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>値と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>異なる場合があります。 が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute> 、また<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>はの場合<xref:System.Windows.Controls.Primitives.Popup> 、はすべての画面の端に合わせて配置されます。 <xref:System.Windows.Controls.Primitives.PlacementMode.Center>  たとえば、 <xref:System.Windows.Controls.Primitives.Popup>がに<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>設定され、が100に設定されているとします。<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>  画面の下端がのすべてまたは一部<xref:System.Windows.Controls.Primitives.Popup>を非表示にすると、は<xref:System.Windows.Controls.Primitives.Popup>画面の下端に沿って再配置され、ターゲットの始点とポップアップの配置ポイントの間の垂直方向の距離は100未満になります。 これを次の図で示します。  
  
 ![画面の端に揃えて配置されるポップアップ](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "ポップアップが画面の端に揃えて配置されます。")    
  
### <a name="changing-the-popup-alignment-point"></a>ポップアップ配置ポイントの変更  
 が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint> <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>、またはの場合、ポップアップが下または右の画面の端に達すると、ポップアップ配置ポイントが変更されます。 <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>  
  
 次の図は、下部画面の端がのすべてまたは一部<xref:System.Windows.Controls.Primitives.Popup>を非表示にしたときに、ポップアップ配置ポイントがの左下隅<xref:System.Windows.Controls.Primitives.Popup>にあることを示しています。  
  
 ![画面の下端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "ポップアップが画面の下端に表示され、ポップアップ配置ポイントが変更されます。")  

 次の図は、が右側<xref:System.Windows.Controls.Primitives.Popup>の画面の端で非表示になっている場合に、ポップアップ配置ポイントが<xref:System.Windows.Controls.Primitives.Popup>の右上隅であることを示しています。  
  
 ![画面の端による新しいポップアップ配置ポイント](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "ポップアップが画面の右端に表示され、ポップアップの配置ポイントが変更されます。")    
  
 が<xref:System.Windows.Controls.Primitives.Popup>下と右の画面の端を検出した場合、ポップアップの配置ポイントは<xref:System.Windows.Controls.Primitives.Popup>の右下隅になります。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイントの変更  
 が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 、 、、、また<xref:System.Windows.Controls.Primitives.PlacementMode.Left> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>はの場合、特定の画面の端が検出されると、ターゲットの原点とポップアップの配置ポイントが変更されます。<xref:System.Windows.Controls.Primitives.PlacementMode.Top> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> <xref:System.Windows.Controls.Primitives.PlacementMode.Right>  位置を変更する画面の端は、 <xref:System.Windows.Controls.Primitives.PlacementMode>値によって異なります。  
  
 次の図は、が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> <xref:System.Windows.Controls.Primitives.Popup>で下部画面の端を検出したときに、ターゲットの始点がターゲット領域の左上隅にあり、ポップアップ配置ポイントがの左下隅にあることを示しています<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の下端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "位置が bottom で、ポップアップが画面の下端に表示されます。")    
  
 次の図に示す時に<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Left>と<xref:System.Windows.Controls.Primitives.Popup>画面の左端を検出したターゲットの基準は対象となる領域の右上隅にある、ポップアップ配置ポイント、の左上隅にあります<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の左端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "配置が左になり、ポップアップが画面の左端に表示されます。")  
  
 次の図は、が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>で<xref:System.Windows.Controls.Primitives.PlacementMode.Right> 、 <xref:System.Windows.Controls.Primitives.Popup>が正しい画面の端を検出した場合に、ターゲットの始点がターゲット領域の左上隅にあり、ポップアップ配置ポイントがの右上隅であることを示しています<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の右端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Placement が right で、ポップアップが画面の右端に表示されます。")  

 次の図は、が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> <xref:System.Windows.Controls.Primitives.Popup>で一番上の画面の端を検出したときに、ターゲットの原点がターゲット領域の左下隅にあり、ポップアップ配置ポイントがの左上隅にあることを示しています<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の上端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Placement が top で、ポップアップが画面の上端に表示されます。")  
  
 次の図は、が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> <xref:System.Windows.Controls.Primitives.Popup>で下部画面の端を検出した場合に、ターゲット領域 (マウスポインターの境界) とポップアップの配置の左上隅にあることを示しています。point はの<xref:System.Windows.Controls.Primitives.Popup>左下隅です。  
  
 ![画面の端に近いマウスによる新しい配置ポイント](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "位置がマウスで、ポップアップが画面の下端に表示されます。")    
  
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティをに設定する<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>ことによって、ターゲットの始点とポップアップ配置ポイントをカスタマイズできます。 次に、 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> <xref:System.Windows.Controls.Primitives.Popup>の一連の可能な配置ポイントと主軸 (優先順) を返すデリゲートを定義します。 の最大部分を示すポイント<xref:System.Windows.Controls.Primitives.Popup>が選択されています。  が画面の端<xref:System.Windows.Controls.Primitives.Popup>で非表示になっ<xref:System.Windows.Controls.Primitives.Popup>ている場合、の位置は自動的に調整されます。 例については、「[方法 : ポップアップのカスタム位置を指定する](how-to-specify-a-custom-popup-position.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [ポップアップの配置のサンプル](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
