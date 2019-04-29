---
title: ポップアップの配置動作
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 911c2064e34ed8d0a341ffd9a52f852eab677e0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771320"
---
# <a name="popup-placement-behavior"></a>ポップアップの配置動作
A<xref:System.Windows.Controls.Primitives.Popup>コントロールは、アプリケーションから浮遊した別のウィンドウにコンテンツを表示します。 位置を指定することができます、<xref:System.Windows.Controls.Primitives.Popup>コントロール、マウス、またはを使用して画面を基準とした、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティ。  これらのプロパティが連携の位置を指定する柔軟性が得、<xref:System.Windows.Controls.Primitives.Popup>します。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ContextMenu>クラスはまたこれら 5 つのプロパティを定義して、同様に動作します。  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>ポップアップの配置  
 配置を<xref:System.Windows.Controls.Primitives.Popup>基準にすることができます、<xref:System.Windows.UIElement>または画面全体にします。  次の例では、4 つ作成します<xref:System.Windows.Controls.Primitives.Popup>の基準とするコントロールを<xref:System.Windows.UIElement>: この場合は、イメージにします。 すべての<xref:System.Windows.Controls.Primitives.Popup>コントロールが、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティに設定`image1`が各<xref:System.Windows.Controls.Primitives.Popup>placement プロパティの別の値を持ちます。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 次の図は、イメージ、<xref:System.Windows.Controls.Primitives.Popup>コントロール  
  
 ![4 つのポップアップ コントロールを持つイメージ](./media/popup-placement-behavior/popup-placement-intro.png "4 つのポップアップを持つイメージ")    
  
 この簡単な例は、設定する方法を示します、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>と<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを使用して、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティ、where より詳細に制御がある、<xref:System.Windows.Controls.Primitives.Popup>が配置されています。  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>用語の定義:ポップアップの構造  
 次の用語は理解に役立つ方法、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティが相互に関連付ける、 <xref:System.Windows.Controls.Primitives.Popup>:  
  
- ターゲット オブジェクト  
  
- ターゲット領域  
  
- ターゲットの始点  
  
- ポップアップ配置ポイント  
  
 これらの用語のさまざまな側面を参照する便利な手段を提供する、<xref:System.Windows.Controls.Primitives.Popup>とが関連付けられているコントロール。  
  
