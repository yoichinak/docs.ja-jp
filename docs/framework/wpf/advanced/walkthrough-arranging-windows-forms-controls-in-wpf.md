---
title: 'チュートリアル: WPF での Windows フォーム コントロールの配置'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 5b759baebb7192c1ee94b4aa925198864ba7a31a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338775"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>チュートリアル: WPF での Windows フォーム コントロールの配置
このチュートリアルは、使用する方法を示します[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を配置するためのレイアウト機能[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ハイブリッド アプリケーションでコントロールできます。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   既定のレイアウト設定の使用。  
  
-   コンテンツに合わせたサイズの変更。  
  
-   絶対配置の使用。  
  
-   サイズの明示的な指定。  
  
-   レイアウト プロパティの設定。  
  
-   z オーダーの制限の理解。  
  
-   ドッキング。  
  
-   可視性の設定。  
  
-   伸縮しないコントロールのホスト。  
  
-   スケーリング。  
  
-   回転。  
  
-   パディングとマージンの設定。  
  
-   動的レイアウト コンテナーの使用。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、次を参照してください。 [WPF のサンプルを使用した Windows フォーム コントロールを配置する](https://go.microsoft.com/fwlink/?LinkID=159971)します。  
  
 理解する必要が完了したら、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]レイアウト機能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーション。  
  
## <a name="prerequisites"></a>必須コンポーネント  

このチュートリアルを完了するには Visual Studio が必要です。
  
## <a name="creating-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには  
  
1. という名前の WPF アプリケーション プロジェクトを作成する`WpfLayoutHostingWf`します。  
  
2. ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3. MainWindow.xaml をダブルクリックして、XAML ビューで開きます。  
  
4. <xref:System.Windows.Window>要素では、次の追加[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名前空間のマッピング。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <xref:System.Windows.Controls.Grid>要素が設定されて、<xref:System.Windows.Controls.Grid.ShowGridLines%2A>プロパティを`true`し、5 つの行と 3 つの列を定義します。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>既定のレイアウト設定の使用  
 既定で、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が、ホストされるレイアウトを処理[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
#### <a name="to-use-default-layout-settings"></a>既定のレイアウト設定を使用するには  
  
1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2. F5 キーを押してアプリケーションをビルドし、実行します。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType>コントロールに表示され、<xref:System.Windows.Controls.Canvas>します。 ホストされるコントロールのサイズは、その内容に基づいて、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素のサイズは、ホストされるコントロールに対応します。  
  
## <a name="sizing-to-content"></a>コンテンツに合わせたサイズの変更  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素によりホストされるコントロールがそのコンテンツを正しく表示するサイズを調整するようになります。  
  
#### <a name="to-size-to-content"></a>コンテンツに合わせてサイズ変更するには  
  
1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2. F5 キーを押してアプリケーションをビルドし、実行します。 2 つの新しいボタン コントロールより長いテキスト文字列と大きくなったフォント サイズが正しく表示にサイズ設定と<xref:System.Windows.Forms.Integration.WindowsFormsHost>にホストされるコントロールを対応する要素のサイズします。  
  
## <a name="using-absolute-positioning"></a>絶対配置の使用  
 絶対配置を使用する配置、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ユーザー インターフェイス (UI) の任意の場所内の要素。  
  
#### <a name="to-use-absolute-positioning"></a>絶対配置を使用するには  
  
1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、グリッド セルの上辺から 20 ピクセル、左端から 20 ピクセルに配置されます。  
  
## <a name="specifying-size-explicitly"></a>サイズの明示的な指定  
 サイズを指定することができます、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を使用して、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ。  
  
#### <a name="to-specify-size-explicitly"></a>サイズを明示的に指定するには  
  
1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は既定のレイアウト設定よりも小さいは 50 ピクセル、高さ 70 ピクセルのサイズに設定します。 コンテンツ、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがそれに応じて再配置します。  
  
## <a name="setting-layout-properties"></a>レイアウト プロパティの設定  
 常のプロパティを使用してホストされるコントロールにレイアウト関連のプロパティを設定、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。 ホストされているコントロールで直接レイアウト プロパティを設定すると、予期しない結果になります。  
  
 ホストされるコントロールにレイアウト関連プロパティを設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]も何も起こりません。  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>ホストされているコントロールでプロパティを設定した場合の結果を確認するには  
  
1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2. ソリューション エクスプ ローラーで MainWindow.xaml をダブルクリックします。 vb または MainWindow.xaml.cs をコード エディターで開きます。  
  
3. 次のコードをコピー、`MainWindow`クラスの定義。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. F5 キーを押してアプリケーションをビルドし、実行します。

5. をクリックして、 **Click me**ボタンをクリックします。 `button1_Click`イベント ハンドラーの設定、<xref:System.Windows.Forms.Control.Top%2A>と<xref:System.Windows.Forms.Control.Left%2A>ホストされるコントロールのプロパティ。 これにより、ホストされるコントロール内の位置を変更する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。 ホストは同じ画面領域を維持しますが、ホストされているコントロールはクリップされます。 ホストされるコントロールの代わりに、常に塗りつぶし、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。

## <a name="understanding-z-order-limitations"></a>z オーダーの制限の理解
 表示される<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は常に、他の WPF 要素の上に描画し、それらは z オーダーによる影響を受けません。 この z オーダーの動作を確認するには、次の操作を行います。

1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がラベル要素上に描画されます。

## <a name="docking"></a>ドッキング
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素をサポートして[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ドッキングします。 設定、<xref:System.Windows.Controls.DockPanel.Dock%2A>添付プロパティでホストされるコントロールをドッキングするのには、<xref:System.Windows.Controls.DockPanel>要素。

#### <a name="to-dock-a-hosted-control"></a>ホストされているコントロールをドッキングするには

1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>の右側にある要素がドッキングされた、<xref:System.Windows.Controls.DockPanel>要素。

## <a name="setting-visibility"></a>可視性の設定
 行うことができます、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを非表示にしたり、折りたたんだりするには、<xref:System.Windows.UIElement.Visibility%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。 コントロールを非表示にすると、そのコントロールは表示されませんが、レイアウト空間は使用されます。 コントロールを折りたたむと、そのコントロールは表示されず、レイアウト空間も使用されません。

#### <a name="to-set-the-visibility-of-a-hosted-control"></a>ホストされているコントロールの可視性を設定するには

1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. F5 キーを押してアプリケーションをビルドし、実行します。

4. をクリックして、**を非表示 をクリックします**を作成するボタン、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を非表示します。

5. をクリックして、**折りたたむにはクリック**ボタンを非表示に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>レイアウトからの要素全体。 ときに、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが折りたたまれ、周囲の要素がその領域を占有するように再配置します。

## <a name="hosting-a-control-that-does-not-stretch"></a>伸縮しないコントロールのホスト
 いくつか[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは固定サイズし、レイアウトで使用可能なスペースに合わせて伸縮しません。 たとえば、<xref:System.Windows.Forms.MonthCalendar>コントロールは、固定された間隔で 1 か月を表示します。

#### <a name="to-host-a-control-that-does-not-stretch"></a>伸縮しないコントロールをホストするには

1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がグリッドの行の中央に配置が、空き領域の塗りつぶしに拡張されていません。 によってホストされている 2 つ以上の月が生じる、ウィンドウが十分に大きい場合<xref:System.Windows.Forms.MonthCalendar>コントロールが、これらが、行の中央に配置します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト エンジンの中心要素を使用可能なスペースに合わせてサイズを変更することはできません。

## <a name="scaling"></a>スケーリング
 WPF の要素とは異なりは、ほとんどの Windows フォーム コントロールは継続的にスケーリングではありません。 オーバーライドするカスタム スケーリングを提供する、<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>メソッド。

#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>既定の動作を使用してホストされているコントロールをスケーリングするには

1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールとその周りの要素は、0.5 倍でスケーリングされます。 ただし、ホストされているコントロールのフォントはスケーリングされません。

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>回転
 WPF の要素とは異なり、Windows フォーム コントロールが回転にサポートされません。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素では、回転変換を適用すると、その他の WPF 要素とともに回転しません。 回転値が 180 度発生させ、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>イベント。

#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>ハイブリッド アプリケーションでの回転の効果を確認するには

1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールは回転しませんが、その周りの要素は 180 度の角度で回転します。 要素を表示するためにウィンドウのサイズを変更する必要がある場合があります。

## <a name="setting-padding-and-margins"></a>パディングとマージンの設定
 パディングとマージンは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトのパディングとマージンのような[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]します。 設定するだけです、<xref:System.Windows.Controls.Control.Padding%2A>と<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。

#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>ホストされているコントロールのパディングとマージンを設定するには

1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 パディングとマージンの設定が適用されるホストに[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに適用される場合と同じ方法で[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]します。

## <a name="using-dynamic-layout-containers"></a>動的レイアウト コンテナーの使用
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 2 つの動的レイアウト コンテナーを提供します<xref:System.Windows.Forms.FlowLayoutPanel>と<xref:System.Windows.Forms.TableLayoutPanel>します。 これらのコンテナーを使用することもできます。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト。

#### <a name="to-use-a-dynamic-layout-container"></a>動的レイアウト コンテナーを使用するには

1. 次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. コンストラクター内の `InitializeFlowLayoutPanel` メソッドに呼び出しを追加します。

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の設定、 <xref:System.Windows.Controls.DockPanel>、および<xref:System.Windows.Forms.FlowLayoutPanel>、既定では、その子コントロール<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WindowsFormsHost 要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)
- [WPF のサンプルでのフォーム コントロールの Windows の配置](https://go.microsoft.com/fwlink/?LinkID=159971)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
