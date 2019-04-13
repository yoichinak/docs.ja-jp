---
title: ToolBar の概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 711d55e46fb548787976a1f966c9fbf6dc7f12d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105328"
---
# <a name="toolbar-overview"></a>ToolBar の概要
<xref:System.Windows.Controls.ToolBar> コントロールは、コマンドまたはコントロールの機能に関連する通常のグループのコンテナーです。 A<xref:System.Windows.Controls.ToolBar>通常のコマンドを呼び出すボタンが含まれています。  

<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar コントロール  
 <xref:System.Windows.Controls.ToolBar>コントロールは、1 つの行または列にボタンやその他のコントロール バーのような配置から名前を取得します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> コントロールがサイズ制限内で自然に適合しないすべての項目を配置するオーバーフロー メカニズムを提供<xref:System.Windows.Controls.ToolBar>特別なオーバーフロー領域にします。 また、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar>コントロールを使用して、通常は、関連の<xref:System.Windows.Controls.ToolBarTray>コントロールで、ユーザーによるサイズ変更や、ツールバーの配置のためのサポートだけでなく、特殊なレイアウト動作を提供します。  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>ToolBarTray でツールバーの位置を指定する  
 使用して、<xref:System.Windows.Controls.ToolBar.Band%2A>と<xref:System.Windows.Controls.ToolBar.BandIndex%2A>プロパティを<xref:System.Windows.Controls.ToolBar>で、<xref:System.Windows.Controls.ToolBarTray>します。 <xref:System.Windows.Controls.ToolBar.Band%2A> 位置を示す、<xref:System.Windows.Controls.ToolBar>はその親内に配置<xref:System.Windows.Controls.ToolBarTray>します。 <xref:System.Windows.Controls.ToolBar.BandIndex%2A> 順序を示す、<xref:System.Windows.Controls.ToolBar>そのバンド内に配置されます。 次の例は、配置するこのプロパティを使用する方法<xref:System.Windows.Controls.ToolBar>内部コントロール、<xref:System.Windows.Controls.ToolBarTray>します。  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>オーバーフロー項目を含むツールバー  
 多くの場合、<xref:System.Windows.Controls.ToolBar>コントロールは、ツールバーのサイズに収まるよりもさらに項目を含めることができます。 この場合、<xref:System.Windows.Controls.ToolBar>オーバーフロー ボタンが表示されます。 ユーザーをオーバーフロー項目を表示するには、オーバーフロー ボタンをクリックして、項目は、次のポップアップ ウィンドウに表示されます、<xref:System.Windows.Controls.ToolBar>します。 次の図は、<xref:System.Windows.Controls.ToolBar>オーバーフロー項目を含む。  
  
 ![オーバーフロー項目を含むツールバーを示すスクリーン ショット。](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 設定してツールバーにあるアイテムがオーバーフロー パネルに配置すると指定することができます、<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType>添付プロパティを<xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>、 <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>、または<xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>します。 次の例では、ツールバーの最後の 4 つのボタンを常にオーバーフロー パネルに配置します。  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar>を使用して、<xref:System.Windows.Controls.Primitives.ToolBarPanel>と<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>でその<xref:System.Windows.Controls.ControlTemplate>します。  <xref:System.Windows.Controls.Primitives.ToolBarPanel>ツールバーの項目のレイアウトを担当します。  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>に収まらない項目のレイアウトを行いますが、<xref:System.Windows.Controls.ToolBar>します。 例については、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ToolBar>を参照してください  
  
 [ツール バーのスタイルとテンプレート](toolbar-styles-and-templates.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [ToolBar のコントロールのスタイルを設定する](how-to-style-controls-on-a-toolbar.md)
- [WPF コントロール ギャラリー サンプル](https://go.microsoft.com/fwlink/?LinkID=160053)
