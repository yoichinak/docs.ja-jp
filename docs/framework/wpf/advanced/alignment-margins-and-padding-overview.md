---
title: 配置、余白、パディングの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: bec2d9cd224febb650e2de67bb7406365d075963
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145476"
---
# <a name="alignment-margins-and-padding-overview"></a>配置、余白、パディングの概要
この<xref:System.Windows.FrameworkElement>クラスは、子要素を正確に配置するために使用される複数のプロパティを公開します。 ここでは、最も重要なプロパティ 、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>の 4 つのプロパティについて説明します。 これらのプロパティの効果を理解することが重要です。[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの要素の位置を制御するための基本となるためです。  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>要素配置の概要  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を利用し、さまざまな方法で要素を配置できます。 しかし、理想的なレイアウトを実現することは、単に正しい<xref:System.Windows.Controls.Panel>要素を選択するだけではありません。 位置を細かく制御するには、 、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>および<xref:System.Windows.Controls.Border.Padding%2A><xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを理解する必要があります。  
  
 次の図は、いくつかの配置プロパティを利用したレイアウト シナリオのものです。  
  
 ![WPF 位置決めのプロパティのサンプル](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 一見すると、この<xref:System.Windows.Controls.Button>図の要素はランダムに配置されているように見えることがあります。 しかしながら、位置は実際のところ、余白、配置、パディングを組み合わせることで正確に制御されます。  
  
 次の例は、前の図のレイアウトの作成方法を示しています。 要素<xref:System.Windows.Controls.Border>は、15<xref:System.Windows.Controls.StackPanel>デバイスに依存<xref:System.Windows.Controls.Border.Padding%2A>しないピクセルの値を持つ親をカプセル化します。 これは、子を取<xref:System.Windows.Media.Brushes.LightBlue%2A>り囲む狭いバンド<xref:System.Windows.Controls.StackPanel>を占めています。 の<xref:System.Windows.Controls.StackPanel>子要素は、このトピックで詳しく説明するさまざまな位置指定プロパティのそれぞれを示すために使用されます。 3<xref:System.Windows.Controls.Button>つの要素を使用して、 <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティと プロパティの両方を示します。  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 次の図は、前のサンプルで使用されたさまざまな配置プロパティを大写しにしたものです。 このトピックの後続のセクションでは、各配置プロパティの使用方法をさらに詳しく説明します。  
  
 ![スクリーン コール&#45;アウトを使用したプロパティの配置](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>配置プロパティを理解する  
 および<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A><xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティは、子要素を親要素の割り当てられたレイアウト空間内にどのように配置するかを記述します。 これらのプロパティを一緒に使用することで、子要素を正確に配置できます。 たとえば、 の子要素は<xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.HorizontalAlignment.Left>、 、 、 <xref:System.Windows.HorizontalAlignment.Right> <xref:System.Windows.HorizontalAlignment.Center>、 、 、 <xref:System.Windows.HorizontalAlignment.Stretch> 、 、 の 4 つの異なる水平方向の配置を指定して、使用可能なスペースを埋めることができます。 垂直配置にも同様の値を利用できます。  
  
> [!NOTE]
> 明示的に設定<xref:System.Windows.FrameworkElement.Height%2A>されたプロパティ<xref:System.Windows.FrameworkElement.Width%2A>と、要素のプロパティは、プロパティ値<xref:System.Windows.HorizontalAlignment.Stretch>よりも優先されます。 <xref:System.Windows.FrameworkElement.Height%2A>、、<xref:System.Windows.FrameworkElement.Width%2A>および<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>値を`Stretch`設定しようとすると、要求が`Stretch`無視されます。  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>HorizontalAlignment プロパティ  
 この<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティは、子要素に適用する水平方向の配置特性を宣言します。 次の表に、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティの値を示します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|子要素は、親要素に割り当てられたレイアウト領域の左に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Center>|子要素は、親要素に割り当てられたレイアウト領域の中央に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Right>|子要素は、親要素に割り当てられたレイアウト領域の右に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (既定値)|子要素は引き伸ばされ、親要素に割り当てられたレイアウト領域を埋めます。 明示的<xref:System.Windows.FrameworkElement.Width%2A>な<xref:System.Windows.FrameworkElement.Height%2A>値と値が優先されます。|  
  
 次の例は、プロパティを要素<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>に適用<xref:System.Windows.Controls.Button>する方法を示しています。 各属性値が示され、さまざまなレンダリング動作をより良く表しています。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 前のコードは次の画像のようなレイアウトを作ります。 各<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>値の位置指定の効果は、図に示されています。  
  
 ![HorizontalAlignment のサンプル](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>VerticalAlignment プロパティ  
 この<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティは、子要素に適用する垂直方向の配置特性を記述します。 次の表に、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティに使用できる値を示します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|子要素は、親要素に割り当てられたレイアウト領域の上に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Center>|子要素は、親要素に割り当てられたレイアウト領域の中央に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Bottom>|子要素は、親要素に割り当てられたレイアウト領域の下に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Stretch> (既定値)|子要素は引き伸ばされ、親要素に割り当てられたレイアウト領域を埋めます。 明示的<xref:System.Windows.FrameworkElement.Width%2A>な<xref:System.Windows.FrameworkElement.Height%2A>値と値が優先されます。|  
  
 次の例は、プロパティを要素<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>に適用<xref:System.Windows.Controls.Button>する方法を示しています。 各属性値が示され、さまざまなレンダリング動作をより良く表しています。 このサンプルでは、表示されるグリッド線<xref:System.Windows.Controls.Grid>を持つ要素を親として使用し、各プロパティ値のレイアウト動作をわかりやすく説明します。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 前のコードは次の画像のようなレイアウトを作ります。 各<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>値の位置指定の効果は、図に示されています。  
  
 ![VerticalAlignment プロパティのサンプル](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>余白プロパティを理解する  
 この<xref:System.Windows.FrameworkElement.Margin%2A>プロパティは、要素とその子またはピア間の距離を記述します。 <xref:System.Windows.FrameworkElement.Margin%2A>値は、 のような`Margin="20"`構文を使用して、一様に設定できます。 この構文では、20<xref:System.Windows.FrameworkElement.Margin%2A>個のデバイスに依存しないピクセルの均一なピクセルが要素に適用されます。 <xref:System.Windows.FrameworkElement.Margin%2A>値は、左、上、右、下 (その順序で) に適用する個別のマージンを表す 4 つの異なる値の形式を`Margin="0,10,5,25"`とることもできます。 プロパティを適切に<xref:System.Windows.FrameworkElement.Margin%2A>使用すると、要素のレンダリング位置と、隣接する要素と子のレンダリング位置を非常に細かく制御できます。  
  
> [!NOTE]
> 0 以外のマージンは、要素<xref:System.Windows.FrameworkElement.ActualWidth%2A>と の外側に<xref:System.Windows.FrameworkElement.ActualHeight%2A>スペースを適用します。  
  
 要素のグループの周囲に均一な余白を適用する<xref:System.Windows.Controls.Button>方法を次の例に示します。 要素<xref:System.Windows.Controls.Button>は、各方向に 10 ピクセルの余白バッファーを使用して均等に配置されます。  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 多くの場合、均一余白は適切ではありません。 適切でなければ、均一ではない間隔を適用できます。 次の例は、均一ではない余白間隔を子要素に適用する方法を示しています。 余白は左、上、右、下の順序で記述されます。  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>
## <a name="understanding-the-padding-property"></a>Padding プロパティを理解する  
 パディングは、<xref:System.Windows.FrameworkElement.Margin%2A>ほとんどの点で似ています。 Padding<xref:System.Windows.Documents.Block>プロパティは、主に便利なクラス 、、および<xref:System.Windows.Controls.Border><xref:System.Windows.Controls.Control>Padding プロパティを公開するクラスの<xref:System.Windows.Controls.TextBlock>サンプルとして、いくつかのクラスでのみ公開されます。 この<xref:System.Windows.Controls.Border.Padding%2A>プロパティは、指定された値だけ子要素の有効なサイズ<xref:System.Windows.Thickness>を拡大します。  
  
 親<xref:System.Windows.Controls.Border.Padding%2A><xref:System.Windows.Controls.Border>要素に適用する方法を次の例に示します。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>アプリケーションで配置、余白、パディングを利用する  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>、、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>および 複合[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]を作成するために必要な位置決め制御を提供します。 各プロパティの効果を利用し、子要素の配置を変更できます。動的なアプリケーション/ユーザー体験を生み出す柔軟性が与えられます。  
  
 次の例は、このトピックで説明した各概念を示しています。 この例では、このトピックの最初のサンプルで見つかったインフラストラクチャを基に<xref:System.Windows.Controls.Grid>、要素を最初のサンプル<xref:System.Windows.Controls.Border>の子として追加します。 <xref:System.Windows.Controls.Border.Padding%2A>が親<xref:System.Windows.Controls.Border>要素に適用されます。 は<xref:System.Windows.Controls.Grid>、3 つの子<xref:System.Windows.Controls.StackPanel>要素間の領域を分割するために使用されます。 <xref:System.Windows.Controls.Button>要素は、 と<xref:System.Windows.FrameworkElement.Margin%2A><xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>のさまざまな効果を示すためにも使用されます。 <xref:System.Windows.Controls.TextBlock>各列の要素に<xref:System.Windows.Controls.ColumnDefinition>適用されるさまざまなプロパティをより適切に定義するために<xref:System.Windows.Controls.Button>、各要素が追加されます。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 コンパイルすると、先のアプリケーションは次の図のような [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] になります。 さまざまなプロパティ値の効果は要素間の間隔で明らかにされ、各列の要素の重要なプロパティ値は要素内<xref:System.Windows.Controls.TextBlock>に表示されます。  
  
 ![1 つのアプリケーション内の複数の位置決めプロパティ](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>参照トピック  
 クラスによって定義される位置プロパティ<xref:System.Windows.FrameworkElement>により、アプリケーション内での要素配置[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の細かい制御が可能になります。 これで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を利用して効果的に要素を配置するための手法を理解できたことでしょう。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトの詳細はその他の資料で確認できます。 [「パネルの概要」](../controls/panels-overview.md)トピックには、さまざまな<xref:System.Windows.Controls.Panel>要素の詳細が含まれています。 トピック[チュートリアル: 最初の WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)では、レイアウト要素を使用してコンポーネントを配置し、そのアクションをデータ ソースにバインドする高度な手法を紹介します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [パネル概要](../controls/panels-overview.md)
- [レイアウト](layout.md)
- [WPF レイアウト ギャラリー サンプル](https://go.microsoft.com/fwlink/?LinkID=160054)
