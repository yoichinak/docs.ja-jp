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
ms.openlocfilehash: 58af8848a6b8a5e4ded453831f5a7ef985548492
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032202"
---
# <a name="alignment-margins-and-padding-overview"></a>配置、余白、パディングの概要
<xref:System.Windows.FrameworkElement>クラスは、子要素の正確な配置に使用されるいくつかのプロパティを公開します。 このトピックでは、4 つの最も重要なプロパティについて説明します。 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.Controls.Border.Padding%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>します。 これらのプロパティの効果を理解することが重要です。[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの要素の位置を制御するための基本となるためです。  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>要素配置の概要  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を利用し、さまざまな方法で要素を配置できます。 ただし、単に、右側の選択を超えるは最適なレイアウトを実現する<xref:System.Windows.Controls.Panel>要素。 配置の制御の理解が必要です、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.Controls.Border.Padding%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティ。  
  
 次の図は、いくつかの配置プロパティを利用したレイアウト シナリオのものです。  
  
 ![WPF 位置決めプロパティのサンプル](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 一見、<xref:System.Windows.Controls.Button>をランダムに配置する次の図の要素があります。 しかしながら、位置は実際のところ、余白、配置、パディングを組み合わせることで正確に制御されます。  
  
 次の例は、前の図のレイアウトの作成方法を示しています。 A<xref:System.Windows.Controls.Border>要素に親がカプセル化します<xref:System.Windows.Controls.StackPanel>で、 <xref:System.Windows.Controls.Border.Padding%2A> 15 デバイス非依存ピクセルの値。 これは、アカウントをナローの<xref:System.Windows.Media.Brushes.LightBlue%2A>バンドを子を囲む<xref:System.Windows.Controls.StackPanel>します。 子要素、<xref:System.Windows.Controls.StackPanel>のこのトピックの詳細については、さまざまな配置のプロパティを説明するために使用されます。 次の 3 つ<xref:System.Windows.Controls.Button>要素を使用すると、両方を示す、<xref:System.Windows.FrameworkElement.Margin%2A>と<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティ。  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 次の図は、前のサンプルで使用されたさまざまな配置プロパティを大写しにしたものです。 このトピックの後続のセクションでは、各配置プロパティの使用方法をさらに詳しく説明します。  
  
 ![配置プロパティ (解説付き)](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>配置プロパティを理解する  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティは、親要素に割り当てられたレイアウト領域内の子要素の配置方法について説明します。 これらのプロパティを一緒に使用することで、子要素を正確に配置できます。 たとえば、子要素の<xref:System.Windows.Controls.DockPanel>4 つの異なる水平配置を指定できます: <xref:System.Windows.HorizontalAlignment.Left>、 <xref:System.Windows.HorizontalAlignment.Right>、または<xref:System.Windows.HorizontalAlignment.Center>、または<xref:System.Windows.HorizontalAlignment.Stretch>使用可能な領域を埋めます。 垂直配置にも同様の値を利用できます。  
  
> [!NOTE]
>  明示的に設定された<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>要素のプロパティよりも優先、<xref:System.Windows.HorizontalAlignment.Stretch>プロパティの値。 設定しようとしています。 <xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、および<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>の値`Stretch`結果、`Stretch`要求が無視されます。  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment プロパティ  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティが子要素に適用する水平方向の配置特性を宣言します。 次の表は、可能な値の<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティ。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|子要素は、親要素に割り当てられたレイアウト領域の左に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Center>|子要素は、親要素に割り当てられたレイアウト領域の中央に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Right>|子要素は、親要素に割り当てられたレイアウト領域の右に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (既定値)|子要素は引き伸ばされ、親要素に割り当てられたレイアウト領域を埋めます。 明示的な<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>値が優先されます。|  
  
 次の例では、適用する方法を示しています、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.Controls.Button>要素。 各属性値が示され、さまざまなレンダリング動作をより良く表しています。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 前のコードは次の画像のようなレイアウトを作ります。 それぞれの配置効果<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>値は、図に表示されます。  
  
 ![HorizontalAlignment のサンプル](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment プロパティ  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティは、子要素に適用する垂直方向の配置特性を記述します。 次の表は、可能な値の<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティ。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|子要素は、親要素に割り当てられたレイアウト領域の上に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Center>|子要素は、親要素に割り当てられたレイアウト領域の中央に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Bottom>|子要素は、親要素に割り当てられたレイアウト領域の下に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Stretch> (既定値)|子要素は引き伸ばされ、親要素に割り当てられたレイアウト領域を埋めます。 明示的な<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>値が優先されます。|  
  
 次の例では、適用する方法を示しています、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを<xref:System.Windows.Controls.Button>要素。 各属性値が示され、さまざまなレンダリング動作をより良く表しています。 このサンプルの目的で、<xref:System.Windows.Controls.Grid>表示のグリッド線を持つ要素は、各プロパティ値のレイアウト動作をよく示すために、親として使用されます。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 前のコードは次の画像のようなレイアウトを作ります。 それぞれの配置効果<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>値は、図に表示されます。  
  
 ![VerticalAlignment プロパティのサンプル](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>余白プロパティを理解する  
 <xref:System.Windows.FrameworkElement.Margin%2A>プロパティには、要素とその子またはピア間の距離がについて説明します。 <xref:System.Windows.FrameworkElement.Margin%2A> ような構文を使用して値を統一されたできます`Margin="20"`します。 この構文では、統一された<xref:System.Windows.FrameworkElement.Margin%2A>要素に 20 のデバイスの非依存のピクセルは適用されます。 <xref:System.Windows.FrameworkElement.Margin%2A> 値をとることも、個別の値が 4 つのフォーム左、上、右、下に (この順序で) に適用する別個の余白の各値のような`Margin="0,10,5,25"`します。 適切な使用、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティが要素のレンダリング位置とその近隣要素、子の描画位置の非常に細かく制御できるようにします。  
  
> [!NOTE]
>  0 以外の余白は、要素の<xref:System.Windows.FrameworkElement.ActualWidth%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>します。  
  
 次の例は、グループの周囲に均一な余白を適用する方法を示しています。<xref:System.Windows.Controls.Button>要素。 <xref:System.Windows.Controls.Button>要素を各方向に 10 ピクセルの余白のバッファーを等間隔に配置します。  
  
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
 パディングは<xref:System.Windows.FrameworkElement.Margin%2A>多くの点でします。 便利なように主に、いくつかのクラスでのみ、Padding プロパティに公開される: <xref:System.Windows.Documents.Block>、 <xref:System.Windows.Controls.Border>、 <xref:System.Windows.Controls.Control>、および<xref:System.Windows.Controls.TextBlock>Padding プロパティを公開するクラスのサンプルに示します。 <xref:System.Windows.Controls.Border.Padding%2A>プロパティは、指定した有効な子要素のサイズを拡大<xref:System.Windows.Thickness>値。  
  
 次の例は、適用する方法を示しています。<xref:System.Windows.Controls.Border.Padding%2A>を親に<xref:System.Windows.Controls.Border>要素。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>アプリケーションで配置、余白、パディングを利用する  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.Controls.Border.Padding%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、複雑なを作成するために必要な配置制御[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]します。 各プロパティの効果を利用し、子要素の配置を変更できます。動的なアプリケーション/ユーザー体験を生み出す柔軟性が与えられます。  
  
 次の例は、このトピックで説明した各概念を示しています。 このトピックでは、最初のサンプルにあるインフラストラクチャの構築には、この例で追加、<xref:System.Windows.Controls.Grid>要素の子として、<xref:System.Windows.Controls.Border>最初の例です。 <xref:System.Windows.Controls.Border.Padding%2A> 親に適用される<xref:System.Windows.Controls.Border>要素。 <xref:System.Windows.Controls.Grid> 3 つの子の間にスペースをパーティション分割するために使用<xref:System.Windows.Controls.StackPanel>要素。 <xref:System.Windows.Controls.Button> 要素をもう一度使用のさまざまな効果を表示する<xref:System.Windows.FrameworkElement.Margin%2A>と<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>します。 <xref:System.Windows.Controls.TextBlock> 各要素が追加<xref:System.Windows.Controls.ColumnDefinition>より適切に適用されるさまざまなプロパティを定義する、<xref:System.Windows.Controls.Button>各列内の要素。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 コンパイルすると、先のアプリケーションは次の図のような [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] になります。 要素間の間隔では、さまざまなプロパティ値の効果は、内の各列内の要素の重要なプロパティの値が示すように<xref:System.Windows.Controls.TextBlock>要素。  
  
 ![1 つのアプリケーション内の複数の配置プロパティ](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>次の内容  
 配置プロパティで定義されている、<xref:System.Windows.FrameworkElement>クラス内で要素配置の制御を有効にする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 これで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を利用して効果的に要素を配置するための手法を理解できたことでしょう。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトの詳細はその他の資料で確認できます。 [パネルの概要](../controls/panels-overview.md)トピックには、さまざまな詳細が含まれています。<xref:System.Windows.Controls.Panel>要素。 トピック[チュートリアル。初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)コンポーネントを配置して、その操作をデータ ソースにバインドするレイアウト要素を使用して高度な手法が導入されています。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [パネルの概要](../controls/panels-overview.md)
- [レイアウト](layout.md)
- [WPF レイアウト ギャラリー サンプル](https://go.microsoft.com/fwlink/?LinkID=160054)
