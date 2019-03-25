---
title: エキスパンダーの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
ms.openlocfilehash: 29003779825b92402fa12b810c1a099731ac8af6
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409459"
---
# <a name="expander-overview"></a>エキスパンダーの概要
<xref:System.Windows.Controls.Expander>コントロール ウィンドウに似ていますし、ヘッダーを含む展開可能な領域内のコンテンツを提供する方法を提供します。  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>単純なエキスパンダーの作成  
 次の例は、単純なを作成する方法を示します<xref:System.Windows.Controls.Expander>コントロール。 この例で作成、<xref:System.Windows.Controls.Expander>前の図のようになります。  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>と<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>の<xref:System.Windows.Controls.Expander>も含めることができます、複雑な内容など<xref:System.Windows.Controls.RadioButton>と<xref:System.Windows.Controls.Image>オブジェクト。  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>コンテンツ エリアの展開方向の設定  
 コンテンツ エリアを設定することができます、 <xref:System.Windows.Controls.Expander> 4 方向のどちらに展開するコントロール (<xref:System.Windows.Controls.ExpandDirection.Down>、 <xref:System.Windows.Controls.ExpandDirection.Up>、 <xref:System.Windows.Controls.ExpandDirection.Left>、または<xref:System.Windows.Controls.ExpandDirection.Right>) を使用して、<xref:System.Windows.Controls.ExpandDirection>プロパティ。 ときに、コンテンツ領域は折りたたまれて、のみ、 <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>され、そのトグル ボタンが表示されます。 A<xref:System.Windows.Controls.Button>方向矢印を表示するコントロールが展開または折りたたみのコンテンツ エリアにトグル ボタンとして使用されます。 展開すると、<xref:System.Windows.Controls.Expander>ウィンドウに似た領域内のすべてのコンテンツの表示を試みます。  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>パネル内のエキスパンダーのサイズの制御  
 場合、<xref:System.Windows.Controls.Expander>から継承されるレイアウト コントロール内のコントロールが<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.StackPanel>を指定しない、<xref:System.Windows.FrameworkElement.Height%2A>上、<xref:System.Windows.Controls.Expander>ときに、<xref:System.Windows.Controls.Expander.ExpandDirection%2A>プロパティに設定されて<xref:System.Windows.Controls.ExpandDirection.Down>または<xref:System.Windows.Controls.ExpandDirection.Up>します。 同様に、指定しない、<xref:System.Windows.FrameworkElement.Width%2A>上、<xref:System.Windows.Controls.Expander>ときに、<xref:System.Windows.Controls.Expander.ExpandDirection%2A>プロパティに設定されて<xref:System.Windows.Controls.ExpandDirection.Left>または<xref:System.Windows.Controls.ExpandDirection.Right>します。  
  
 サイズを設定すると、<xref:System.Windows.Controls.Expander>展開されたコンテンツが表示されることは、方向、<xref:System.Windows.Controls.Expander>はコンテンツによって使用され、その周囲に境界線を表示する領域を制御します。 コンテンツが折りたたまれても、境界線は表示されます。 展開されたコンテンツ エリアのサイズを設定するには、上のコンテンツ サイズを設定、 <xref:System.Windows.Controls.Expander>、または、機能上のスクロールする場合、<xref:System.Windows.Controls.ScrollViewer>コンテンツを囲みます。  
  
 ときに、<xref:System.Windows.Controls.Expander>コントロールは、最後の要素を<xref:System.Windows.Controls.DockPanel>、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]が自動的に設定、<xref:System.Windows.Controls.Expander>等しく、残りの領域のディメンション、<xref:System.Windows.Controls.DockPanel>します。 この既定の動作を防ぐためには、次のように設定します。、<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>プロパティを、<xref:System.Windows.Controls.DockPanel>オブジェクトを`false`、ことを確認しますまたは、<xref:System.Windows.Controls.Expander>の最後の要素ではありません、<xref:System.Windows.Controls.DockPanel>します。  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>スクロール可能なコンテンツの作成  
 コンテンツをラップするには、コンテンツが大きすぎてコンテンツ領域のサイズの場合、<xref:System.Windows.Controls.Expander>で、<xref:System.Windows.Controls.ScrollViewer>スクロール可能なコンテンツを提供するためにします。 <xref:System.Windows.Controls.Expander>コントロールがスクロール機能を自動的に提供しません。 次の図は、<xref:System.Windows.Controls.Expander>コントロールを含む、<xref:System.Windows.Controls.ScrollViewer>コントロール。  
  
 **ScrollViewer 内のエキスパンダー**  
  
 ![ScrollBar を持つエキスパンダーを示すスクリーン ショット。](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 配置するとき、<xref:System.Windows.Controls.Expander>を制御、 <xref:System.Windows.Controls.ScrollViewer>、設定、<xref:System.Windows.Controls.ScrollViewer>ディメンションの方向に対応するプロパティ、<xref:System.Windows.Controls.Expander>コンテンツのサイズが表示されます、<xref:System.Windows.Controls.Expander>コンテンツ エリア。 設定する場合など、<xref:System.Windows.Controls.Expander.ExpandDirection%2A>プロパティを<xref:System.Windows.Controls.Expander>に<xref:System.Windows.Controls.ExpandDirection.Down>(コンテンツ領域は、ダウンが開いたら、) 設定、<xref:System.Windows.FrameworkElement.Height%2A>プロパティを<xref:System.Windows.Controls.ScrollViewer>必要なコンテンツ エリアの高さを制御します。 代わりに自体には、コンテンツの高さを設定した場合<xref:System.Windows.Controls.ScrollViewer>この設定は認識されず、そのため、スクロール可能なコンテンツは提供されません。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>を持つ複合型のコンテンツを含むコントロールを<xref:System.Windows.Controls.ScrollViewer>コントロール。 この例で作成、<xref:System.Windows.Controls.Expander>このセクションの先頭には図のようです。  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>配置プロパティの使用  
 コンテンツの配置を設定して、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>と<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>プロパティを<xref:System.Windows.Controls.Expander>コントロール。 これらのプロパティを設定すると、配置がヘッダーに適用され、展開されたコンテンツにも適用されます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [方法トピック](expander-how-to-topics.md)
