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
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "69951732"
---
# <a name="popup-placement-behavior"></a>ポップアップの配置動作
@No__t_0 コントロールは、アプリケーションにフローティングする別のウィンドウにコンテンツを表示します。 @No__t_1、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> の各プロパティを使用して、コントロール、マウス、または画面を基準とした <xref:System.Windows.Controls.Primitives.Popup> の位置を指定できます。  これらのプロパティは、<xref:System.Windows.Controls.Primitives.Popup> の位置を柔軟に指定できるように連携します。  
  
> [!NOTE]
> また、<xref:System.Windows.Controls.ToolTip> クラスと <xref:System.Windows.Controls.ContextMenu> クラスもこれらの5つのプロパティを定義し、同様に動作します。  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>ポップアップの配置  
 @No__t_0 の配置は、<xref:System.Windows.UIElement> または画面全体に対して相対的に行うことができます。  次の例では、<xref:System.Windows.UIElement> (この場合はイメージ) に対して相対的な4つの <xref:System.Windows.Controls.Primitives.Popup> コントロールを作成します。 すべての <xref:System.Windows.Controls.Primitives.Popup> コントロールには、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> プロパティが `image1` に設定されていますが、各 <xref:System.Windows.Controls.Primitives.Popup> の配置プロパティの値が異なります。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 次の図は、イメージと <xref:System.Windows.Controls.Primitives.Popup> コントロールを示しています。  
  
 ![4 つのポップアップ コントロールを含む画像](./media/popup-placement-behavior/popup-placement-intro.png "4つのポップアップを含むイメージ")    
  
 この簡単な例では、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> と <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> のプロパティを設定する方法を示していますが、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> の各プロパティを使用して、<xref:System.Windows.Controls.Primitives.Popup> の配置場所をさらに細かく制御することができます。  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>用語の定義: ポップアップの構造  
 @No__t_0、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> の各プロパティが相互にどのように関連しているかを理解するには、次の用語が役立ちます。  
  
- ターゲット オブジェクト  
  
- ターゲット領域  
  
- ターゲットの始点  
  
- ポップアップ配置ポイント  
  
 これらの用語は、<xref:System.Windows.Controls.Primitives.Popup> とそれに関連付けられているコントロールのさまざまな側面を参照する便利な方法を提供します。  
  
### <a name="target-object"></a>ターゲット オブジェクト  
 *ターゲットオブジェクト*は、<xref:System.Windows.Controls.Primitives.Popup> が関連付けられている要素です。 @No__t_0 プロパティが設定されている場合は、対象のオブジェクトを指定します。  @No__t_0 が設定されておらず、<xref:System.Windows.Controls.Primitives.Popup> に親がある場合、親はターゲットオブジェクトです。  @No__t_0 値がなく、親も存在しない場合、ターゲットオブジェクトはなく、<xref:System.Windows.Controls.Primitives.Popup> は画面の相対位置に配置されます。  
  
 次の例では、<xref:System.Windows.Controls.Canvas> の子である <xref:System.Windows.Controls.Primitives.Popup> を作成します。  この例では、<xref:System.Windows.Controls.Primitives.Popup> の <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> プロパティは設定しません。 @No__t_0 の既定値は <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType> であるため、<xref:System.Windows.Controls.Canvas> の下に <xref:System.Windows.Controls.Primitives.Popup> が表示されます。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 次の図は、<xref:System.Windows.Controls.Primitives.Popup> が <xref:System.Windows.Controls.Canvas> に対して相対的に配置されていることを示しています。  
  
 ![PlacementTarget がないポップアップ コントロール](./media/popup-placement-behavior/popup-placement-no-placement-target.png "ショートカットがありません。")  

 次の例では、<xref:System.Windows.Controls.Canvas> の子である <xref:System.Windows.Controls.Primitives.Popup> を作成しますが、今度は <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> を `ellipse1` に設定します。そのため、ポップアップは <xref:System.Windows.Shapes.Ellipse> の下に表示されます。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 次の図は、<xref:System.Windows.Controls.Primitives.Popup> が <xref:System.Windows.Shapes.Ellipse> に対して相対的に配置されていることを示しています。  
  
 ![楕円を基準にして配置されるポップアップ](./media/popup-placement-behavior/popup-placement-with-placement-target.png "PlacementTarget があるポップアップ")    
  
> [!NOTE]
> @No__t_0 の場合、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> の既定値は <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> です。  @No__t_0 の場合、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> の既定値は <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> です。 これらの値については、後ほど「プロパティの連携のしくみ」で説明します。  
  
