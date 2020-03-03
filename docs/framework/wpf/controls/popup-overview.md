---
title: ポップアップの概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 7e6977737d362fd0df6321702bb8a1ac6cad66e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951429"
---
# <a name="popup-overview"></a>ポップアップの概要
コントロール<xref:System.Windows.Controls.Primitives.Popup>は、指定された要素または画面座標を基準として、現在のアプリケーションウィンドウにフローティングする別のウィンドウにコンテンツを表示する方法を提供します。 このトピックでは<xref:System.Windows.Controls.Primitives.Popup> 、コントロールについて説明し、その使用方法について説明します。  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>ポップアップとは  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>は、画面上の要素またはポイントを基準にして、コンテンツを別のウィンドウに表示します。 が表示されると`true`、プロパティはに設定されます。<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> <xref:System.Windows.Controls.Primitives.Popup>  
  
> [!NOTE]
> マウス<xref:System.Windows.Controls.Primitives.Popup>ポインターが親オブジェクトの上に移動しても、は自動的には開きません。 を自動的に開く<xref:System.Windows.Controls.ToolTipService> <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.Primitives.Popup>ようにする場合は、クラスまたはクラスを使用します。 詳細については、[ToolTip の概要](tooltip-overview.md)を参照してください。  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>ポップアップの作成  
 次の例は、 <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Button>コントロールの子要素であるコントロールを定義する方法を示しています。 は<xref:System.Windows.Controls.Button>子要素を1つしか持つことができないため、この例<xref:System.Windows.Controls.Button>では<xref:System.Windows.Controls.Primitives.Popup> 、のテキスト<xref:System.Windows.Controls.StackPanel>とコントロールをに配置します。 の<xref:System.Windows.Controls.Primitives.Popup>内容が<xref:System.Windows.Controls.TextBlock>コントロールに表示され、関連<xref:System.Windows.Controls.Button>するコントロールの近くにあるアプリケーションウィンドウにフローティングする別のウィンドウにテキストが表示されます。  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>ポップアップを実装するコントロール  
 コントロールを他<xref:System.Windows.Controls.Primitives.Popup>のコントロールに組み込むことができます。 次のコントロールは、 <xref:System.Windows.Controls.Primitives.Popup>特定の用途のためにコントロールを実装します。  
  
- <xref:System.Windows.Controls.ToolTip>。 要素のツールヒントを作成する場合は、クラス<xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ToolTipService>クラスを使用します。 詳細については、[ToolTip の概要](tooltip-overview.md)を参照してください。  
  
- <xref:System.Windows.Controls.ContextMenu>。 要素のコンテキストメニューを作成する場合は、 <xref:System.Windows.Controls.ContextMenu>コントロールを使用します。 詳細については、[ContextMenu の概要](contextmenu-overview.md)を参照してください。  
  
- <xref:System.Windows.Controls.ComboBox>。 表示または非表示にできるドロップダウンリストボックスがある選択コントロールを作成する場合は、 <xref:System.Windows.Controls.ComboBox>コントロールを使用します。  
  
- <xref:System.Windows.Controls.Expander>。 コンテンツを表示する折りたたみ可能な領域を含むヘッダーを表示するコントロールを作成する場合は、 <xref:System.Windows.Controls.Expander>コントロールを使用します。 詳細については、 [Expander の概要](expander-overview.md)を参照してください。  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>ポップアップの動作と外観  
 <xref:System.Windows.Controls.Primitives.Popup>コントロールには、動作と外観をカスタマイズできる機能が用意されています。 たとえば、[開始] と [終了] の動作、アニメーション、不透明度とビットマップ効果<xref:System.Windows.Controls.Primitives.Popup> 、およびサイズと位置を設定できます。  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>オープンとクローズの動作  
 プロパティ<xref:System.Windows.Controls.Primitives.Popup>がに設定されて<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>いる場合、コントロール`true`はその内容を表示します。 既定では<xref:System.Windows.Controls.Primitives.Popup> 、プロパティがに<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> `false`設定されるまで、は開いたままになります。 ただし、 <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A>プロパティをに`false`設定すると、既定の動作を変更できます。 このプロパティをに`false`設定すると<xref:System.Windows.Controls.Primitives.Popup> 、コンテンツウィンドウにマウスキャプチャが表示されます。 で<xref:System.Windows.Controls.Primitives.Popup>マウスのキャプチャが失われ、 <xref:System.Windows.Controls.Primitives.Popup>ウィンドウの外側でマウスイベントが発生すると、ウィンドウが閉じます。  
  
 イベントとイベント<xref:System.Windows.Controls.Primitives.Popup.Closed>は、コンテンツウィンドウが開いているとき、または閉じたときに発生します。<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Opened>  
  
