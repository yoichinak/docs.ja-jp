---
title: ToolTip の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181946"
---
# <a name="tooltip-overview"></a>ToolTip の概要
ツールヒントは、ユーザーが要素の上にマウス ポインタを置くと表示される小さなポップアップ ウィンドウです<xref:System.Windows.Controls.Button>。 このトピックでは、ツールヒントを紹介し、ツールヒントの内容を作成およびカスタマイズする方法について説明します。  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a>ツールヒントとは  
 ツールヒントを持つ要素の上にマウス ポインターを置くと、一定の時間、ツールヒントの内容 (たとえば、コントロールの機能を説明するテキスト コンテンツ) を含むウィンドウが表示されます。 コントロールからマウス ポインターを移動すると、ツールヒントの内容がフォーカスを受け取ることができなくなるため、ウィンドウが消えます  
  
 ツールヒントの内容は、1 行または複数行のテキスト、イメージ、図形などのビジュアル コンテンツを含めることができます。 次のプロパティの 1 つをツールヒントの内容に設定することによって、コントロールのツールヒントを定義します。  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 使用するプロパティは、ツールヒントを定義するコントロールが<xref:System.Windows.FrameworkContentElement>クラスまたは<xref:System.Windows.FrameworkElement>クラスから継承するかどうかによって異なります。  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a>ツールヒントの作成  
 コントロールの<xref:System.Windows.FrameworkElement.ToolTip%2A>プロパティをテキスト文字列に設定して、簡単なツールヒントを作成<xref:System.Windows.Controls.Button>する方法を次の例に示します。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 ツールチップを<xref:System.Windows.Controls.ToolTip>オブジェクトとして定義することもできます。 次の例では[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、要素の<xref:System.Windows.Controls.ToolTip>ツールヒントとしてオブジェクトを指定<xref:System.Windows.Controls.TextBox>します。 この例では、プロパティを<xref:System.Windows.Controls.ToolTip>設定することによって<xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>を指定しています。  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 次の例では、コードを使用<xref:System.Windows.Controls.ToolTip>してオブジェクトを生成します。 この例では、 <xref:System.Windows.Controls.ToolTip> `tt`( ) を作成し<xref:System.Windows.Controls.Button>、 に関連付けます。  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 また、 など、レイアウト要素にツールヒントコンテンツを<xref:System.Windows.Controls.ToolTip>囲むことで、オブジェクトとして定義されていないツールヒントコンテンツを<xref:System.Windows.Controls.DockPanel>作成することもできます。 コントロールに囲まれたコンテンツに<xref:System.Windows.FrameworkElement.ToolTip%2A>プロパティを設定する方法<xref:System.Windows.Controls.TextBox>を次の例に<xref:System.Windows.Controls.DockPanel>示します。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>ToolTip クラスおよび ToolTipService クラスのプロパティの使用  
 ビジュアル プロパティを設定し、スタイルを適用して、ツールヒントの内容をカスタマイズできます。 ツールヒントの内容を<xref:System.Windows.Controls.ToolTip>オブジェクトとして定義する場合は、オブジェクトの表示プロパティを<xref:System.Windows.Controls.ToolTip>設定できます。 それ以外の場合は、クラスに対応する<xref:System.Windows.Controls.ToolTipService>添付プロパティを設定する必要があります。  
  
 プロパティとプロパティを使用して<xref:System.Windows.Controls.ToolTip>ツールヒント コンテンツの位置を指定するために<xref:System.Windows.Controls.ToolTipService>プロパティを設定する方法の例については、「[ツールヒントの配置](how-to-position-a-tooltip.md)」を参照してください。  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a>ツールヒントのスタイル設定  
 カスタム<xref:System.Windows.Style>を定義<xref:System.Windows.Controls.ToolTip>して スタイルを設定できます。 次の例では、 <xref:System.Windows.Style> `Simple` 、 <xref:System.Windows.Controls.Control.Foreground%2A>、、<xref:System.Windows.Controls.Control.FontSize%2A>および<xref:System.Windows.Controls.Control.FontWeight%2A>を設定して<xref:System.Windows.Controls.ToolTip>、 の配置をオフセットし<xref:System.Windows.Controls.Control.Background%2A>、その外観を変更する方法を示す呼び出しを定義します。  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>ToolTipService の時間間隔プロパティの使用  
 この<xref:System.Windows.Controls.ToolTipService>クラスには、ツールヒントの表示時間 、、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A><xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>および を設定するための<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>プロパティが用意されています。  
  
 プロパティと<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A><xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>プロパティを使用して、表示される前の遅延<xref:System.Windows.Controls.ToolTip>(通常は短い) を<xref:System.Windows.Controls.ToolTip>指定し、表示状態を維持する期間を指定します。 詳細については、「[ How to: Delay the Display of a ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90))」を参照してください。  
  
 この<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>プロパティは、マウス ポインターをすばやく移動したときに、コントロールごとにツールヒントを初期遅延なしで表示するかどうかを決定します。 プロパティの<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>詳細については、「[ビトビトルーディ プロパティの使用](how-to-use-the-betweenshowdelay-property.md)」を参照してください。  
  
 次の例では、ツールヒントのこれらのプロパティを設定する方法を示します。  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [ハウツートピック](tooltip-how-to-topics.md)
