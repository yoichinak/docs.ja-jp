---
title: コントロール
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: faa1fbad85acf5788c10de7750c6a7c32b535bf5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957031"
---
# <a name="controls"></a>コントロール
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Controls.Button>には、 、<xref:System.Windows.Controls.Menu>、、、など、ほぼすべての Windows アプリケーションで使用される共通の UI コンポーネントの多くが付属しています。<xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Label> これまで、これらのオブジェクトはコントロールと呼ばれてきました。 SDK は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、アプリケーション内の表示されたオブジェクトを表すクラスを厳密には "コントロール" として使用しますが、クラスは、表示可能なプレゼンスを持つように<xref:System.Windows.Controls.Control>クラスを継承する必要がないことに注意することが重要です。 <xref:System.Windows.Controls.Control>クラスを継承するクラスには<xref:System.Windows.Controls.ControlTemplate>が含まれています。これにより、コントロールのコンシューマーは、新しいサブクラスを作成しなくても、コントロールの外観を根本的に変更できます。  このトピックでは、で一般的に使用されるコントロール ( <xref:System.Windows.Controls.Control>クラスを継承するコントロールと、そうでないもの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の両方) について説明します。  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>コントロールのインスタンスの作成  
 コントロールは、またはのいずれか[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]のコードを使用して、アプリケーションに追加できます。  次の例では、ユーザーに姓と名の入力を求める単純なアプリケーションの作成方法を示します。  この例では、2つのラベル、2つのテキストボックス、2つ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のボタン () を作成します。 どのコントロールも同じ方法で作成できます。  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 次の例では、同じアプリケーションをコードで作成します。 簡潔にするために、の<xref:System.Windows.Controls.Grid>作成`grid1`はサンプルから除外されています。 `grid1`には、前[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の例で示したのと同じ列と行の定義があります。  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>コントロールの外観の変更  
 通常は、アプリケーションの外観に合わせてコントロールの外観を変更します。 コントロールの外観を変更するには、目的に応じて、次のいずれかの手順を実行します。  
  
- コントロールのプロパティ値を変更します。  
  
- コントロールの<xref:System.Windows.Style>を作成します。  
  
- コントロールに新しい<xref:System.Windows.Controls.ControlTemplate>を作成します。  
  
### <a name="changing-a-controls-property-value"></a>コントロールのプロパティ値の変更  
 <xref:System.Windows.Controls.Control.Background%2A> 多く<xref:System.Windows.Controls.Button>のコントロールには、のなど、コントロールの表示方法を変更できるプロパティがあります。 値のプロパティは、とコードの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]両方で設定できます。 <xref:System.Windows.Controls.Control.Background%2A>次の例<xref:System.Windows.Controls.Button>で<xref:System.Windows.Controls.Control.FontWeight%2A> <xref:System.Windows.Controls.Control.FontSize%2A>は[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、ので、、およびの各プロパティを設定します。  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 次の例では、同じプロパティをコードで設定しています。  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>コントロールのスタイル作成  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用すると、アプリケーションの各インスタンスにプロパティを設定する代わりに、を<xref:System.Windows.Style>作成することによって、コントロールの外観を指定できます。 次の例では<xref:System.Windows.Style> 、アプリケーションの各<xref:System.Windows.Controls.Button>に適用されるを作成します。 <xref:System.Windows.Style>定義は、通常、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の<xref:System.Windows.FrameworkElement.Resources%2A>プロパティ<xref:System.Windows.ResourceDictionary> <xref:System.Windows.FrameworkElement>など、で定義されます。  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 また、スタイルにキーを割り当て、コントロールの`Style`プロパティでそのキーを指定することによって、特定の種類の特定のコントロールにのみスタイルを適用できます。  スタイルの詳細については、「スタイル[とテンプレート](styling-and-templating.md)」を参照してください。  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate の作成  
 を<xref:System.Windows.Style>使用すると、一度に複数のコントロールのプロパティを設定でき<xref:System.Windows.Style>ますが、を作成することによっ<xref:System.Windows.Controls.Control>て行うことのできないの外観をカスタマイズすることもできます。 <xref:System.Windows.Controls.Control>クラスを継承するクラスには<xref:System.Windows.Controls.ControlTemplate>、の<xref:System.Windows.Controls.Control>構造と外観を定義するがあります。 のプロパティはパブリックである<xref:System.Windows.Controls.Control>ため、既定値とは異なる<xref:System.Windows.Controls.ControlTemplate>を指定できます。 <xref:System.Windows.Controls.Control.Template%2A> <xref:System.Windows.Controls.Control> 多くの場合、コントロールから<xref:System.Windows.Controls.ControlTemplate>継承する<xref:System.Windows.Controls.Control>のではなく、の新しいを指定することで<xref:System.Windows.Controls.Control>、の外観をカスタマイズできます。  
  
 非常に一般的なコントロールで<xref:System.Windows.Controls.Button>あるを考えてみましょう。  の主な動作<xref:System.Windows.Controls.Button>は、アプリケーションがユーザーがクリックしたときに何らかのアクションを実行できるようにすることです。  既定では、 <xref:System.Windows.Controls.Button>の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は浮き出し四角形として表示されます。  アプリケーションの開発中に、ボタンのクリックイベントを処理することによっ<xref:System.Windows.Controls.Button>て、の動作を利用することができます。ただし、ボタンのプロパティを変更することにより、ボタンの外観を変更することはできません。  この場合は、新しい<xref:System.Windows.Controls.ControlTemplate>を作成できます。  
  
 次の例では<xref:System.Windows.Controls.ControlTemplate> 、 <xref:System.Windows.Controls.Button>のを作成します。  は<xref:System.Windows.Controls.ControlTemplate> 、角<xref:System.Windows.Controls.Button>が丸く、グラデーションの背景を持つを作成します。  <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Border>は、2つ<xref:System.Windows.Controls.ControlTemplate> のオブジェクトを持つを持つを<xref:System.Windows.Media.LinearGradientBrush>格納します。 <xref:System.Windows.Media.GradientStop>  最初<xref:System.Windows.Media.GradientStop>のは、データバインディングを使用<xref:System.Windows.Media.GradientStop.Color%2A>して、 <xref:System.Windows.Media.GradientStop>のプロパティをボタンの背景の色にバインドします。  <xref:System.Windows.Controls.Control.Background%2A>のプロパティを設定すると、その値の色が最初<xref:System.Windows.Media.GradientStop>の値として使用されます。 <xref:System.Windows.Controls.Button> データ バインディングの詳細については、「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。 また、この例で<xref:System.Windows.Trigger>は、が`true`の<xref:System.Windows.Controls.Button>場合に<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>の外観を変更するを作成します。  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> 例を正しく動作<xref:System.Windows.Controls.Button>させるには、 <xref:System.Windows.Media.SolidColorBrush>のプロパティをに設定する必要があります。<xref:System.Windows.Controls.Control.Background%2A>  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>イベントのサブスクライブ  
 コントロールのイベントをサブスクライブするに[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、またはコードを使用しますが、イベントを処理できるのはコードのみです。  次の例は、 `Click` <xref:System.Windows.Controls.Button>のイベントをサブスクライブする方法を示しています。  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 `Click` 次<xref:System.Windows.Controls.Button>の例では、のイベントを処理します。  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>コントロールでのリッチ コンテンツ  
 <xref:System.Windows.Controls.Control>クラスを継承するほとんどのクラスは、豊富なコンテンツを格納できる容量を備えています。 たとえば、に<xref:System.Windows.Controls.Label>は、文字列<xref:System.Windows.Controls.Image>、、または<xref:System.Windows.Controls.Panel>など、任意のオブジェクトを含めることができます。  次のクラスは、リッチコンテンツをサポートし、の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ほとんどのコントロールの基本クラスとして機能します。  
  
- <xref:System.Windows.Controls.ContentControl>--このクラスを継承するクラスの例と<xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.ToolTip>して<xref:System.Windows.Controls.Button>、、、があります。  
  
- <xref:System.Windows.Controls.ItemsControl>--このクラスを継承するクラスの例と<xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.Primitives.StatusBar>して<xref:System.Windows.Controls.Menu>、、、があります。  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--このクラスを継承するクラスの例と<xref:System.Windows.Controls.TabItem> <xref:System.Windows.Controls.Expander>して<xref:System.Windows.Controls.GroupBox>、、、があります。  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--このクラスを継承するクラスの例と<xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ToolBar>して<xref:System.Windows.Controls.TreeViewItem>、、、があります。  

 これらの基本クラスの詳細については、「 [WPF コンテンツモデル](wpf-content-model.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [スタイルとテンプレート](styling-and-templating.md)
- [カテゴリ別のコントロール](controls-by-category.md)
- [コントロール ライブラリ](control-library.md)
- [データ テンプレートの概要](../data/data-templating-overview.md)
- [データ バインディングの概要](../data/data-binding-overview.md)
- [入力](../advanced/input-wpf.md)
- [コマンドを有効にする](../advanced/how-to-enable-a-command.md)
- [チュートリアル: カスタムのアニメーションボタンを作成する](walkthroughs-create-a-custom-animated-button.md)
- [コントロールのカスタマイズ](control-customization.md)
