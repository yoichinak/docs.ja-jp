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
ms.openlocfilehash: 892d972a5704d50e91d04e05d6fdea7180a3155d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187109"
---
# <a name="expander-overview"></a>エキスパンダーの概要
コントロール<xref:System.Windows.Controls.Expander>は、ウィンドウに似た展開可能な領域にコンテンツを提供する方法を提供し、ヘッダーを含みます。  

<a name="CreatinganExpanderinXAML"></a>
## <a name="creating-a-simple-expander"></a>単純なエキスパンダーの作成  
 次の例は、単純な<xref:System.Windows.Controls.Expander>コントロールを作成する方法を示しています。 この例では、<xref:System.Windows.Controls.Expander>前の図のようなを作成します。  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>および<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>の<xref:System.Windows.Controls.Expander>は、 および オブジェクトなどの<xref:System.Windows.Controls.RadioButton>複雑な<xref:System.Windows.Controls.Image>コンテンツを含むこともできます。  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>
## <a name="setting-the-direction-of-the-expanding-content-area"></a>コンテンツ エリアの展開方向の設定  
 <xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.ExpandDirection.Down><xref:System.Windows.Controls.ExpandDirection.Up><xref:System.Windows.Controls.ExpandDirection.Left><xref:System.Windows.Controls.ExpandDirection.Right>プロパティを使用して、コントロールのコンテンツ領域を 4 つの方向 (、、、、、、、、、、または ) のいずれかで展開するように設定できます。 <xref:System.Windows.Controls.ExpandDirection> コンテンツ領域が折りたたまれている場合は、<xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.HeaderedContentControl.Header%2A>および トグル ボタンのみが表示されます。 方向<xref:System.Windows.Controls.Button>矢印を表示するコントロールは、コンテンツ領域を展開または折りたたむ切り替えボタンとして使用されます。 展開すると、ウィンドウ<xref:System.Windows.Controls.Expander>に似た領域にすべてのコンテンツが表示されます。  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>パネル内のエキスパンダーのサイズの制御  
 から継承<xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.Panel>されるレイアウト コントロール内<xref:System.Windows.Controls.StackPanel>にコントロールがある場合は、 プロパティ<xref:System.Windows.FrameworkElement.Height%2A><xref:System.Windows.Controls.Expander>が or に設定<xref:System.Windows.Controls.Expander.ExpandDirection%2A><xref:System.Windows.Controls.ExpandDirection.Down>されているときに、 で を指定<xref:System.Windows.Controls.ExpandDirection.Up>しないでください。 同様に、 プロパティが<xref:System.Windows.FrameworkElement.Width%2A>or<xref:System.Windows.Controls.Expander>に<xref:System.Windows.Controls.Expander.ExpandDirection%2A>設定<xref:System.Windows.Controls.ExpandDirection.Left>されている場合は、<xref:System.Windows.Controls.ExpandDirection.Right>で を指定しないでください。  
  
 展開されたコンテンツが表示される方向に<xref:System.Windows.Controls.Expander>コントロールにサイズ ディメンションを設定すると、コンテンツで使用<xref:System.Windows.Controls.Expander>される領域がコントロールされ、その周りに枠線が表示されます。 コンテンツが折りたたまれても、境界線は表示されます。 展開されたコンテンツ領域のサイズを設定するには、 の<xref:System.Windows.Controls.Expander>コンテンツにサイズのサイズを設定するか、スクロール機能を使用する場合<xref:System.Windows.Controls.ScrollViewer>は、コンテンツを囲みます。  
  
 <xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.DockPanel>コントロールが[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の最後の要素である場合、寸法は<xref:System.Windows.Controls.Expander>自動的にの残りの領域と等しくなる<xref:System.Windows.Controls.DockPanel>。 この既定の動作を回避するには、<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>オブジェクトのプロパティ<xref:System.Windows.Controls.DockPanel>を`false`に設定するか、 が<xref:System.Windows.Controls.Expander>の最後の要素でないことを<xref:System.Windows.Controls.DockPanel>確認します。  
  
<a name="CreatingScrollableContent"></a>
## <a name="creating-scrollable-content"></a>スクロール可能なコンテンツの作成  
 コンテンツ領域のサイズに対してコンテンツが大きすぎる場合は、スクロール可能なコンテンツを提供するために<xref:System.Windows.Controls.Expander>、コンテンツ<xref:System.Windows.Controls.ScrollViewer>を in にラップできます。 コントロール<xref:System.Windows.Controls.Expander>は、スクロール機能を自動的に提供しません。 コントロールを含むコントロール<xref:System.Windows.Controls.Expander>を次の図<xref:System.Windows.Controls.ScrollViewer>に示します。  
  
 **ScrollViewer 内のエキスパンダー**  
  
 ![スクロール バーを使用してエクスパンダを示すスクリーンショット。](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 コントロールを<xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.ScrollViewer>に配置する場合、<xref:System.Windows.Controls.ScrollViewer><xref:System.Windows.Controls.Expander>コンテンツが開く方向に対応する dimension プロパティをコンテンツ領域のサイズに設定します<xref:System.Windows.Controls.Expander>。 たとえば、<xref:System.Windows.Controls.Expander.ExpandDirection%2A>のプロパティ<xref:System.Windows.Controls.Expander>を設定した場合<xref:System.Windows.Controls.ExpandDirection.Down>(コンテンツ領域が下に開く)、<xref:System.Windows.FrameworkElement.Height%2A><xref:System.Windows.Controls.ScrollViewer>コントロールのプロパティをコンテンツ領域の必要な高さに設定します。 代わりにコンテンツ自体に高さディメンションを設定した場合<xref:System.Windows.Controls.ScrollViewer>、この設定は認識されず、スクロール可能なコンテンツは提供されません。  
  
 次の例は、複雑なコンテンツ<xref:System.Windows.Controls.Expander>を持ち、コントロールを含むコントロール<xref:System.Windows.Controls.ScrollViewer>を作成する方法を示しています。 この例では、<xref:System.Windows.Controls.Expander>このセクションの冒頭の図のような図を作成します。  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>
## <a name="using-the-alignment-properties"></a>配置プロパティの使用  
 コントロールの プロパティと プロパティ<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>を<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>設定して、<xref:System.Windows.Controls.Expander>コンテンツを配置できます。 これらのプロパティを設定すると、配置がヘッダーに適用され、展開されたコンテンツにも適用されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [ハウツートピック](expander-how-to-topics.md)
