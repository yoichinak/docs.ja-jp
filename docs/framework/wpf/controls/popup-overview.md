---
title: ポップアップの概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 53283619d1bd2727bdca1df6a3a408ec0ce873a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625709"
---
# <a name="popup-overview"></a>ポップアップの概要
<xref:System.Windows.Controls.Primitives.Popup>コントロールには、指定された要素や画面座標を基準と現在のアプリケーション ウィンドウから浮遊した別のウィンドウの内容を表示する方法が用意されています。 このトピックでは、<xref:System.Windows.Controls.Primitives.Popup>を制御し、その使用方法についての情報を提供します。  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>ポップアップとは  
 A<xref:System.Windows.Controls.Primitives.Popup>要素または画面上のポイントを基準とした別のウィンドウでコントロールがコンテンツを表示します。 ときに、<xref:System.Windows.Controls.Primitives.Popup>が表示されて、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティに設定されて`true`します。  
  
> [!NOTE]
>  A<xref:System.Windows.Controls.Primitives.Popup>その親オブジェクトの上にマウス ポインターが移動したときに自動的に開くはありません。 場合は、<xref:System.Windows.Controls.Primitives.Popup>自動的に開くを使用して、<xref:System.Windows.Controls.ToolTip>または<xref:System.Windows.Controls.ToolTipService>クラス。 詳細については、[ToolTip の概要](tooltip-overview.md)を参照してください。  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>ポップアップの作成  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.Primitives.Popup>の子要素であるコントロール、<xref:System.Windows.Controls.Button>コントロール。 <xref:System.Windows.Controls.Button>子要素の 1 つだけ持つことができます、この例のテキストの配置、<xref:System.Windows.Controls.Button>と<xref:System.Windows.Controls.Primitives.Popup>でコントロールを<xref:System.Windows.Controls.StackPanel>します。 コンテンツ、<xref:System.Windows.Controls.Primitives.Popup>に表示されます、<xref:System.Windows.Controls.TextBlock>近く、関連のアプリケーション ウィンドウから浮遊した別のウィンドウでそのテキストを表示するコントロール<xref:System.Windows.Controls.Button>コントロール。  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>ポップアップを実装するコントロール  
 ビルドすることができます<xref:System.Windows.Controls.Primitives.Popup>他のコントロールにコントロール。 次のコントロールの実装、<xref:System.Windows.Controls.Primitives.Popup>特定の使用目的。  
  
- <xref:System.Windows.Controls.ToolTip>。 要素のツールヒントを作成する場合を使用して、<xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ToolTipService>クラス。 詳細については、[ToolTip の概要](tooltip-overview.md)を参照してください。  
  
- <xref:System.Windows.Controls.ContextMenu>。 要素のコンテキスト メニューを作成する場合は、使用、<xref:System.Windows.Controls.ContextMenu>コントロール。 詳細については、[ContextMenu の概要](contextmenu-overview.md)を参照してください。  
  
- <xref:System.Windows.Controls.ComboBox>。 または、非表示に使用できるドロップダウン リスト ボックスのある選択コントロールを作成する場合、<xref:System.Windows.Controls.ComboBox>コントロール。  
  
- <xref:System.Windows.Controls.Expander>。 コンテンツを表示する折りたたみ可能な領域を持つヘッダーを表示するコントロールを作成する場合、使用、<xref:System.Windows.Controls.Expander>コントロール。 詳細については、 [Expander の概要](expander-overview.md)を参照してください。  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>ポップアップの動作と外観  
 <xref:System.Windows.Controls.Primitives.Popup>コントロールには、その動作と外観をカスタマイズできるようにする機能が用意されています。 たとえば、オープンとクローズの動作、アニメーション、不透明度とビットマップ効果を設定し、<xref:System.Windows.Controls.Primitives.Popup>サイズと位置。  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>オープンとクローズの動作  
 A<xref:System.Windows.Controls.Primitives.Popup>コントロールは、そのコンテンツを表示します。 ときに、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティに設定されて`true`します。 既定では、<xref:System.Windows.Controls.Primitives.Popup>まで開いたまま、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティに設定されて`false`します。 ただし、既定の動作を設定して変更できます、<xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A>プロパティを`false`します。 このプロパティ設定すると`false`、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ ウィンドウがマウスのキャプチャ。 <xref:System.Windows.Controls.Primitives.Popup>外部マウス イベントが発生したときにマウスをキャプチャをウィンドウが閉じますに失い、<xref:System.Windows.Controls.Primitives.Popup>ウィンドウ。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened>と<xref:System.Windows.Controls.Primitives.Popup.Closed>イベントが発生したときに、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ ウィンドウが開くまたは閉じる。  
  
