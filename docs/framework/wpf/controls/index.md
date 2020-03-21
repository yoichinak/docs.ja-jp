---
title: コントロール
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 2ec8c0a99f4e2431aed0d8c24168b7329de669f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187526"
---
# <a name="controls"></a>コントロール
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]には、 <xref:System.Windows.Controls.Button>、 、 <xref:System.Windows.Controls.Label>、、<xref:System.Windows.Controls.TextBox>および など、ほぼすべての Windows アプリケーションで使用される共通<xref:System.Windows.Controls.Menu>UI<xref:System.Windows.Controls.ListBox>コンポーネントが多数含まれています。 これまで、これらのオブジェクトはコントロールと呼ばれてきました。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK は、アプリケーション内の可視オブジェクトを表すクラスをゆるやかに意味するために、「control」という用語を使用し続けますが、クラスが存在する場合は<xref:System.Windows.Controls.Control>クラスから継承する必要はありません。 <xref:System.Windows.Controls.Control>クラスから継承するクラスには<xref:System.Windows.Controls.ControlTemplate>、コントロールのコンシューマーが、新しいサブクラスを作成しなくてもコントロールの外観を根本的に変更できるようにする が含まれます。  ここでは、クラスから継承するコントロールと継承しないコントロールの<xref:System.Windows.Controls.Control>両方が、 でよく[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用される方法について説明します。  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>コントロールのインスタンスの作成  
 コントロールは、どちらかまたは[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]コードを使用してアプリケーションに追加できます。  次の例では、ユーザーに姓と名の入力を求める単純なアプリケーションの作成方法を示します。  この例では、6 つのコントロール (2 つのラベル、2 つの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]テキスト ボックス、2 つのボタン) を作成します。 どのコントロールも同じ方法で作成できます。  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 次の例では、同じアプリケーションをコードで作成します。 簡潔にするために<xref:System.Windows.Controls.Grid>、 の`grid1`作成はサンプルから除外されています。 `grid1`は、前の例に示した列と行の定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]と同じです。  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>コントロールの外観の変更  
 通常は、アプリケーションの外観に合わせてコントロールの外観を変更します。 コントロールの外観を変更するには、目的に応じて、次のいずれかの手順を実行します。  
  
- コントロールのプロパティ値を変更します。  
  
- コントロールの<xref:System.Windows.Style>を作成します。  
  
- コントロールの新<xref:System.Windows.Controls.ControlTemplate>しいコントロールを作成します。  
  
