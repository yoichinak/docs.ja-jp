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
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972307"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>チュートリアル: WPF での Windows フォーム コントロールの配置

このチュートリアルでは、レイアウト機能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用して[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 、ハイブリッドアプリケーションでコントロールを配置する方法について説明します。

このチュートリアルでは、以下のタスクを行います。

- プロジェクトの作成。

- 既定のレイアウト設定の使用。

- コンテンツに合わせたサイズの変更。

- 絶対配置の使用。

- サイズの明示的な指定。

- レイアウト プロパティの設定。

- z オーダーの制限の理解。

- ドッキング。

- 可視性の設定。

- 伸縮しないコントロールのホスト。

- スケーリング。

- 回転。

- パディングとマージンの設定。

- 動的レイアウト コンテナーの使用。

このチュートリアルで示すタスクの完全なコード一覧については、「 [WPF の Windows フォームコントロールの配置](https://go.microsoft.com/fwlink/?LinkID=159971)」を参照してください。

完了すると、ベースのアプリケーションの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]レイアウト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]機能について理解できるようになります。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには Visual Studio が必要です。

## <a name="creating-the-project"></a>プロジェクトの作成

### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには

1. という名前`WpfLayoutHostingWf`の WPF アプリケーションプロジェクトを作成します。

2. ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。

    - WindowsFormsIntegration

    - System.Windows.Forms

    - System.Drawing

3. MainWindow.xaml をダブルクリックして、XAML ビューで開きます。

