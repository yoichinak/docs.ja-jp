---
title: ToolBar の概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: b5498b8b88c7403ffe51256a57544261de3ace08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186609"
---
# <a name="toolbar-overview"></a>ToolBar の概要
<xref:System.Windows.Controls.ToolBar>コントロールは、通常、その機能に関連するコマンドまたはコントロールのグループのコンテナです。 通常<xref:System.Windows.Controls.ToolBar>、 にはコマンドを呼び出すボタンが含まれています。  

<a name="ToolBarControl"></a>
## <a name="toolbar-control"></a>ToolBar コントロール  
 コントロール<xref:System.Windows.Controls.ToolBar>は、ボタンやその他のコントロールのバーのような配置から、その名前を単一の行または列に取り込みます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar>コントロールは、サイズ制約<xref:System.Windows.Controls.ToolBar>内に自然に収まらない項目を特殊なオーバーフロー領域に配置するオーバーフローメカニズムを提供します。 また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar>通常、コントロールは、特別な<xref:System.Windows.Controls.ToolBarTray>レイアウト動作を提供するだけでなく、ツールバーのユーザーが開始するサイズ変更と配置のサポートを提供する、関連するコントロールで使用されます。  
  
<a name="Creating_ToolBars"></a>
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>ToolBarTray でツールバーの位置を指定する  
 プロパティと<xref:System.Windows.Controls.ToolBar.Band%2A><xref:System.Windows.Controls.ToolBar.BandIndex%2A>プロパティを使用して<xref:System.Windows.Controls.ToolBar>、<xref:System.Windows.Controls.ToolBarTray>を に配置します。 <xref:System.Windows.Controls.ToolBar.Band%2A>は、 が親<xref:System.Windows.Controls.ToolBar><xref:System.Windows.Controls.ToolBarTray>内に配置される位置を示します。 <xref:System.Windows.Controls.ToolBar.BandIndex%2A>は、バンド内に配置<xref:System.Windows.Controls.ToolBar>される順序を示します。 このプロパティを使用してコントロールを内部に配置<xref:System.Windows.Controls.ToolBar>する方法を<xref:System.Windows.Controls.ToolBarTray>次の例に示します。  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>
## <a name="toolbars-with-overflow-items"></a>オーバーフロー項目を含むツールバー  
 多<xref:System.Windows.Controls.ToolBar>くの場合、コントロールには、ツールバーのサイズに収まらない項目が含まれています。 この場合、オーバーフロー<xref:System.Windows.Controls.ToolBar>ボタンが表示されます。 オーバーフロー項目を表示するには、オーバーフロー ボタンをクリックすると、アイテムが の下のポップアップ ウィンドウに<xref:System.Windows.Controls.ToolBar>表示されます。 次の図は、<xref:System.Windows.Controls.ToolBar>オーバーフロー項目を示しています。  
  
 ![オーバーフロー項目を含むツール バーを示すスクリーンショット。](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 ツールバーの項目をオーバーフロー パネルに配置するタイミングを指定するには、添付プロパティを<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType><xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>、 、<xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>または<xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>に設定します。 次の例では、ツールバーの最後の 4 つのボタンを常にオーバーフロー パネルに配置します。  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 は<xref:System.Windows.Controls.ToolBar>、<xref:System.Windows.Controls.Primitives.ToolBarPanel>と<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>で<xref:System.Windows.Controls.ControlTemplate>使用します。  <xref:System.Windows.Controls.Primitives.ToolBarPanel>は、ツールバー上の項目のレイアウトを担当します。  は<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>、 に収まらない項目のレイアウトを担当します<xref:System.Windows.Controls.ToolBar>。 の例<xref:System.Windows.Controls.ControlTemplate>については<xref:System.Windows.Controls.ToolBar>、 を参照してください。  
  
 [ツール バーのスタイルとテンプレート 。](toolbar-styles-and-templates.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [ToolBar のコントロールのスタイルを設定する](how-to-style-controls-on-a-toolbar.md)
- [WPF コントロール ギャラリーのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