### <a name="target-area"></a>ターゲット領域  
 *ターゲット領域*は、画面上の <xref:System.Windows.Controls.Primitives.Popup> の基準となる領域です。 前の例では、<xref:System.Windows.Controls.Primitives.Popup> はターゲットオブジェクトの境界に合わせて調整されますが、場合によっては、<xref:System.Windows.Controls.Primitives.Popup> に対象オブジェクトがある場合でも、<xref:System.Windows.Controls.Primitives.Popup> が他の境界に合わせてアラインされます。  @No__t_0 プロパティが設定されている場合、ターゲット領域はターゲットオブジェクトの境界とは異なります。  
  
 次の例では、<xref:System.Windows.Shapes.Rectangle> と <xref:System.Windows.Controls.Primitives.Popup> を含む2つの <xref:System.Windows.Controls.Canvas> オブジェクトを作成します。  どちらの場合も、<xref:System.Windows.Controls.Primitives.Popup> のターゲットオブジェクトは <xref:System.Windows.Controls.Canvas> です。 最初の <xref:System.Windows.Controls.Canvas> の <xref:System.Windows.Controls.Primitives.Popup> には <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> が設定されており、それぞれ <xref:System.Windows.Rect.X%2A>、<xref:System.Windows.Rect.Y%2A>、<xref:System.Windows.Rect.Width%2A>、および <xref:System.Windows.Rect.Height%2A> の各プロパティが50、50、50、100に設定されています。 2番目の <xref:System.Windows.Controls.Canvas> の <xref:System.Windows.Controls.Primitives.Popup> には <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> が設定されていません。  その結果、最初の <xref:System.Windows.Controls.Primitives.Popup> は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> の下に配置され、2番目の <xref:System.Windows.Controls.Primitives.Popup> は <xref:System.Windows.Controls.Canvas> の下に配置されます。 各 <xref:System.Windows.Controls.Canvas> には、最初の <xref:System.Windows.Controls.Primitives.Popup> の <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> と同じ境界を持つ <xref:System.Windows.Shapes.Rectangle> も含まれます。  @No__t_0 では、アプリケーションに表示される要素は作成されないことに注意してください。この例では、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> を表す <xref:System.Windows.Shapes.Rectangle> を作成します。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![PlacementRectangle がある (またはない) ポップアップ](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "ショートカットの有無を含むポップアップ。")  

### <a name="target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイント  
 *ターゲットの始点*と*ポップアップ配置ポイント*は、それぞれターゲット領域とポップアップ上の基準点であり、配置に使用します。 @No__t_0 と <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> のプロパティを使用して、ターゲット領域からポップアップをオフセットできます。  @No__t_0 と <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> は、ターゲットの始点とポップアップの配置ポイントを基準としています。 @No__t_0 プロパティの値によって、ターゲットの元とポップアップの配置ポイントが配置されている場所が決まります。  
  
 次の例では、<xref:System.Windows.Controls.Primitives.Popup> を作成し、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> と <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> のプロパティを20に設定します。  @No__t_0 プロパティが <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (既定値) に設定されているため、ターゲットの起点はターゲット領域の左下隅、ポップアップ配置ポイントは <xref:System.Windows.Controls.Primitives.Popup> の左上隅になります。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![ターゲットの始点の配置ポイントを含むポップアップ配置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "System.windows.controls.primitives.iscrollinfo.horizontaloffset と System.windows.controls.primitives.popup.verticaloffset を使用したポップアップ。")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>プロパティの連携のしくみ  
 @No__t_0、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、および <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> の値は、正しいターゲット領域、ターゲットの始点、およびポップアップ配置ポイントを確認するために、まとめて考慮する必要があります。  たとえば、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> の値が <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> である場合、対象オブジェクトが存在せず、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> が無視され、ターゲット領域がマウスポインターの境界になります。 一方、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> が <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 場合、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親によって対象オブジェクトが決定され、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ターゲット領域が決まります。  
  
 次の表では、ターゲットオブジェクト、ターゲット領域、ターゲットの始点、およびポップアップの配置ポイントについて説明し、<xref:System.Windows.Controls.Primitives.PlacementMode> 列挙値ごとに <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> と <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> を使用するかどうかを示します。  
  
