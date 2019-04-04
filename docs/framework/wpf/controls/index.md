---
title: コントロール
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: f4aeb3dd60186a4060f7825257c7adb274fc8b24
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363151"
---
# <a name="controls"></a>コントロール
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] など、ほとんどすべての Windows アプリケーションで使用される一般的な UI コンポーネントの多くに付属<xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.Menu>、および<xref:System.Windows.Controls.ListBox>します。 これまで、これらのオブジェクトはコントロールと呼ばれてきました。 中に、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK では引き続き"control"という用語を使用して、アプリケーションでは、表示可能なオブジェクトを表すクラスを広義に意味は、クラスが継承する必要がないことに注意してください、<xref:System.Windows.Controls.Control>クラスが表示されているかどうか。 継承するクラス、<xref:System.Windows.Controls.Control>クラスが含まれて、 <xref:System.Windows.Controls.ControlTemplate>、コントロールのコンシューマーは、新しいサブクラスを作成することがなく、コントロールの外観を大幅に変更することができます。  このトピックで説明する方法のコントロール (から継承された、<xref:System.Windows.Controls.Control>クラスとそうでないもの) でよく使用される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>コントロールのインスタンスの作成  
 コントロールをアプリケーションに追加するにはいずれかを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]またはコード。  次の例では、ユーザーに姓と名の入力を求める単純なアプリケーションの作成方法を示します。  この例は、6 つのコントロールを作成します。 2 つのラベル、2 つのテキスト ボックスでの 2 つのボタンや[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 どのコントロールも同じ方法で作成できます。  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 次の例では、同じアプリケーションをコードで作成します。 簡潔にするため、作成、 <xref:System.Windows.Controls.Grid>、 `grid1`、サンプルから除外しています。 `grid1` 上記のように同じ列と行の定義が[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例。  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>コントロールの外観の変更  
 通常は、アプリケーションの外観に合わせてコントロールの外観を変更します。 コントロールの外観を変更するには、目的に応じて、次のいずれかの手順を実行します。  
  
-   コントロールのプロパティ値を変更します。  
  
-   作成、<xref:System.Windows.Style>コントロール。  
  
-   新規作成<xref:System.Windows.Controls.ControlTemplate>コントロール。  
  
### <a name="changing-a-controls-property-value"></a>コントロールのプロパティ値の変更  
 多くのコントロールがコントロールの外観などを変更するためのプロパティを持つ、<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button>します。 両方の値のプロパティを設定する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]とコード。 次の例のセット、 <xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.FontSize%2A>、および<xref:System.Windows.Controls.Control.FontWeight%2A>プロパティを<xref:System.Windows.Controls.Button>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 次の例では、同じプロパティをコードで設定しています。  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>コントロールのスタイル作成  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 作成して、アプリケーションの各インスタンスのプロパティを設定する代わりに、コントロールの外観を指定する機能を提供する<xref:System.Windows.Style>します。 次の例では、作成、<xref:System.Windows.Style>それぞれに適用される<xref:System.Windows.Controls.Button>アプリケーションにします。 <xref:System.Windows.Style> 定義で通常[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で、<xref:System.Windows.ResourceDictionary>など、<xref:System.Windows.FrameworkElement.Resources%2A>のプロパティ、<xref:System.Windows.FrameworkElement>します。  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 キー、スタイルを割り当て、および内でそのキーを指定することによって、特定の種類の特定のコントロールのみにスタイルを適用することも、`Style`コントロールのプロパティ。  スタイルの詳細については、[スタイルとテンプレート](styling-and-templating.md)を参照してください。  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate の作成  
 A <xref:System.Windows.Style> 、一度に複数のコントロールのプロパティを設定することができますの外観をカスタマイズすることがあります、<xref:System.Windows.Controls.Control>を作成して行うことができますを超える、<xref:System.Windows.Style>します。 継承するクラス、<xref:System.Windows.Controls.Control>クラスが、 <xref:System.Windows.Controls.ControlTemplate>、構造との外観を定義する、<xref:System.Windows.Controls.Control>します。 <xref:System.Windows.Controls.Control.Template%2A>のプロパティを<xref:System.Windows.Controls.Control>付けることができますので、パブリックでは、 <xref:System.Windows.Controls.Control> 、<xref:System.Windows.Controls.ControlTemplate>は既定の異なる。 多くの場合、指定、新しいできます<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Control>の外観をカスタマイズするコントロールからの継承ではなく、 <xref:System.Windows.Controls.Control>。  
  
 非常に共通のコントロールについて考えてみます<xref:System.Windows.Controls.Button>します。  主な動作、<xref:System.Windows.Controls.Button>をユーザーがクリックしたときに、何らかのアクションを実行するアプリケーションを有効にします。  既定で、<xref:System.Windows.Controls.Button>で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]発生した四角形として表示されます。  動作を活用するために、アプリケーションの開発中にすることがあります、 <xref:System.Windows.Controls.Button>-は、ボタンのクリック イベントを処理することにより、ボタンのプロパティを変更することによって行うことができますを超えるボタンの外観を変更する可能性があります。  この場合、作成、新しい<xref:System.Windows.Controls.ControlTemplate>します。  
  
 次の例では、作成、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>します。  <xref:System.Windows.Controls.ControlTemplate>作成、<xref:System.Windows.Controls.Button>の角が丸いとグラデーションの背景を使用します。  <xref:System.Windows.Controls.ControlTemplate>が含まれています、<xref:System.Windows.Controls.Border>が<xref:System.Windows.Controls.Border.Background%2A>は、<xref:System.Windows.Media.LinearGradientBrush>の 2 つ<xref:System.Windows.Media.GradientStop>オブジェクト。  最初の<xref:System.Windows.Media.GradientStop>データ バインディングを使用してバインドする、<xref:System.Windows.Media.GradientStop.Color%2A>のプロパティ、<xref:System.Windows.Media.GradientStop>ボタンの背景の色にします。  設定すると、<xref:System.Windows.Controls.Control.Background%2A>のプロパティ、 <xref:System.Windows.Controls.Button>、その値の色が 1 つ目として使用される<xref:System.Windows.Media.GradientStop>します。 データ バインディングの詳細については、「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。 例でも作成、<xref:System.Windows.Trigger>の外観を変更する、<xref:System.Windows.Controls.Button>とき<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>は`true`します。  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A>のプロパティ、<xref:System.Windows.Controls.Button>に設定する必要があります、<xref:System.Windows.Media.SolidColorBrush>適切に機能する例。  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>イベントのサブスクライブ  
 コントロールのイベントを購読するには、いずれかを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]やコードのみを処理できるコードではイベントです。  次の例をサブスクライブする方法を示しています、`Click`のイベントを<xref:System.Windows.Controls.Button>します。  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 次の例のハンドル、`Click`のイベントを<xref:System.Windows.Controls.Button>します。  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>コントロールでのリッチ コンテンツ  
 ほとんどのクラスを継承するクラス、<xref:System.Windows.Controls.Control>クラス リッチ コンテンツを格納する容量があります。 たとえば、<xref:System.Windows.Controls.Label>文字列など、任意のオブジェクトを含めることができます、 <xref:System.Windows.Controls.Image>、または<xref:System.Windows.Controls.Panel>します。  次のクラスがリッチ コンテンツのサポートを提供し、ほとんどのコントロールの基本クラスとして機能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  
  