### <a name="changing-a-controls-property-value"></a>コントロールのプロパティ値の変更  
 多くのコントロールには、コントロールの表示<xref:System.Windows.Controls.Control.Background%2A>方法を変更できるプロパティがあります。 <xref:System.Windows.Controls.Button> 値のプロパティは、コードと両方[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で設定できます。 <xref:System.Windows.Controls.Control.Background%2A>次の例では、<xref:System.Windows.Controls.Control.FontSize%2A>の<xref:System.Windows.Controls.Control.FontWeight%2A>プロパティ 、、および プロパティを<xref:System.Windows.Controls.Button>設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 次の例では、同じプロパティをコードで設定しています。  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>コントロールのスタイル作成  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を作成することにより、アプリケーション内の各インスタンスにプロパティを設定する代わりに、コントロールの外観を指定する必要があります<xref:System.Windows.Style>。 次の例では、<xref:System.Windows.Style>アプリケーション内の各<xref:System.Windows.Controls.Button>アプリケーションに適用される を作成します。 <xref:System.Windows.Style>定義は通常、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の<xref:System.Windows.ResourceDictionary>プロパティなど で<xref:System.Windows.FrameworkElement.Resources%2A>定義されます<xref:System.Windows.FrameworkElement>。  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 また、スタイルにキーを割り当て、コントロールのプロパティでそのキーを指定することで、特定の種類の特定のコントロールにのみスタイル`Style`を適用することもできます。  スタイルの詳細については、「[スタイルとテンプレート](styling-and-templating.md)」を参照してください。  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate の作成  
 A<xref:System.Windows.Style>を使用すると、一度に複数の<xref:System.Windows.Controls.Control>コントロールにプロパティを設定できますが、<xref:System.Windows.Style>を作成して、その外観をカスタマイズする必要がある場合があります。 クラスから継承する<xref:System.Windows.Controls.Control>クラスには、<xref:System.Windows.Controls.ControlTemplate>の構造と外観を定義する<xref:System.Windows.Controls.Control>が、 が含まれます。 の<xref:System.Windows.Controls.Control.Template%2A><xref:System.Windows.Controls.Control>プロパティはパブリックなので、デフォルトとは異なる<xref:System.Windows.Controls.Control>を<xref:System.Windows.Controls.ControlTemplate>与えることができます。 多くの場合、コントロールから<xref:System.Windows.Controls.ControlTemplate>継承する<xref:System.Windows.Controls.Control>代わりに、 に新しいを指定して、 の<xref:System.Windows.Controls.Control>外観をカスタマイズできます。  
  
 非常に一般的なコントロール<xref:System.Windows.Controls.Button>を考えてみましょう。  a の主な<xref:System.Windows.Controls.Button>動作は、ユーザーがアプリケーションをクリックしたときに、アプリケーションが何らかのアクションを実行できるようにすることです。  既定では、in <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、上げられた四角形として表示されます。  アプリケーションの開発中に、<xref:System.Windows.Controls.Button>ボタンのクリック イベントを処理することで 、ボタンの動作を利用する必要がありますが、ボタンのプロパティを変更することで、ボタンの外観を変更する場合があります。  この場合、新しい<xref:System.Windows.Controls.ControlTemplate>を作成できます。  
  
 次の例では、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>を作成します。  は<xref:System.Windows.Controls.ControlTemplate>、角<xref:System.Windows.Controls.Button>が丸くグラデーションの背景を持つ を作成します。  に<xref:System.Windows.Controls.ControlTemplate>2 <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Border.Background%2A>つの<xref:System.Windows.Media.GradientStop>オブジェクト<xref:System.Windows.Media.LinearGradientBrush>を持つ が含まれます。  最初<xref:System.Windows.Media.GradientStop>のプロパティは、データ バインディング<xref:System.Windows.Media.GradientStop.Color%2A>を使用して<xref:System.Windows.Media.GradientStop>、 のプロパティをボタンの背景の色にバインドします。  のプロパティ<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Button>を設定すると、その値の色が最初<xref:System.Windows.Media.GradientStop>の として使用されます。 データ バインディングの詳細については、「[データ バインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)」を参照してください。 この例では、 <xref:System.Windows.Trigger> when<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>の外観を変更する`true`を作成します。  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> の<xref:System.Windows.Controls.Control.Background%2A>プロパティは、<xref:System.Windows.Controls.Button>例が正しく動作<xref:System.Windows.Media.SolidColorBrush>するためににに設定する必要があります。  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>イベントのサブスクライブ  
 コントロールのイベントをサブスクライブするには、コードまたはコードを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用しますが、コード内で処理できるのはイベントだけです。  次の例は、 の`Click`イベントをサブスクライブする方法<xref:System.Windows.Controls.Button>を示しています。  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 次の例では、`Click`のイベント<xref:System.Windows.Controls.Button>を処理します。  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>コントロールでのリッチ コンテンツ  
 <xref:System.Windows.Controls.Control>クラスから継承するほとんどのクラスには、リッチ コンテンツを含める機能があります。 たとえば、 には<xref:System.Windows.Controls.Label>、文字列、、、、、、a など<xref:System.Windows.Controls.Image>、任意の<xref:System.Windows.Controls.Panel>オブジェクトを含めることができます。  次のクラスは、リッチ コンテンツをサポートし、 の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの大部分の基本クラスとして機能します。  
  
- <xref:System.Windows.Controls.ContentControl>-- このクラスから継承するクラスの例として<xref:System.Windows.Controls.Label>は<xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.ToolTip>、、 、および が挙げられます。  
  
- <xref:System.Windows.Controls.ItemsControl>-- このクラスから継承するクラスの例として<xref:System.Windows.Controls.ListBox>は<xref:System.Windows.Controls.Menu>、 <xref:System.Windows.Controls.Primitives.StatusBar>、、 、および が挙げられます。  
  
- <xref:System.Windows.Controls.HeaderedContentControl>-- このクラスから継承するクラスの例として<xref:System.Windows.Controls.TabItem>は<xref:System.Windows.Controls.GroupBox>、 <xref:System.Windows.Controls.Expander>、、 、および が挙げられます。  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>-- このクラスから継承するクラスの例として<xref:System.Windows.Controls.MenuItem>は<xref:System.Windows.Controls.TreeViewItem>、 <xref:System.Windows.Controls.ToolBar>、、および が挙げられます。  

 これらの基本クラスの詳細については、「 [WPF コンテンツ モデル](wpf-content-model.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [スタイルとテンプレート](styling-and-templating.md)
- [カテゴリ別のコントロール](controls-by-category.md)
- [コントロール ライブラリ](control-library.md)
- [データ テンプレートの概要](../data/data-templating-overview.md)
- [データバインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)
- [入力](../advanced/input-wpf.md)
- [コマンドを有効にする](../advanced/how-to-enable-a-command.md)
- [チュートリアル: カスタム アニメーション ボタンの作成](walkthroughs-create-a-custom-animated-button.md)
- [コントロールのカスタマイズ](control-customization.md)