|PlacementMode|ターゲット オブジェクト|ターゲット領域|ターゲットの始点|ポップアップ配置ポイント|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|該当しない。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> は無視されます。|画面。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は画面に対して相対的です。|ターゲット領域の左上隅。|@No__t_0 の左上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|該当しない。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> は無視されます。|画面。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は画面に対して相対的です。|ターゲット領域の左上隅。|@No__t_0 の左上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親。|ターゲットオブジェクト。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は、対象オブジェクトに対する相対パスです。|ターゲット領域の左下隅。|@No__t_0 の左上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親。|ターゲットオブジェクト。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は、対象オブジェクトに対する相対パスです。|ターゲット領域の中央。|@No__t_0 の中心。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親。|ターゲットオブジェクト。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は、対象オブジェクトに対する相対パスです。|@No__t_0 によって定義されます。|@No__t_0 によって定義されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親。|ターゲットオブジェクト。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は、対象オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|@No__t_0 の右上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|該当しない。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> は無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> は無視されます。|ターゲット領域の左下隅。|@No__t_0 の左上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|該当しない。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> は無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> は無視されます。|ターゲット領域の左上隅。|@No__t_0 の左上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親。|ターゲットオブジェクト。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は、対象オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|@No__t_0 の左上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親。|ターゲットオブジェクト。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は、対象オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|@No__t_0 の左上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親。|ターゲットオブジェクト。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は、対象オブジェクトに対する相対パスです。|ターゲット領域の右上隅。|@No__t_0 の左上隅。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または親。|ターゲットオブジェクト。設定されている場合は <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 は、対象オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|@No__t_0 の左下隅。|  
  
 次の図は、各 <xref:System.Windows.Controls.Primitives.PlacementMode> 値の <xref:System.Windows.Controls.Primitives.Popup>、ターゲット領域、ターゲットの始点、およびポップアップの配置ポイントを示しています。 各図では、ターゲット領域は黄色、<xref:System.Windows.Controls.Primitives.Popup> は青です。  
  
 ![Absolute または AbsolutePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-absolute.png "Placement は Absolute または AbsolutePoint です。")    
  
 ![Bottom 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-bottom.png "Placement は Bottom です。")   
  
 ![Center 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-center.png "Placement は Center です。")    
  
 ![Left 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-left.png "配置は残されています。")   
  
 ![Mouse 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-mouse.png "Placement は Mouse です。")  
  
 ![MousePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-mousepoint.png "配置は MousePoint です。")  
  
 ![Relative または RelativePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-relative.png "Placement は相対または RelativePoint です。")    
  
 ![Right 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-right.png "Placement は Right です。")    
  
 ![Top 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-top.png "Placement は Top です。")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>ポップアップが画面の端と重なった場合  
 セキュリティ上の理由により、<xref:System.Windows.Controls.Primitives.Popup> を画面の端で非表示にすることはできません。 @No__t_0 が画面の端に達すると、次の3つのいずれかが発生します。  
  
- ポップアップは、<xref:System.Windows.Controls.Primitives.Popup> が見えなくなる画面の端に沿って再配置されます。  
  
- ポップアップは別のポップアップ配置ポイントを使用します。  
  
- ポップアップは別のターゲットの始点とポップアップ配置ポイントを使用します。  
  
 これらのオプションについては、このセクションの後半で詳しく説明します。  
  
 画面の端が検出されたときの <xref:System.Windows.Controls.Primitives.Popup> の動作は、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> プロパティの値とポップアップが検出する画面の端によって異なります。 次の表は、<xref:System.Windows.Controls.Primitives.Popup> が各 <xref:System.Windows.Controls.Primitives.PlacementMode> 値に対して画面の端を検出した場合の動作をまとめたものです。  
  
|PlacementMode|上端|下端|左端|右端|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|上端に揃えます。|ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左下隅に変わります。|左端に揃えます。|ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の右上隅に変わります。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|上端に揃えます。|ターゲットのオリジンがターゲット領域の左上隅に変わり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左下隅に変わります。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|上端に揃えます。|下端に揃えます。|ターゲットの原点がターゲット領域の右上隅に変わり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左上隅に変わります。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|上端に揃えます。|ターゲットの原点が、ターゲット領域の左上隅 (マウスポインターの境界) に変わり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左下隅に変わりますが、|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|上端に揃えます。|ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左下隅に変わります。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|上端に揃えます。|ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左下隅に変わります。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|上端に揃えます。|下端に揃えます。|左端に揃えます。|ターゲットのオリジンがターゲット領域の左上隅に変わり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の右上隅に変わります。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|ターゲットのオリジンがターゲット領域の左下隅に変わり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左上隅に変わります。 実際には、これは <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> が <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 場合と同じです。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
  
### <a name="aligning-to-the-screen-edge"></a>画面の端への配置  
 @No__t_1 全体が画面上に表示されるように、<xref:System.Windows.Controls.Primitives.Popup> を画面の端に合わせることができます。  この場合、ターゲットの始点とポップアップの配置ポイント間の距離は、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> と <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> の値とは異なる場合があります。 @No__t_0 が <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>、<xref:System.Windows.Controls.Primitives.PlacementMode.Center>、または <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> の場合、<xref:System.Windows.Controls.Primitives.Popup> はすべての画面の端に配置されます。  たとえば、<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> が <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> に設定され、<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> が100に設定されているとします。  画面の下端が <xref:System.Windows.Controls.Primitives.Popup> の一部または一部を非表示にした場合、<xref:System.Windows.Controls.Primitives.Popup> は画面の下端に沿って再配置され、ターゲットの始点とポップアップの配置ポイントの間の垂直方向の距離は100未満になります。 これを次の図で示します。  
  
 ![画面の端に揃えて配置されたポップアップ](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "ポップアップが画面の端に揃えて配置されます。")    
  
