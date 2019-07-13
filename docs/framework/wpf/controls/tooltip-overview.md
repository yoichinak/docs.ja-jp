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
ms.openlocfilehash: 097eb8c50a6a21f9d356aba562c95fd2d9d09022
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630771"
---
# <a name="tooltip-overview"></a>ToolTip の概要
ツールヒントは、ユーザーが経由の要素の上にマウス ポインターを置いたときに表示される小さいポップアップ ウィンドウ、<xref:System.Windows.Controls.Button>します。 このトピックでは、ツールヒントを紹介し、ツールヒントの内容を作成およびカスタマイズする方法について説明します。  

<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>ツールヒントとは  
 ツールヒントを持つ要素の上にマウス ポインターを置くと、一定の時間、ツールヒントの内容 (たとえば、コントロールの機能を説明するテキスト コンテンツ) を含むウィンドウが表示されます。 コントロールからマウス ポインターを移動すると、ツールヒントの内容がフォーカスを受け取ることができなくなるため、ウィンドウが消えます  
  
 ツールヒントの内容は、1 行または複数行のテキスト、イメージ、図形などのビジュアル コンテンツを含めることができます。 次のプロパティの 1 つをツールヒントの内容に設定することによって、コントロールのツールヒントを定義します。  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 使用するプロパティは、ツールヒントを定義するコントロールを継承するかどうかによって異なります、<xref:System.Windows.FrameworkContentElement>または<xref:System.Windows.FrameworkElement>クラス。  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>ツールヒントの作成  
 次の例では、設定して、単純なツールヒントを作成する方法を示しています、<xref:System.Windows.FrameworkElement.ToolTip%2A>プロパティを<xref:System.Windows.Controls.Button>をテキスト文字列に制御します。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 としてのツールヒントを定義することも、<xref:System.Windows.Controls.ToolTip>オブジェクト。 次の例では[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を指定する、<xref:System.Windows.Controls.ToolTip>オブジェクトのツールヒントとして、<xref:System.Windows.Controls.TextBox>要素。 例では、指定、<xref:System.Windows.Controls.ToolTip>を設定して、<xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>プロパティ。  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 次の例では、コードを使用して、生成する、<xref:System.Windows.Controls.ToolTip>オブジェクト。 例は、作成、 <xref:System.Windows.Controls.ToolTip> (`tt`) に関連付けますと、<xref:System.Windows.Controls.Button>します。  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 として定義されていないツールヒントの内容を作成することも、<xref:System.Windows.Controls.ToolTip>オブジェクトなどのレイアウト要素でツールヒントの内容を囲むことで、<xref:System.Windows.Controls.DockPanel>します。 次の例は、設定する方法を示します、<xref:System.Windows.FrameworkElement.ToolTip%2A>のプロパティを<xref:System.Windows.Controls.TextBox>で囲まれたコンテンツを<xref:System.Windows.Controls.DockPanel>コントロール。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>ToolTip クラスおよび ToolTipService クラスのプロパティの使用  
 ビジュアル プロパティを設定し、スタイルを適用して、ツールヒントの内容をカスタマイズできます。 コンテンツのツールヒントを定義する場合、<xref:System.Windows.Controls.ToolTip>オブジェクトのビジュアル プロパティを設定することができます、<xref:System.Windows.Controls.ToolTip>オブジェクト。 それ以外の場合、同等の添付プロパティを設定する必要があります、<xref:System.Windows.Controls.ToolTipService>クラス。  
  
 使用して、ツールヒントの内容の位置を指定するためにプロパティを設定する方法の例については、<xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ToolTipService>プロパティを参照してください[ToolTip を配置する](how-to-position-a-tooltip.md)します。  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>ツールヒントのスタイル設定  
 スタイルを設定することができます、<xref:System.Windows.Controls.ToolTip>カスタムを定義することで<xref:System.Windows.Style>します。 次の例では、定義、<xref:System.Windows.Style>と呼ばれる`Simple`の位置をオフセットする方法を示す、<xref:System.Windows.Controls.ToolTip>を設定してその外観を変更し、 <xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>、 <xref:System.Windows.Controls.Control.FontSize%2A>、および<xref:System.Windows.Controls.Control.FontWeight%2A>します。  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>ToolTipService の時間間隔プロパティの使用  
 <xref:System.Windows.Controls.ToolTipService>時間が表示されます、次のプロパティにツールヒントを設定するクラスが用意されています: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>、 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>、および<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>します。  
  
 使用、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>と<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>プロパティ遅延を指定する通常の簡単な前に、<xref:System.Windows.Controls.ToolTip>が表示されますとどのくらいの期間を指定することも、<xref:System.Windows.Controls.ToolTip>引き続き表示されます。 詳細については、「[方法 :ツールヒントの表示が遅延](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90))します。  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>プロパティは、それらのマウス ポインターをすばやく移動するときを初期遅延なしのさまざまなコントロールのツールヒントが表示されるかどうかを決定します。 詳細については、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>プロパティを参照してください[Use the BetweenShowDelay Property](how-to-use-the-betweenshowdelay-property.md)します。  
  
 次の例では、ツールヒントのこれらのプロパティを設定する方法を示します。  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [方法トピック](tooltip-how-to-topics.md)