<a name="Animation"></a>   
### <a name="animation"></a>アニメーション  
 <xref:System.Windows.Controls.Primitives.Popup>コントロールは通常、フェードインとスライドインのような動作に関連付けられているアニメーションの組み込みサポートしています。 これらのアニメーションをオンに設定して、<xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A>プロパティを<xref:System.Windows.Controls.Primitives.PopupAnimation>列挙値。 <xref:System.Windows.Controls.Primitives.Popup>アニメーションが正常に動作を設定する必要があります、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`します。  
  
 ようなアニメーションを適用することもできます。<xref:System.Windows.Media.Animation.Storyboard>を、<xref:System.Windows.Controls.Primitives.Popup>コントロール。  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>不透明度とビットマップ効果  
 <xref:System.Windows.UIElement.Opacity%2A>プロパティを<xref:System.Windows.Controls.Primitives.Popup>コントロールがそのコンテンツに影響を与えません。 既定で、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ ウィンドウは非透過的です。 透過的なを作成する<xref:System.Windows.Controls.Primitives.Popup>、設定、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`します。  
  
 コンテンツを<xref:System.Windows.Controls.Primitives.Popup>など、ビットマップ効果を継承しません<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>、直接を設定することで、<xref:System.Windows.Controls.Primitives.Popup>コントロールまたは親ウィンドウ内の他の要素でします。 コンテンツを表示するビットマップ効果を<xref:System.Windows.Controls.Primitives.Popup>、そのコンテンツに直接ビットマップ効果を設定する必要があります。 たとえば場合の子、<xref:System.Windows.Controls.Primitives.Popup>は、<xref:System.Windows.Controls.StackPanel>でビットマップ効果を設定、<xref:System.Windows.Controls.StackPanel>します。  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>ポップアップのサイズ  
 既定で、<xref:System.Windows.Controls.Primitives.Popup>そのコンテンツのサイズは自動的にします。 ため、自動サイズ調整が発生したときに一部のビットマップ効果が表示されないことに定義されている画面の領域の既定のサイズ、<xref:System.Windows.Controls.Primitives.Popup>コンテンツがビットマップ効果を表示するための十分な領域を提供していません。  
  
 <xref:System.Windows.Controls.Primitives.Popup> 設定すると、コンテンツを隠されることも、<xref:System.Windows.UIElement.RenderTransform%2A>内容にします。 このシナリオで一部のコンテンツが非表示になるコンテンツの変換された<xref:System.Windows.Controls.Primitives.Popup>、元の領域からはみ出して拡大<xref:System.Windows.Controls.Primitives.Popup>します。 ビットマップ効果または変換より多くの領域が必要とする場合は、周囲に余白を定義することができます、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ コントロールの領域を提供するためにします。  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>ポップアップ位置の定義  
 ポップアップを配置するには、設定、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および<xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty>プロパティ。 詳細については、「[Popup Placement Behavior](popup-placement-behavior.md)」を参照してください。 ときに<xref:System.Windows.Controls.Primitives.Popup>表示される画面で、これが再配置されない場合、その親の位置します。  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 配置をカスタマイズすることができます、<xref:System.Windows.Controls.Primitives.Popup>コントロールに対する相対座標のセットを指定することによって、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>先、<xref:System.Windows.Controls.Primitives.Popup>を表示します。  
  
 配置をカスタマイズする設定、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>します。 定義し、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>の一連の可能な配置ポイントとプライマリ軸を (優先順) を返すデリゲート、<xref:System.Windows.Controls.Primitives.Popup>します。 ポイントの最大部分を示している<xref:System.Windows.Controls.Primitives.Popup>が自動的に選択します。 例については、「[方法 : ポップアップのカスタム位置を指定する](how-to-specify-a-custom-popup-position.md)」をご覧ください。  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>ポップアップとビジュアル ツリー  
 A<xref:System.Windows.Controls.Primitives.Popup>コントロールには、独自のビジュアル ツリーはありません。 代わりに、サイズ 0 を返します、(0)、<xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A>メソッド<xref:System.Windows.Controls.Primitives.Popup>が呼び出されます。 ただし、設定、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティの<xref:System.Windows.Controls.Primitives.Popup>に`true`、独自のビジュアル ツリーを新しいウィンドウが作成されます。 新しいウィンドウには、<xref:System.Windows.Controls.Primitives.Popup.Child%2A>のコンテンツ<xref:System.Windows.Controls.Primitives.Popup>します。 新しいウィンドウの幅および高さは、画面の幅または高さの 75% より大きくすることはできません。  
  
 <xref:System.Windows.Controls.Primitives.Popup>コントロールへの参照を保持する、<xref:System.Windows.Controls.Primitives.Popup.Child%2A>論理上の子としてコンテンツ。 新しいウィンドウが作成されたとき、コンテンツの<xref:System.Windows.Controls.Primitives.Popup>、ウィンドウのビジュアルの子になり、論理上の子を引き続き<xref:System.Windows.Controls.Primitives.Popup>します。 逆に、<xref:System.Windows.Controls.Primitives.Popup>の論理上の親のままその<xref:System.Windows.Controls.Primitives.Popup.Child%2A>コンテンツ。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [方法トピック](popup-how-to-topics.md)
- [方法トピック](tooltip-how-to-topics.md)
