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
ms.openlocfilehash: bf351b6df972dc992f214ddfe899bfa808d0cd53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963636"
---
# <a name="alignment-margins-and-padding-overview"></a>配置、余白、パディングの概要
クラス<xref:System.Windows.FrameworkElement>は、子要素を正確に配置するために使用されるいくつかのプロパティを公開します。 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>このトピック<xref:System.Windows.FrameworkElement.Margin%2A>では<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、、、 、およびの4つの最も重要なプロパティについて説明します。<xref:System.Windows.Controls.Border.Padding%2A> これらのプロパティの効果を理解することが重要です。[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの要素の位置を制御するための基本となるためです。  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>要素配置の概要  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を利用し、さまざまな方法で要素を配置できます。 ただし、最適なレイアウトを実現するには、 <xref:System.Windows.Controls.Panel>単に適切な要素を選択するだけではありません。 配置を細かく制御する<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>には<xref:System.Windows.Controls.Border.Padding%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、、、およびの<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>各プロパティについて理解している必要があります。  
  
 次の図は、いくつかの配置プロパティを利用したレイアウト シナリオのものです。  
  
 ![WPF 位置決めプロパティのサンプル](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 一見すると、この<xref:System.Windows.Controls.Button>図の要素はランダムに配置されているように見えることがあります。 しかしながら、位置は実際のところ、余白、配置、パディングを組み合わせることで正確に制御されます。  
  
 次の例は、前の図のレイアウトの作成方法を示しています。 要素<xref:System.Windows.Controls.Border>は親<xref:System.Windows.Controls.StackPanel>をカプセル化し、 <xref:System.Windows.Controls.Border.Padding%2A>値は15デバイス非依存ピクセルになります。 <xref:System.Windows.Media.Brushes.LightBlue%2A> 子<xref:System.Windows.Controls.StackPanel>を囲むナローバンドのこのアカウント。 の子要素は<xref:System.Windows.Controls.StackPanel> 、このトピックで詳しく説明されているさまざまな配置プロパティを示すために使用されます。 プロパティ<xref:System.Windows.Controls.Button> <xref:System.Windows.FrameworkElement.Margin%2A>とプロパティ<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>の両方を示すために、3つの要素が使用されます。  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 次の図は、前のサンプルで使用されたさまざまな配置プロパティを大写しにしたものです。 このトピックの後続のセクションでは、各配置プロパティの使用方法をさらに詳しく説明します。  
  
 ![配置プロパティ (解説付き)](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>配置プロパティを理解する  
 プロパティ<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティは、親要素に割り当てられたレイアウト領域内に子要素を配置する方法を記述します。 これらのプロパティを一緒に使用することで、子要素を正確に配置できます。 たとえば<xref:System.Windows.Controls.DockPanel> 、の子要素では<xref:System.Windows.HorizontalAlignment.Right> <xref:System.Windows.HorizontalAlignment.Left>、、、また<xref:System.Windows.HorizontalAlignment.Center>はの4つの異なる水平方向の<xref:System.Windows.HorizontalAlignment.Stretch>配置を指定できます。または、を使用して、使用可能な領域を塗りつぶすことができます。 垂直配置にも同様の値を利用できます。  
  
> [!NOTE]
> 明示的に<xref:System.Windows.FrameworkElement.Height%2A>設定<xref:System.Windows.FrameworkElement.Width%2A>された要素のプロパティは、 <xref:System.Windows.HorizontalAlignment.Stretch>プロパティの値よりも優先されます。 <xref:System.Windows.FrameworkElement.Height%2A>、 `Stretch` 、およびの`Stretch`値を設定しようとすると、要求は無視されます。 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Width%2A>  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment プロパティ  
 プロパティ<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>は、子要素に適用する水平方向の配置特性を宣言します。 次の表に、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティの使用可能な値を示します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|子要素は、親要素に割り当てられたレイアウト領域の左に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Center>|子要素は、親要素に割り当てられたレイアウト領域の中央に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Right>|子要素は、親要素に割り当てられたレイアウト領域の右に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Stretch>標準|子要素は引き伸ばされ、親要素に割り当てられたレイアウト領域を埋めます。 明示<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.FrameworkElement.Height%2A>な値と値が優先されます。|  
  
 次の例は、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを要素に<xref:System.Windows.Controls.Button>適用する方法を示しています。 各属性値が示され、さまざまなレンダリング動作をより良く表しています。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 前のコードは次の画像のようなレイアウトを作ります。 各<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>値の配置効果が図に表示されます。  
  
 ![HorizontalAlignment のサンプル](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment プロパティ  
 プロパティ<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>は、子要素に適用する垂直方向の配置特性を記述します。 次の表に、 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティに使用できる値を示します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|子要素は、親要素に割り当てられたレイアウト領域の上に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Center>|子要素は、親要素に割り当てられたレイアウト領域の中央に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Bottom>|子要素は、親要素に割り当てられたレイアウト領域の下に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Stretch>標準|子要素は引き伸ばされ、親要素に割り当てられたレイアウト領域を埋めます。 明示<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.FrameworkElement.Height%2A>な値と値が優先されます。|  
  
 次の例は、 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを要素に<xref:System.Windows.Controls.Button>適用する方法を示しています。 各属性値が示され、さまざまなレンダリング動作をより良く表しています。 このサンプルでは、 <xref:System.Windows.Controls.Grid>表示されるグリッド線を持つ要素を親として使用し、各プロパティ値のレイアウト動作をわかりやすく示します。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 前のコードは次の画像のようなレイアウトを作ります。 各<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>値の配置効果が図に表示されます。  
  
 ![VerticalAlignment プロパティのサンプル](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>余白プロパティを理解する  
 プロパティ<xref:System.Windows.FrameworkElement.Margin%2A>は、要素とその子またはピア間の距離を表します。 <xref:System.Windows.FrameworkElement.Margin%2A>値は、のような`Margin="20"`構文を使用して一様にすることができます。 この構文では、デバイス<xref:System.Windows.FrameworkElement.Margin%2A>に依存しない一様なピクセルが要素に適用されます。 <xref:System.Windows.FrameworkElement.Margin%2A>また、値には、4つの異なる値の形式を使用できます。各値は、のよう`Margin="0,10,5,25"`に、左、上、右、下に適用する個別の余白を記述します。 <xref:System.Windows.FrameworkElement.Margin%2A>プロパティを適切に使用すると、要素のレンダリング位置とその近隣要素と子のレンダリング位置を細かく制御できます。  
  
> [!NOTE]
> 0以外の余白は、要素の<xref:System.Windows.FrameworkElement.ActualWidth%2A>および<xref:System.Windows.FrameworkElement.ActualHeight%2A>の外側にスペースを適用します。  
  
 次の例では、要素の<xref:System.Windows.Controls.Button>グループの周りに均一な余白を適用する方法を示します。 各<xref:System.Windows.Controls.Button>要素には、それぞれの方向に10ピクセルの余白バッファーが等間隔で配置されます。  
  
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
 パディングは、ほとんど<xref:System.Windows.FrameworkElement.Margin%2A>の点でに似ています。 Padding プロパティは、いくつかのクラスでのみ公開さ<xref:System.Windows.Documents.Block>れます。主に便利なのは<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.Control>、 <xref:System.Windows.Controls.Border>、、、および padding プロパティを公開するクラスのサンプルです。 プロパティ<xref:System.Windows.Controls.Border.Padding%2A>は、指定された<xref:System.Windows.Thickness>値で子要素の有効なサイズを拡大します。  
  
 次の例は、を親<xref:System.Windows.Controls.Border.Padding%2A> <xref:System.Windows.Controls.Border>要素に適用する方法を示しています。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>アプリケーションで配置、余白、パディングを利用する  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>は、複雑なを作成するために必要な配置コントロールを提供します。 <xref:System.Windows.Controls.Border.Padding%2A> 各プロパティの効果を利用し、子要素の配置を変更できます。動的なアプリケーション/ユーザー体験を生み出す柔軟性が与えられます。  
  
 次の例は、このトピックで説明した各概念を示しています。 このトピックの最初のサンプルにあるインフラストラクチャを基にして構築され<xref:System.Windows.Controls.Grid>たこの例では<xref:System.Windows.Controls.Border> 、最初のサンプルでのの子として要素を追加します。 <xref:System.Windows.Controls.Border.Padding%2A>は、親<xref:System.Windows.Controls.Border>要素に適用されます。 は<xref:System.Windows.Controls.Grid> 、3つの子<xref:System.Windows.Controls.StackPanel>要素の間にスペースを分割するために使用されます。 <xref:System.Windows.Controls.Button>要素は、と<xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>のさまざまな効果を示すために再び使用されます。 <xref:System.Windows.Controls.TextBlock>各列の<xref:System.Windows.Controls.Button>要素に<xref:System.Windows.Controls.ColumnDefinition>適用されるさまざまなプロパティをより適切に定義するために、それぞれに要素が追加されています。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 コンパイルすると、先のアプリケーションは次の図のような [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] になります。 さまざまなプロパティ値の影響は、要素間の間隔で明確に示され、各列の要素の重要なプロパティ値<xref:System.Windows.Controls.TextBlock>が要素内に表示されます。  
  
 ![1 つのアプリケーション内の複数の配置プロパティ](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>次の内容  
 クラスで定義され<xref:System.Windows.FrameworkElement>たプロパティを配置すると、アプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内の要素の配置を細かく制御できます。 これで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を利用して効果的に要素を配置するための手法を理解できたことでしょう。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトの詳細はその他の資料で確認できます。 [パネルの概要](../controls/panels-overview.md)に関するトピックには、さまざま<xref:System.Windows.Controls.Panel>な要素の詳細が含まれています。 「 [チュートリアル:最初の WPF デスクトップアプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)では、レイアウト要素を使用してコンポーネントを配置し、それらのアクションをデータソースにバインドする高度な手法が導入されています。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [パネルの概要](../controls/panels-overview.md)
- [レイアウト](layout.md)
- [WPF レイアウト ギャラリー サンプル](https://go.microsoft.com/fwlink/?LinkID=160054)
