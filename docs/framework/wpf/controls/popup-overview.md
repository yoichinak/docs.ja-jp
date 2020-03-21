---
title: ポップアップの概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 911130d52744c5ba54750f214829a5d1900e083c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185949"
---
# <a name="popup-overview"></a>ポップアップの概要
コントロール<xref:System.Windows.Controls.Primitives.Popup>は、指定された要素または画面座標に対して現在のアプリケーション ウィンドウの上に浮かぶ別のウィンドウにコンテンツを表示する方法を提供します。 このトピックでは、<xref:System.Windows.Controls.Primitives.Popup>コントロールについて説明し、その使用方法に関する情報を提供します。  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>ポップアップとは  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>は、画面上の要素またはポイントに対して相対的に別のウィンドウにコンテンツを表示します。 が<xref:System.Windows.Controls.Primitives.Popup>表示されている場合、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティは に`true`設定されます。  
  
> [!NOTE]
> A<xref:System.Windows.Controls.Primitives.Popup>は、マウス ポインターがその親オブジェクトの上に移動しても自動的には開きません。 を<xref:System.Windows.Controls.Primitives.Popup>自動的に開く場合は、 または<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.ToolTipService>クラスを使用します。 詳細については、[ToolTip の概要](tooltip-overview.md)を参照してください。  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>ポップアップの作成  
 コントロールの子要素であるコントロールを<xref:System.Windows.Controls.Primitives.Popup>定義する方法を次の例に<xref:System.Windows.Controls.Button>示します。 子要素<xref:System.Windows.Controls.Button>は 1 つしか持てないので、 および コントロール<xref:System.Windows.Controls.Button>のテキスト<xref:System.Windows.Controls.Primitives.Popup>を<xref:System.Windows.Controls.StackPanel>. の内容は<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.TextBlock>、関連<xref:System.Windows.Controls.Button>するコントロールの近くにアプリケーション ウィンドウの上に浮かぶ別のウィンドウに、そのテキストを表示するコントロールに表示されます。  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>ポップアップを実装するコントロール  
 コントロールは、<xref:System.Windows.Controls.Primitives.Popup>他のコントロールに組み込むことができます。 次のコントロールは、<xref:System.Windows.Controls.Primitives.Popup>特定の用途に対応するコントロールを実装します。  
  
- <xref:System.Windows.Controls.ToolTip>. 要素のツールヒントを作成する場合は、 および<xref:System.Windows.Controls.ToolTip>クラス<xref:System.Windows.Controls.ToolTipService>を使用します。 詳細については、[ToolTip の概要](tooltip-overview.md)を参照してください。  
  
- <xref:System.Windows.Controls.ContextMenu>. 要素のコンテキスト メニューを作成する場合は、コントロールを使用<xref:System.Windows.Controls.ContextMenu>します。 詳細については、[ContextMenu の概要](contextmenu-overview.md)を参照してください。  
  
- <xref:System.Windows.Controls.ComboBox>. 表示または非表示にできるドロップダウン リスト ボックスを持つ選択コントロールを作成する場合は、そのコントロールを<xref:System.Windows.Controls.ComboBox>使用します。  
  
- <xref:System.Windows.Controls.Expander>. コンテンツを表示する折りたたみ可能な領域を持つヘッダーを表示するコントロールを作成する場合は<xref:System.Windows.Controls.Expander>、コントロールを使用します。 詳細については、 [Expander の概要](expander-overview.md)を参照してください。  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>ポップアップの動作と外観  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>には、動作と外観をカスタマイズできる機能があります。 たとえば、開閉動作、アニメーション、不透明度とビットマップ効果、サイズと位置を<xref:System.Windows.Controls.Primitives.Popup>設定できます。  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>オープンとクローズの動作  
 プロパティ<xref:System.Windows.Controls.Primitives.Popup>が`true`に設定されている場合<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>、コントロールのコンテンツが表示されます。 既定では、<xref:System.Windows.Controls.Primitives.Popup>プロパティが<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>に設定されるまで開いたまま`false`になります。 ただし、プロパティを<xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A>`false`に設定すると、既定の動作を変更できます。 このプロパティを に`false`設定すると、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ ウィンドウにマウス キャプチャが表示されます。 マウス<xref:System.Windows.Controls.Primitives.Popup>キャプチャが失われ、ウィンドウの外側でマウス イベントが発生すると<xref:System.Windows.Controls.Primitives.Popup>ウィンドウが閉じます。  
  
 と イベントは、コンテンツ<xref:System.Windows.Controls.Primitives.Popup>ウィンドウが開いているか閉じられたときに発生します。 <xref:System.Windows.Controls.Primitives.Popup.Closed> <xref:System.Windows.Controls.Primitives.Popup.Opened>  
  