<a name="Animation"></a>   
### <a name="animation"></a>アニメーション  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>には、通常、フェードインやスライドインなどの動作に関連付けられているアニメーションのサポートが組み込まれています。 プロパティを<xref:System.Windows.Controls.Primitives.PopupAnimation>列挙値に設定することに<xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A>よって、これらのアニメーションを有効にすることができます。 アニメーションが正常に機能するには、 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティをに`true`設定する必要があります。 <xref:System.Windows.Controls.Primitives.Popup>  
  
 また、の<xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.Primitives.Popup>ようなアニメーションをコントロールに適用することもできます。  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>不透明度とビットマップ効果  
 コントロールのプロパティは、 <xref:System.Windows.UIElement.Opacity%2A>そのコンテンツには影響しません。 <xref:System.Windows.Controls.Primitives.Popup> 既定では、 <xref:System.Windows.Controls.Primitives.Popup>コンテンツウィンドウは不透明です。 透過<xref:System.Windows.Controls.Primitives.Popup>を作成するには、 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`に設定します。  
  
 の<xref:System.Windows.Controls.Primitives.Popup>コンテンツは、 <xref:System.Windows.Controls.Primitives.Popup>コントロールまたは親ウィンドウの他の<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>要素に直接設定したなどのビットマップ効果を継承しません。 ビットマップ効果がの<xref:System.Windows.Controls.Primitives.Popup>コンテンツに表示されるようにするには、ビットマップ効果をそのコンテンツに対して直接設定する必要があります。 たとえば、の<xref:System.Windows.Controls.Primitives.Popup>子<xref:System.Windows.Controls.StackPanel>がである場合は、に<xref:System.Windows.Controls.StackPanel>ビットマップ効果を設定します。  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>ポップアップのサイズ  
 既定では、 <xref:System.Windows.Controls.Primitives.Popup>はそのコンテンツに合わせて自動的にサイズ変更されます。 自動サイズ変更が発生した場合、 <xref:System.Windows.Controls.Primitives.Popup>コンテンツに対して定義されている画面領域の既定のサイズによってビットマップ効果を表示するための十分な領域が提供されないため、一部のビットマップ効果が非表示になることがあります。  
  
 <xref:System.Windows.Controls.Primitives.Popup>コンテンツにを設定すると、 <xref:System.Windows.UIElement.RenderTransform%2A>コンテンツが隠されることもあります。 このシナリオでは、変換<xref:System.Windows.Controls.Primitives.Popup>されたの内容が元<xref:System.Windows.Controls.Primitives.Popup>の領域を超えている場合、一部のコンテンツが非表示になることがあります。 ビットマップ効果または変換でより多くの領域が必要な場合は、コントロール<xref:System.Windows.Controls.Primitives.Popup>により多くの領域を提供するために、コンテンツの周りに余白を定義することができます。  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>ポップアップ位置の定義  
 ポップアップを配置するには<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、、、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および<xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty>の各プロパティを設定します。 詳細については、「[ポップアップの配置動作](popup-placement-behavior.md)」を参照してください。 <xref:System.Windows.Controls.Primitives.Popup>が画面に表示されている場合、親の位置が変更されても、その位置は再配置されません。  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 を表示する<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>位置<xref:System.Windows.Controls.Primitives.Popup>を基準とする座標のセットを指定することによって、コントロールの配置をカスタマイズできます。  
  
 配置をカスタマイズするには<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 、プロパティ<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>をに設定します。 次に、 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> <xref:System.Windows.Controls.Primitives.Popup>の一連の可能な配置ポイントと主軸 (優先順) を返すデリゲートを定義します。 の最大部分を示すポイント<xref:System.Windows.Controls.Primitives.Popup>が自動的に選択されます。 例については、「[方法 : ポップアップのカスタム位置を指定する](how-to-specify-a-custom-popup-position.md)」をご覧ください。  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>ポップアップとビジュアル ツリー  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>は、独自のビジュアルツリーを持ちません。の<xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> <xref:System.Windows.Controls.Primitives.Popup>メソッドが呼び出されたときに、代わりにサイズ 0 (ゼロ) を返します。 ただし、の<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティをに`true`設定する<xref:System.Windows.Controls.Primitives.Popup>と、独自のビジュアルツリーを持つ新しいウィンドウが作成されます。 新しいウィンドウには、 <xref:System.Windows.Controls.Primitives.Popup.Child%2A>の<xref:System.Windows.Controls.Primitives.Popup>内容が表示されます。 新しいウィンドウの幅および高さは、画面の幅または高さの 75% より大きくすることはできません。  
  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>は、その<xref:System.Windows.Controls.Primitives.Popup.Child%2A>コンテンツへの参照を論理上の子として保持します。 新しいウィンドウが作成されると、の<xref:System.Windows.Controls.Primitives.Popup>コンテンツはウィンドウのビジュアル子になり、の論理上の<xref:System.Windows.Controls.Primitives.Popup>子のままになります。 逆に<xref:System.Windows.Controls.Primitives.Popup> 、は、その<xref:System.Windows.Controls.Primitives.Popup.Child%2A>内容の論理的な親のままです。  
  
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