### <a name="target-object"></a>ターゲット オブジェクト  
 *ターゲット オブジェクト*要素ですが、<xref:System.Windows.Controls.Primitives.Popup>に関連付けられています。 場合、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティが設定されて、ターゲット オブジェクトを指定します。  場合<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>が設定されていないと、<xref:System.Windows.Controls.Primitives.Popup>親を持つ親がターゲット オブジェクト。  ある場合ありません<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>値と、親ターゲットのオブジェクトが存在しないと、<xref:System.Windows.Controls.Primitives.Popup>が画面を基準に配置されています。  
  
 次の例では、作成、<xref:System.Windows.Controls.Primitives.Popup>の子は、<xref:System.Windows.Controls.Canvas>します。  例は設定されていない、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティを<xref:System.Windows.Controls.Primitives.Popup>します。 既定値<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>であり、<xref:System.Windows.Controls.Primitives.Popup>下に表示されます、<xref:System.Windows.Controls.Canvas>します。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 次の図は、ことを示しています、<xref:System.Windows.Controls.Primitives.Popup>が相対的に配置される、<xref:System.Windows.Controls.Canvas>します。  
  
 ![Placementtarget がないポップアップ コントロール](./media/popup-placement-behavior/popup-placement-no-placement-target.png "placementtarget がないポップアップします。")  

 次の例では、作成、<xref:System.Windows.Controls.Primitives.Popup>の子は、 <xref:System.Windows.Controls.Canvas>、今回、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>に設定されている`ellipse1`下に、ポップアップが表示されますので、<xref:System.Windows.Shapes.Ellipse>します。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 次の図は、ことを示しています、<xref:System.Windows.Controls.Primitives.Popup>が相対的に配置される、<xref:System.Windows.Shapes.Ellipse>します。  
  
 ![楕円に相対的に配置されるポップアップ](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Placementtarget")    
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip>、既定値の<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>します。  <xref:System.Windows.Controls.ContextMenu>、既定値の<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>します。 これらの値については、後ほど「プロパティの連携のしくみ」で説明します。  
  
### <a name="target-area"></a>ターゲット領域  
 *ターゲット領域*が画面上の領域を<xref:System.Windows.Controls.Primitives.Popup>に相対的であります。 前の例で、<xref:System.Windows.Controls.Primitives.Popup>場合もありますが、対象のオブジェクトの境界に揃えて配置されます、<xref:System.Windows.Controls.Primitives.Popup>は他の境界に配置される場合でも、<xref:System.Windows.Controls.Primitives.Popup>ターゲット オブジェクトがあります。  場合、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>プロパティが設定されて、ターゲット領域がターゲット オブジェクトの境界と異なります。  
  
 次の例では、2 つ作成されます<xref:System.Windows.Controls.Canvas>オブジェクト、1 つを含む、<xref:System.Windows.Shapes.Rectangle>と<xref:System.Windows.Controls.Primitives.Popup>します。  どちらの場合で、ターゲット オブジェクトの<xref:System.Windows.Controls.Primitives.Popup>は、<xref:System.Windows.Controls.Canvas>します。 <xref:System.Windows.Controls.Primitives.Popup>最初<xref:System.Windows.Controls.Canvas>が、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>セットと、その<xref:System.Windows.Rect.X%2A>、 <xref:System.Windows.Rect.Y%2A>、<xref:System.Windows.Rect.Width%2A>と<xref:System.Windows.Rect.Height%2A>プロパティがそれぞれ 50、50、50 と 100 に設定します。 <xref:System.Windows.Controls.Primitives.Popup> 、2 番目の<xref:System.Windows.Controls.Canvas>はありません、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>を設定します。  その結果、最初の<xref:System.Windows.Controls.Primitives.Popup>の下にある、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、2 番目<xref:System.Windows.Controls.Primitives.Popup>下に配置されます、<xref:System.Windows.Controls.Canvas>します。 各<xref:System.Windows.Controls.Canvas>も含まれています、<xref:System.Windows.Shapes.Rectangle>と同じ境界を持つ、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、最初の<xref:System.Windows.Controls.Primitives.Popup>します。  なお、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>は、アプリケーションに表示される要素が作成されません例は、作成、<xref:System.Windows.Shapes.Rectangle>を表す、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>します。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![ポップアップ placementrectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "placementrectangle ポップアップします。")  

### <a name="target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイント  
 *ターゲットの始点*と*ポップアップ配置ポイント*は、それぞれターゲット領域とポップアップ上の基準点であり、配置に使用します。 使用することができます、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>ターゲット領域からポップアップをオフセットするプロパティ。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>は、ターゲットの始点とポップアップ配置ポイントを基準とします。 値、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティは、ターゲットの始点とポップアップ配置ポイントがある場所を決定します。  
  
 次の例では、作成、<xref:System.Windows.Controls.Primitives.Popup>設定と、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティを 20。  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティに設定されて<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>(既定)、ターゲットの始点がターゲット領域の左下隅にはそのためと、ポップアップ配置ポイントの左上隅にあるは、<xref:System.Windows.Controls.Primitives.Popup>します。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![ターゲットの始点の配置ポイントを含むポップアップ配置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "HorizontalOffset と verticaloffset があるポップアップします。")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>プロパティの連携のしくみ  
 値<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、および<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>適切なターゲット領域、ターゲットの始点とポップアップ配置ポイントを一緒に考慮する必要があります。  たとえば場合の値<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、対象のオブジェクトが存在しない、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>は無視されます、ターゲット領域は、マウス ポインターの境界とします。 その一方で場合、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親がターゲット オブジェクトを判断しますおよび<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット領域を決定します。  
  
 次の表は、ターゲット オブジェクト、ターゲット領域、ターゲットの始点とポップアップ配置ポイントについて説明し、示すかどうか<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>と<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>のそれぞれに使用<xref:System.Windows.Controls.Primitives.PlacementMode>列挙値。  
  
|PlacementMode|ターゲット オブジェクト|ターゲット領域|ターゲットの始点|ポップアップ配置ポイント|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|該当なし。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 無視されます。|画面または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>画面に対する相対パスです。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|該当なし。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 無視されます。|画面または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>画面に対する相対パスです。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対パスです。|ターゲット領域の左下隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対パスです。|ターゲット領域の中央。|中央、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対パスです。|によって定義されている、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>します。|によって定義されている、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|右上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|該当なし。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 無視されます。|ターゲット領域の左下隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|該当なし。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 無視されます。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対パスです。|ターゲット領域の右上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクト、または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ターゲット オブジェクトに対する相対パスです。|ターゲット領域の左上隅。|左下隅、<xref:System.Windows.Controls.Primitives.Popup>します。|  
  
 次の図に示す、 <xref:System.Windows.Controls.Primitives.Popup>、ターゲット領域、ターゲットの始点とポップアップ配置ポイントの各<xref:System.Windows.Controls.Primitives.PlacementMode>値。 各図では、ターゲット領域は黄色、および<xref:System.Windows.Controls.Primitives.Popup>は青色です。  
  
 ![Absolute または AbsolutePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-absolute.png "Placement が Absolute または AbsolutePoint します。")    
  
 ![Bottom 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-bottom.png "Placement が Bottom です。")   
  
 ![Center 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-center.png "Placement が Center。")    
  
 ![Left 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-left.png "Placement が Left。")   
  
 ![Mouse 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-mouse.png "Placement が Mouse します。")  
  
 ![MousePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-mousepoint.png "Placement が MousePoint します。")  
  
 ![Relative または RelativePoint 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-relative.png "Placement が Relative または RelativePoint します。")    
  
 ![Right 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-right.png "Placement が Right。")    
  
 ![Top 配置を含むポップアップ](./media/popup-placement-behavior/popup-placement-top.png "Placement が Top です。")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>ポップアップが画面の端と重なった場合  
 セキュリティ上の理由から、<xref:System.Windows.Controls.Primitives.Popup>画面の端で非表示にすることはできません。 次の 3 つのいずれかが発生時に、<xref:System.Windows.Controls.Primitives.Popup>で画面の端が発生しました。  
  
- ポップアップ揃うように隠れないよう、画面の端に沿って、<xref:System.Windows.Controls.Primitives.Popup>します。  
  
- ポップアップは別のポップアップ配置ポイントを使用します。  
  
- ポップアップは別のターゲットの始点とポップアップ配置ポイントを使用します。  
  
 これらのオプションについては、このセクションの後半で詳しく説明します。  
  
 動作、<xref:System.Windows.Controls.Primitives.Popup>画面の端がの値に依存を検出すると、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>画面の端を検出すると、ポップアップにプロパティとします。 次の表は、動作をまとめたものです。 ときに、<xref:System.Windows.Controls.Primitives.Popup>各画面の端を検出すると<xref:System.Windows.Controls.Primitives.PlacementMode>値。  
  
|PlacementMode|上端|下端|左端|右端|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|上端に揃えます。|左下隅、ポップアップ配置ポイントに変更、<xref:System.Windows.Controls.Primitives.Popup>します。|左端に揃えます。|右上隅に、ポップアップ配置ポイントの変更、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|上端に揃えます。|ターゲットの始点がターゲット領域の左上隅に変更し、ポップアップ配置ポイントの左下隅に変更、<xref:System.Windows.Controls.Primitives.Popup>します。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|上端に揃えます。|下端に揃えます。|ターゲットの始点がターゲット領域の右上隅に変更し、ポップアップ配置ポイントの左上隅に変更、<xref:System.Windows.Controls.Primitives.Popup>します。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|上端に揃えます。|ターゲットの始点がターゲット領域 (マウス ポインターの境界) の左上隅に変更し、ポップアップ配置ポイントの左下隅に変更、<xref:System.Windows.Controls.Primitives.Popup>します。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|上端に揃えます。|左下隅、ポップアップ配置ポイントに変更、<xref:System.Windows.Controls.Primitives.Popup>します。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|上端に揃えます。|左下隅、ポップアップ配置ポイントに変更、<xref:System.Windows.Controls.Primitives.Popup>します。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|上端に揃えます。|下端に揃えます。|左端に揃えます。|ターゲットの始点がターゲット領域の左上隅に変更し、ポップアップ配置ポイントの右上隅に変更、<xref:System.Windows.Controls.Primitives.Popup>します。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|ターゲットの始点がターゲット領域の左下隅に変更し、ポップアップ配置ポイントの左上隅に変更、<xref:System.Windows.Controls.Primitives.Popup>します。 これは、有効な場合と同じ<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>します。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
  
### <a name="aligning-to-the-screen-edge"></a>画面の端への配置  
 A<xref:System.Windows.Controls.Primitives.Popup>揃えることが、画面の端にため再配置して全体<xref:System.Windows.Controls.Primitives.Popup>が画面に表示されます。  値からターゲットの始点とポップアップ配置ポイント間の距離が異なる場合がありますこのとき、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>します。 ときに<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>、 <xref:System.Windows.Controls.Primitives.PlacementMode.Center>、または<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>、<xref:System.Windows.Controls.Primitives.Popup>各画面端に揃えて配置します。  たとえば、ある、<xref:System.Windows.Controls.Primitives.Popup>が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>に設定<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>を 100 に設定します。  画面の下端の全部または一部を非表示にする場合、 <xref:System.Windows.Controls.Primitives.Popup>、<xref:System.Windows.Controls.Primitives.Popup>自体を再配置、画面とターゲットの始点とポップアップの縦方向の距離の下端に沿って配置ポイントが 100 よりも小さいが。 これを次の図で示します。  
  
 ![画面の端に配置されるポップアップ](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "ポップアップが画面の端に揃えて配置します。")    
  
### <a name="changing-the-popup-alignment-point"></a>ポップアップ配置ポイントの変更  
 場合<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>、 <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>、または<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>、ポップアップ配置ポイントが、ポップアップが下または画面の右端に変更します。  
  
 次の図は、ことを示しますの全部または一部が画面の下端に非表示にすると、 <xref:System.Windows.Controls.Primitives.Popup>、ポップアップ配置ポイントの左下隅は、<xref:System.Windows.Controls.Primitives.Popup>します。  
  
 ![画面の下端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "ポップアップが画面の下端を検出し、ポップアップ配置ポイントを変更します。")  

 次の図は、する場合を示しています、<xref:System.Windows.Controls.Primitives.Popup>が非表示、ポップアップ配置ポイントの右上隅にあるの画面の右端で、<xref:System.Windows.Controls.Primitives.Popup>します。  
  
 ![画面の端による新しいポップアップ配置ポイント](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "ポップアップが画面の右端を検出し、ポップアップ配置ポイントを変更します。")    
  
 場合、<xref:System.Windows.Controls.Primitives.Popup>下および右の画面の端を検出すると、ポップアップ配置ポイントは、の右下隅、<xref:System.Windows.Controls.Primitives.Popup>します。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイントの変更  
 ときに<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、 <xref:System.Windows.Controls.Primitives.PlacementMode.Left>、 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、 <xref:System.Windows.Controls.Primitives.PlacementMode.Right>、または<xref:System.Windows.Controls.Primitives.PlacementMode.Top>、特定の画面の端が発生した場合、ターゲットの始点とポップアップ配置ポイントが変更されます。  画面の端の位置の変更の原因となるによって異なります、<xref:System.Windows.Controls.Primitives.PlacementMode>値。  
  
 次の図は、する場合を示しています<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>と<xref:System.Windows.Controls.Primitives.Popup>、画面の下端が発生したターゲットの始点がターゲット領域の左上隅にあると、ポップアップ配置ポイントの左下隅のは<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の下端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Placement が Bottom で、ポップアップが画面の下端。")    
  
 次の図に示す時に<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Left>と<xref:System.Windows.Controls.Primitives.Popup>画面の左端を検出したターゲットの基準は対象となる領域の右上隅にある、ポップアップ配置ポイント、の左上隅にあります<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の左端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Placement が Left と、ポップアップが画面の左端。")  
  
 次の図は、する場合を示しています<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Right>、<xref:System.Windows.Controls.Primitives.Popup>画面の右端を検出すると、ターゲットの始点がターゲット領域の左上隅にあると、ポップアップ配置ポイントの右上隅にあるのは<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の右端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Placement が Right と、ポップアップが画面の右端。")  

 次の図は、する場合を示しています<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Top>、<xref:System.Windows.Controls.Primitives.Popup>画面の上端を検出すると、ターゲットの始点がターゲット領域の左下隅と、ポップアップ配置ポイントの左上隅にあるのは<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の上端による新しい配置ポイント](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Placement が Top と、ポップアップが画面の上端。")  
  
 次の図は、する場合を示しています<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>と<xref:System.Windows.Controls.Primitives.Popup>、画面の下端が検出したターゲットの始点がターゲット領域 (マウス ポインターの境界) とポップアップの配置の左上隅にある。ポイントの左下隅は、<xref:System.Windows.Controls.Primitives.Popup>します。  
  
 ![画面の端に近いマウスによる新しい配置ポイント](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Placement が Mouse で、ポップアップが画面の下端。")    
  
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 設定して、ターゲットの始点とポップアップ配置ポイントをカスタマイズすることができます、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>します。 定義し、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>の一連の可能な配置ポイントとプライマリ軸を (優先順) を返すデリゲート、<xref:System.Windows.Controls.Primitives.Popup>します。 ポイントの最大部分を示す、<xref:System.Windows.Controls.Primitives.Popup>が選択されています。  位置、<xref:System.Windows.Controls.Primitives.Popup>場合に自動的に調整、<xref:System.Windows.Controls.Primitives.Popup>画面の端で非表示になります。 例については、「[方法 : ポップアップのカスタム位置を指定する](how-to-specify-a-custom-popup-position.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [ポップアップの配置のサンプル](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