4. 要素に、次[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の名前空間マッピングを追加します。 <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. 要素で、 <xref:System.Windows.Controls.Grid.ShowGridLines%2A>プロパティをに`true`設定し、5つの行と3つの列を定義します。 <xref:System.Windows.Controls.Grid>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>既定のレイアウト設定の使用

既定では、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素はホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されるコントロールのレイアウトを処理します。

### <a name="to-use-default-layout-settings"></a>既定のレイアウト設定を使用するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 コントロールがに<xref:System.Windows.Controls.Canvas>表示されます。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> ホストされるコントロールは、そのコンテンツに基づいてサイズ<xref:System.Windows.Forms.Integration.WindowsFormsHost>が設定され、ホストされるコントロールに合わせて要素のサイズが変更されます。

## <a name="sizing-to-content"></a>コンテンツに合わせたサイズの変更

要素<xref:System.Windows.Forms.Integration.WindowsFormsHost>によって、ホストされるコントロールのサイズが、コンテンツを適切に表示するように設定されます。

### <a name="to-size-to-content"></a>コンテンツに合わせてサイズ変更するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 2つの新しいボタンコントロールは、長いテキスト文字列と大きいフォントサイズを適切に表示するよう<xref:System.Windows.Forms.Integration.WindowsFormsHost>にサイズが設定され、ホストされているコントロールに合わせて要素のサイズが変更されます。

## <a name="using-absolute-positioning"></a>絶対配置の使用

絶対配置を使用して、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素をユーザーインターフェイス (UI) 内の任意の場所に配置できます。

### <a name="to-use-absolute-positioning"></a>絶対配置を使用するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、グリッドセルの上端から20ピクセル、左から20ピクセルが配置されます。

## <a name="specifying-size-explicitly"></a>サイズの明示的な指定

<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素のサイズは、プロパティ<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティを使用して指定できます。

### <a name="to-specify-size-explicitly"></a>サイズを明示的に指定するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、幅50ピクセル、高さ70ピクセル、既定のレイアウト設定より小さいサイズに設定されています。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの内容は、それに応じて再配置されます。

## <a name="setting-layout-properties"></a>レイアウト プロパティの設定

常に、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素のプロパティを使用して、ホストされるコントロールのレイアウト関連のプロパティを設定します。 ホストされているコントロールで直接レイアウト プロパティを設定すると、予期しない結果になります。

 で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ホストされるコントロールのレイアウト関連のプロパティを設定しても効果はありません。

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>ホストされているコントロールでプロパティを設定した場合の結果を確認するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. ソリューションエクスプローラーで、Mainwindow.xaml をダブルクリックします。 vb または MainWindow.xaml.cs をコードエディターで開きます。

3. 次のコードを`MainWindow`クラス定義にコピーします。

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. F5 キーを押してアプリケーションをビルドし、実行します。

5. **[クリック**してください] ボタンをクリックします。 イベント`button1_Click`ハンドラーは、ホスト<xref:System.Windows.Forms.Control.Top%2A>さ<xref:System.Windows.Forms.Control.Left%2A>れるコントロールのプロパティとプロパティを設定します。 これにより、ホストされるコントロールが<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素内で位置が移動します。 ホストは同じ画面領域を維持しますが、ホストされているコントロールはクリップされます。 代わりに、ホストされるコントロールは常に<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を埋める必要があります。

## <a name="understanding-z-order-limitations"></a>z オーダーの制限の理解

可視<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、常に他の WPF 要素の上に描画され、z オーダーの影響を受けません。 この z オーダーの動作を確認するには、次の手順を実行します。

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は label 要素上に描画されます。

## <a name="docking"></a>ドッキング

<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ドッキングをサポートしています。 添付プロパティを設定して、ホストされて<xref:System.Windows.Controls.DockPanel>いるコントロールを要素にドッキングします。 <xref:System.Windows.Controls.DockPanel.Dock%2A>

### <a name="to-dock-a-hosted-control"></a>ホストされているコントロールをドッキングするには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 要素は<xref:System.Windows.Controls.DockPanel>要素の右側にドッキングされます。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>

## <a name="setting-visibility"></a>可視性の設定

要素のプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.UIElement.Visibility%2A>を設定することによって、コントロールを非表示にしたり折りたたんだりできます。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールを非表示にすると、そのコントロールは表示されませんが、レイアウト空間は使用されます。 コントロールを折りたたむと、そのコントロールは表示されず、レイアウト空間も使用されません。

### <a name="to-set-the-visibility-of-a-hosted-control"></a>ホストされているコントロールの可視性を設定するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. F5 キーを押してアプリケーションをビルドし、実行します。

4. [クリックして**非表示に**する] ボタン<xref:System.Windows.Forms.Integration.WindowsFormsHost>をクリックすると、要素が非表示になります。

5. レイアウトの<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を完全に非表示にするには、 **[クリック**して閉じる] ボタンをクリックします。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを折りたたむと、周囲の要素が再配置され、そのスペースが占有されます。

## <a name="hosting-a-control-that-does-not-stretch"></a>伸縮しないコントロールのホスト

一部[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールは固定サイズであり、レイアウト内の使用可能な領域を塗りつぶすために伸縮しません。 たとえば、コントロールは<xref:System.Windows.Forms.MonthCalendar> 、固定されたスペースで月を表示します。

### <a name="to-host-a-control-that-does-not-stretch"></a>伸縮しないコントロールをホストするには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素はグリッド行の中央に配置されますが、使用可能な領域に合わせて拡大されることはありません。 ウィンドウのサイズが十分な場合は、ホスト<xref:System.Windows.Forms.MonthCalendar>されているコントロールによって複数の月が表示されることがありますが、これらは行の中央に配置されます。 レイアウト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]エンジンは、使用可能な領域に合わせてサイズを変更できない要素を中央揃えにします。

## <a name="scaling"></a>スケーリング

WPF 要素とは異なり、ほとんどの Windows フォームコントロールは継続的に拡張できません。 カスタムスケーリングを提供するには<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> 、メソッドをオーバーライドします。

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>既定の動作を使用してホストされているコントロールをスケーリングするには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールとその周りの要素は、0.5 倍でスケーリングされます。 ただし、ホストされているコントロールのフォントはスケーリングされません。

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>回転

WPF 要素とは異なり、Windows フォームコントロールは回転をサポートしていません。 回転<xref:System.Windows.Forms.Integration.WindowsFormsHost>変換が適用されている場合、要素は他の WPF 要素とは回転しません。 180°以外の回転値を指定する<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>と、イベントが発生します。

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>ハイブリッド アプリケーションでの回転の効果を確認するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールは回転しませんが、その周りの要素は 180 度の角度で回転します。 要素を表示するためにウィンドウのサイズを変更する必要がある場合があります。

## <a name="setting-padding-and-margins"></a>パディングとマージンの設定

レイアウトの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]埋め込みと余白は、の[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]埋め込みと余白に似ています。 要素のプロパティ<xref:System.Windows.Controls.Control.Padding%2A>と<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを設定するだけです。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>ホストされているコントロールのパディングとマージンを設定するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. F5 キーを押してアプリケーションをビルドし、実行します。 埋め込みと余白の設定は、で[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]適用されるのと同じ方法で、ホストされるコントロールに適用されます。

## <a name="using-dynamic-layout-containers"></a>動的レイアウト コンテナーの使用

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]には、とという<xref:System.Windows.Forms.FlowLayoutPanel> 2 <xref:System.Windows.Forms.TableLayoutPanel>つの動的レイアウトコンテナーが用意されています。 これらのコンテナーはレイアウトで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]も使用できます。

### <a name="to-use-a-dynamic-layout-container"></a>動的レイアウト コンテナーを使用するには

1. 次の XAML を<xref:System.Windows.Controls.Grid>要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. コンストラクター内の `InitializeFlowLayoutPanel` メソッドに呼び出しを追加します。

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. F5 キーを押してアプリケーションをビルドし、実行します。 要素<xref:System.Windows.Forms.Integration.WindowsFormsHost> は、<xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>を設定し、既定ので子コントロールを配置します。 <xref:System.Windows.Controls.DockPanel>

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WindowsFormsHost 要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)
- [WPF サンプルでの Windows フォームコントロールの配置](https://go.microsoft.com/fwlink/?LinkID=159971)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