### <a name="changing-the-popup-alignment-point"></a>ポップアップ配置ポイントの変更  
 @No__t_0 が <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>、<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>、または <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> の場合、ポップアップが画面の下端または右端で検出されるとポップアップの配置ポイントが変わります。  
  
 次の図は、下部画面の端が <xref:System.Windows.Controls.Primitives.Popup> の一部または一部を非表示にしたときに、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左下隅にあることを示しています。  
  
 ![画面の下端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "ポップアップが画面の下端に表示され、ポップアップ配置ポイントが変更されます。")  

 次の図は、<xref:System.Windows.Controls.Primitives.Popup> が右側の画面の端で非表示になっている場合、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の右上隅にあることを示しています。  
  
 ![画面の端による新しいポップアップ配置ポイント](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "ポップアップが画面の右端に表示され、ポップアップの配置ポイントが変更されます。")    
  
 @No__t_0 が一番下と右の画面の端に達すると、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の右下隅になります。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイントの変更  
 @No__t_0 が <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、<xref:System.Windows.Controls.Primitives.PlacementMode.Left>、<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、<xref:System.Windows.Controls.Primitives.PlacementMode.Right>、または <xref:System.Windows.Controls.Primitives.PlacementMode.Top> の場合、特定の画面の端が検出されると、ターゲットの元とポップアップの配置ポイントが変更されます。  位置を変更する画面の端は、<xref:System.Windows.Controls.Primitives.PlacementMode> の値によって異なります。  
  
 次の図は、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> が <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、<xref:System.Windows.Controls.Primitives.Popup> が下部画面の端に到達した場合に、ターゲットの原点がターゲット領域の左上隅にあり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左下隅にあることを示しています。  
  
 ![画面の下端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "位置が Bottom で、ポップアップが画面の下端に表示されます。")    
  
 次の図は、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> が <xref:System.Windows.Controls.Primitives.PlacementMode.Left>、<xref:System.Windows.Controls.Primitives.Popup> が左端の画面の端に達すると、ターゲットの原点がターゲット領域の右上隅にあり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左上隅にあることを示しています。  
  
 ![画面の左端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "配置が左になり、ポップアップが画面の左端に表示されます。")  
  
 次の図は、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> が <xref:System.Windows.Controls.Primitives.PlacementMode.Right>、<xref:System.Windows.Controls.Primitives.Popup> が正しい画面の端を検出した場合に、ターゲットの原点がターゲット領域の左上隅にあり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の右上隅であることを示しています。  
  
 ![画面の右端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Placement が Right で、ポップアップが画面の右端に表示されます。")  

 次の図は、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> が <xref:System.Windows.Controls.Primitives.PlacementMode.Top>、<xref:System.Windows.Controls.Primitives.Popup> が一番上の画面の端に達すると、ターゲットの原点がターゲット領域の左下隅にあり、ポップアップの配置ポイントが <xref:System.Windows.Controls.Primitives.Popup> の左上隅にあることを示しています。  
  
 ![画面の上端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Placement が Top で、ポップアップが画面の上端に表示されます。")  
  
 次の図は、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> が <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、<xref:System.Windows.Controls.Primitives.Popup> が下部画面の端に達すると、ターゲット領域の左上隅 (マウスポインターの境界) であり、ポップアップ配置ポイントが左下になっていることを示しています。<xref:System.Windows.Controls.Primitives.Popup> のコーナー。  
  
 ![画面の端に近いマウスによる新しい配置ポイント](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "位置がマウスで、ポップアップが画面の下端に表示されます。")    
  
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 [@No__t_0] プロパティを [<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>] に設定すると、ターゲットの始点とポップアップの配置ポイントをカスタマイズできます。 次に、<xref:System.Windows.Controls.Primitives.Popup> に対して可能な配置ポイントと主軸 (優先順) のセットを返す <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> デリゲートを定義します。 @No__t_0 の最大部分を示すポイントが選択されています。  @No__t_1 が画面の端で非表示になっている場合、<xref:System.Windows.Controls.Primitives.Popup> の位置は自動的に調整されます。 例については、「[カスタム ポップアップの位置を指定する](how-to-specify-a-custom-popup-position.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ポップアップの配置のサンプル](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