<a name="Animation"></a>
### <a name="animation"></a>アニメーション  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>には、フェードインやスライドインなどの動作に通常関連付けられているアニメーションの組み込みサポートがあります。 これらのアニメーションを有効にするには、プロパティを<xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A>列挙値に<xref:System.Windows.Controls.Primitives.PopupAnimation>設定します。 <xref:System.Windows.Controls.Primitives.Popup>アニメーションが正しく動作するには、プロパティを<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>に設定する`true`必要があります。  
  
 コントロールにアニメーションを<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Controls.Primitives.Popup>適用することもできます。  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>不透明度とビットマップ効果  
 <xref:System.Windows.Controls.Primitives.Popup>コントロールのプロパティは<xref:System.Windows.UIElement.Opacity%2A>、その内容には影響しません。 既定では、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ ウィンドウは不透明です。 透明<xref:System.Windows.Controls.Primitives.Popup>を作成するには、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`に設定します。  
  
 の<xref:System.Windows.Controls.Primitives.Popup>コンテンツは、<xref:System.Windows.Media.Effects.DropShadowBitmapEffect><xref:System.Windows.Controls.Primitives.Popup>コントロールまたは親ウィンドウの他の要素に直接設定したビットマップ効果など、継承されません。 のコンテンツにビットマップ効果を表示するには、その<xref:System.Windows.Controls.Primitives.Popup>コンテンツに直接ビットマップ効果を設定する必要があります。 たとえば、 の<xref:System.Windows.Controls.Primitives.Popup>子が<xref:System.Windows.Controls.StackPanel>の場合は、 にビットマップ効果を設定<xref:System.Windows.Controls.StackPanel>します。  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>ポップアップのサイズ  
 デフォルトでは、<xref:System.Windows.Controls.Primitives.Popup>はコンテンツに合わせて自動的にサイズ設定されます。 自動サイズ変更が発生すると、<xref:System.Windows.Controls.Primitives.Popup>コンテンツに定義されている画面領域の既定のサイズではビットマップ効果を表示するのに十分な領域が提供されないため、ビットマップ効果の一部が非表示になることがあります。  
  
 <xref:System.Windows.Controls.Primitives.Popup>コンテンツに対して を<xref:System.Windows.UIElement.RenderTransform%2A>設定すると、コンテンツが隠されることもあります。 このシナリオでは、変換後<xref:System.Windows.Controls.Primitives.Popup>のコンテンツが元<xref:System.Windows.Controls.Primitives.Popup>の領域を超えている場合、一部のコンテンツが非表示になることがあります。 ビットマップ効果または変換により多くの領域が必要な場合は、コントロールの領域<xref:System.Windows.Controls.Primitives.Popup>を広げるために、コンテンツの周囲に余白を定義できます。  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>ポップアップ位置の定義  
 ポップアップの<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>位置は、 、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>および<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty>の各プロパティを設定することによって行うことができます。 詳細については、「[Popup Placement Behavior](popup-placement-behavior.md)」を参照してください。 画面<xref:System.Windows.Controls.Primitives.Popup>に表示されている場合、親が再配置された場合、その位置は変更されません。  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 コントロールの配置を<xref:System.Windows.Controls.Primitives.Popup>カスタマイズするには、表示する位置に対して相対的な座標の<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>セット<xref:System.Windows.Controls.Primitives.Popup>を指定します。  
  
 配置をカスタマイズするには、プロパティ<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>を<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>に設定します。 次に、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>可能な配置ポイントと基本軸のセットを (優先順に) 返すデリゲート<xref:System.Windows.Controls.Primitives.Popup>を定義します。 の最大部分を示す点<xref:System.Windows.Controls.Primitives.Popup>が自動的に選択されます。 例については、「[方法 : ポップアップのカスタム位置を指定する](how-to-specify-a-custom-popup-position.md)」をご覧ください。  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>ポップアップとビジュアル ツリー  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>には独自のビジュアル ツリーがありません。代わりに、メソッド<xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A><xref:System.Windows.Controls.Primitives.Popup>が呼び出されたときに、サイズ 0 (ゼロ) を返します。 ただし、 のプロパティを<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>`true`に設定<xref:System.Windows.Controls.Primitives.Popup>すると、独自のビジュアル ツリーを持つ新しいウィンドウが作成されます。 新しいウィンドウには<xref:System.Windows.Controls.Primitives.Popup.Child%2A>の内容<xref:System.Windows.Controls.Primitives.Popup>が含まれます。 新しいウィンドウの幅および高さは、画面の幅または高さの 75% より大きくすることはできません。  
  
 コントロール<xref:System.Windows.Controls.Primitives.Popup>は、その<xref:System.Windows.Controls.Primitives.Popup.Child%2A>コンテンツへの参照を論理子として保持します。 新しいウィンドウが作成されると、 の<xref:System.Windows.Controls.Primitives.Popup>内容がウィンドウのビジュアル子となり、 の<xref:System.Windows.Controls.Primitives.Popup>論理子のままになります。 逆に、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ<xref:System.Windows.Controls.Primitives.Popup.Child%2A>の論理的な親はそのまま残ります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [ハウツートピック](popup-how-to-topics.md)
- [ハウツートピック](tooltip-how-to-topics.md)