-   <xref:System.Windows.Controls.ContentControl>-このクラスから継承するクラスの例としては、 <xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.Button>、および<xref:System.Windows.Controls.ToolTip>します。  
  
-   <xref:System.Windows.Controls.ItemsControl>-このクラスから継承するクラスの例としては、 <xref:System.Windows.Controls.ListBox>、 <xref:System.Windows.Controls.Menu>、および<xref:System.Windows.Controls.Primitives.StatusBar>します。  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>-このクラスから継承するクラスの例としては、 <xref:System.Windows.Controls.TabItem>、 <xref:System.Windows.Controls.GroupBox>、および<xref:System.Windows.Controls.Expander>します。  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>-このクラスから継承するクラスの例としては、 <xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Controls.TreeViewItem>、および<xref:System.Windows.Controls.ToolBar>します。  

  
 これらの基本クラスの詳細については、[WPF コンテンツ モデル](wpf-content-model.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [スタイルとテンプレート](styling-and-templating.md)
- [カテゴリ別のコントロール](controls-by-category.md)
- [コントロール ライブラリ](control-library.md)
- [データ テンプレートの概要](../data/data-templating-overview.md)
- [データ バインディングの概要](../data/data-binding-overview.md)
- [入力](../advanced/input-wpf.md)
- [コマンドを有効にする](../advanced/how-to-enable-a-command.md)
- [チュートリアル: カスタム アニメーション ボタンを作成します。](walkthroughs-create-a-custom-animated-button.md)
- [コントロールのカスタマイズ](control-customization.md)
