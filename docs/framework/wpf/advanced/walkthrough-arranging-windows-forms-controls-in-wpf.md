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
ms.openlocfilehash: 484895db539b288bf388ff6c2ce3c29db55080b1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197844"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>チュートリアル: WPF での Windows フォーム コントロールの配置

このチュートリアルでは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウト機能を使用して、ハイブリッドアプリケーションで [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを配置する方法について説明します。

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

完了すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ベースのアプリケーションの [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] レイアウト機能について理解できるようになります。

## <a name="prerequisites"></a>必要条件

このチュートリアルを完了するには Visual Studio が必要です。

## <a name="creating-the-project"></a>プロジェクトの作成

プロジェクトを作成して設定するには、次の手順を実行します。

1. `WpfLayoutHostingWf`という名前の WPF アプリケーションプロジェクトを作成します。

2. ソリューションエクスプローラーで、次のアセンブリへの参照を追加します。

    - WindowsFormsIntegration
    - System.Windows.Forms
    - System.Drawing

3. *Mainwindow.xaml*をダブルクリックして、xaml ビューで開きます。

4. <xref:System.Windows.Window> 要素に、次の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 名前空間マッピングを追加します。

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <xref:System.Windows.Controls.Grid> 要素で、<xref:System.Windows.Controls.Grid.ShowGridLines%2A> プロパティを `true` に設定し、5つの行と3つの列を定義します。

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>既定のレイアウト設定の使用

既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのレイアウトを処理します。

既定のレイアウト設定を使用するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Controls.Canvas>に [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> コントロールが表示されます。 ホストされるコントロールは、そのコンテンツに基づいてサイズが変更され、ホストされるコントロールに合わせて <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素のサイズが変更されます。

## <a name="sizing-to-content"></a>コンテンツに合わせたサイズの変更

<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素によって、ホストされるコントロールのサイズが、コンテンツを適切に表示するように設定されます。

コンテンツのサイズを変更するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 2つの新しいボタンコントロールは、長いテキスト文字列と大きいフォントサイズを適切に表示するようにサイズが設定され、ホストされているコントロールに合わせて <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素のサイズが変更されます。

## <a name="using-absolute-positioning"></a>絶対配置の使用

絶対配置を使用して、ユーザーインターフェイス (UI) の任意の場所に <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を配置できます。

絶対配置を使用するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、グリッドセルの上端から20ピクセル、左側から20ピクセルが配置されます。

## <a name="specifying-size-explicitly"></a>サイズの明示的な指定

<xref:System.Windows.FrameworkElement.Width%2A> と <xref:System.Windows.FrameworkElement.Height%2A> プロパティを使用して、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素のサイズを指定できます。

サイズを明示的に指定するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、既定のレイアウト設定よりも小さい50ピクセルのサイズ (高さ70ピクセル) に設定されます。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの内容は、それに応じて再配置されます。

## <a name="setting-layout-properties"></a>レイアウト プロパティの設定

<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素のプロパティを使用して、ホストされるコントロールのレイアウト関連のプロパティを常に設定します。 ホストされているコントロールで直接レイアウト プロパティを設定すると、予期しない結果になります。

 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のホストされるコントロールにレイアウト関連のプロパティを設定しても効果はありません。

ホストされるコントロールでプロパティを設定した場合の影響を確認するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. **ソリューションエクスプローラー**で、 *mainwindow.xaml*または*MainWindow.xaml.cs*をダブルクリックしてコードエディターで開きます。

3. `MainWindow` クラス定義に次のコードをコピーします。

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。

5. **[クリック**してください] ボタンをクリックします。 `button1_Click` イベントハンドラーは、ホストされるコントロールの <xref:System.Windows.Forms.Control.Top%2A> および <xref:System.Windows.Forms.Control.Left%2A> プロパティを設定します。 これにより、ホストされているコントロールが <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素内で位置が移動します。 ホストは同じ画面領域を維持しますが、ホストされているコントロールはクリップされます。 代わりに、ホストされるコントロールは常に <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を満たす必要があります。

## <a name="understanding-z-order-limitations"></a>z オーダーの制限の理解

可視の <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、常に他の WPF 要素の上に描画され、z オーダーの影響を受けません。 この z オーダーの動作を確認するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、label 要素上に描画されます。

## <a name="docking"></a>ドッキング

<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ドッキングをサポートします。 <xref:System.Windows.Controls.DockPanel> 要素にホストされるコントロールをドッキングするには、<xref:System.Windows.Controls.DockPanel.Dock%2A> 添付プロパティを設定します。

ホストされたコントロールをドッキングするには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、<xref:System.Windows.Controls.DockPanel> 要素の右側にドッキングされます。

## <a name="setting-visibility"></a>可視性の設定

<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の <xref:System.Windows.UIElement.Visibility%2A> プロパティを設定することによって、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを非表示にしたり折りたたんだりできます。 コントロールを非表示にすると、そのコントロールは表示されませんが、レイアウト空間は使用されます。 コントロールを折りたたむと、そのコントロールは表示されず、レイアウト空間も使用されません。

ホストされるコントロールの表示を設定するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. *Mainwindow.xaml*または*MainWindow.xaml.cs*で、次のコードをクラス定義にコピーします。

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。

4. [クリックして**非表示に**する] ボタンをクリックすると、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素が非表示になります。

5. レイアウトの <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を完全に非表示にするには、 **[クリック**して閉じる] ボタンをクリックします。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを折りたたむと、周囲の要素が再配置され、そのスペースが占有されます。

## <a name="hosting-a-control-that-does-not-stretch"></a>伸縮しないコントロールのホスト

一部の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのサイズは固定されており、レイアウト内の使用可能な領域を塗りつぶすために伸縮しません。 たとえば、<xref:System.Windows.Forms.MonthCalendar> コントロールでは、固定領域に月が表示されます。

ストレッチされないコントロールをホストするには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素はグリッド行の中央に配置されますが、使用可能な領域に合わせて拡大されることはありません。 ウィンドウのサイズが十分な場合は、ホストされている <xref:System.Windows.Forms.MonthCalendar> コントロールによって複数の月が表示されることがありますが、これらは行の中央に配置されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトエンジンは、使用可能な領域に合わせてサイズを変更できない要素を中央揃えにします。

## <a name="scaling"></a>スケーリング

WPF 要素とは異なり、ほとんどの Windows フォームコントロールは継続的に拡張できません。 カスタムスケーリングを提供するには、<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> メソッドをオーバーライドします。

既定の動作を使用してホストされているコントロールをスケーリングするには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールとその周りの要素は、0.5 倍でスケーリングされます。 ただし、ホストされているコントロールのフォントはスケーリングされません。

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>回転

WPF 要素とは異なり、Windows フォームコントロールは回転をサポートしていません。 回転変換が適用されている場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は他の WPF 要素とは回転しません。 180°以外の回転値を指定すると、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> イベントが発生します。

ハイブリッドアプリケーションでのローテーションの効果を確認するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールは回転しませんが、その周りの要素は 180 度の角度で回転します。 要素を表示するためにウィンドウのサイズを変更する必要がある場合があります。

## <a name="setting-padding-and-margins"></a>パディングとマージンの設定

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトの埋め込みと余白は [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の埋め込みと余白に似ています。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の <xref:System.Windows.Controls.Control.Padding%2A> と <xref:System.Windows.FrameworkElement.Margin%2A> のプロパティを設定するだけです。

ホストされるコントロールの埋め込みと余白を設定するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 埋め込みと余白の設定は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]で適用されるのと同じ方法で、ホストされる [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに適用されます。

## <a name="using-dynamic-layout-containers"></a>動的レイアウト コンテナーの使用

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] には、<xref:System.Windows.Forms.FlowLayoutPanel> と <xref:System.Windows.Forms.TableLayoutPanel>の2つの動的レイアウトコンテナーが用意されています。 これらのコンテナーは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトでも使用できます。

動的レイアウトコンテナーを使用するには、次の手順を実行します。

1. 次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. *Mainwindow.xaml*または*MainWindow.xaml.cs*で、次のコードをクラス定義にコピーします。

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. コンストラクターで `InitializeFlowLayoutPanel` メソッドの呼び出しを追加します。

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は <xref:System.Windows.Controls.DockPanel>に入力し、<xref:System.Windows.Forms.FlowLayoutPanel> 子コントロールを既定の <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>に配置します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [WindowsFormsHost 要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)
- [WPF サンプルでの Windows フォームコントロールの配置](https://go.microsoft.com/fwlink/?LinkID=159971)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
