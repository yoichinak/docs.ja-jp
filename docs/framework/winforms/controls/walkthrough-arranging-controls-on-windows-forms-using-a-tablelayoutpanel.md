---
title: 'チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 392d548a5f89c31d94af9134b8cc3a37b28d8c6c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341622"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置
アプリケーションによっては、フォームのサイズを変更したり、コンテンツのサイズが変化したりしたときに、それに応じて自動的にレイアウトを調整するフォームが必要です。 動的なレイアウトが必要であり、かつコードで <xref:System.Windows.Forms.Control.Layout> イベントを明示的に処理しない場合は、レイアウト パネルの使用をご検討ください。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> コントロールと <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、コントロールをフォームに直感的な方法で配置できます。 これら 2 つのコントロールは、それぞれに含まれる子コントロールの相対位置を制御するための自動的で構成可能な機能を提供します。また、どちらも実行時に動的なレイアウト機能を提供するため、親フォームの寸法の変更に応じて子コントロールのサイズと位置を変更できます。 レイアウト パネルは他のレイアウト パネルの入れ子にすることができるため、高度なユーザー インターフェイスを実現できます。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> はその内容を特定のフローの方向 (水平または垂直) に配置します。 ある行から次の行、またはある列から次の列に内容をラップすることができます。 また、ラップする代わりにクリップすることもできます。 詳細については、「[チュートリアル:FlowLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)します。  
  
 <xref:System.Windows.Forms.TableLayoutPanel>グリッド、HTML と同様の機能を提供するのには、その内容を整列\<テーブル > 要素。 <xref:System.Windows.Forms.TableLayoutPanel>コントロールでは、個々 のコントロールの位置を正確に指定することがなく、グリッド レイアウトにコントロールを配置できます。 セルは行と列に配置され、それぞれに異なるサイズを設定できます。 セルは、行と列の間で結合できます。 セルには、すべてのフォームは含めることができ、コンテナーとして他の多くの点で動作を含めることができます。  
  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールがフォームのサイズを変更、レイアウトがスムーズに変更できるように、実行時に、比例サイズ変更機能も提供します。 これにより、<xref:System.Windows.Forms.TableLayoutPanel>コントロールがデータ エントリ フォームとローカライズされたアプリケーションなどの目的に適しています。 詳細については、「[チュートリアル:データ エントリのサイズ変更可能な Windows フォームを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))と[チュートリアル。ローカライズ可能な Windows フォームを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))します。  
  
 一般に、行わないで、<xref:System.Windows.Forms.TableLayoutPanel>コントロール全体のレイアウト コンテナーとして。 使用<xref:System.Windows.Forms.TableLayoutPanel>コントロールをレイアウトの部分に比例してサイズ変更の機能を提供します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   行と列でコントロールの配置  
  
-   設定の行と列のプロパティ  
  
-   コントロールを使って行および列にまたがりメモリ割り当てください。  
  
-   オーバーフローの自動処理  
  
-   ツールボックスでのダブルクリックによるコントロールの挿入  
  
-   アウトラインの描画によるコントロールの挿入  
  
-   別の親コントロールへの既存コントロールの再割り当て  
  
 終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1. "TableLayoutPanelExample"と呼ばれる Windows アプリケーション プロジェクトを作成します。 詳細については、「[方法 :Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)です。  
  
2. フォームを選択、 **Windows** **フォーム デザイナー**します。  
  
## <a name="arranging-controls-in-rows-and-columns"></a>行と列でコントロールの配置  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールでは、行と列にコントロールを簡単に配置できます。  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>行と列は、TableLayoutPanel を使用してコントロールを配置するには  
  
1. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。 既定では、それに注意してください、<xref:System.Windows.Forms.TableLayoutPanel>コントロールに 4 つのセルがあります。  
  
2. ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**に、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、セルの 1 つにドロップします。 なお、<xref:System.Windows.Forms.Button>コントロールが選択したセル内で作成されます。  
  
3. 3 回ドラッグ<xref:System.Windows.Forms.Button>コントロールを**ツールボックス**に、<xref:System.Windows.Forms.TableLayoutPanel>制御、各セルには、ボタンが含まれているようにします。  
  
4. 2 つの列間の垂直方向のサイズ変更ハンドルをドラッグし、左に移動します。 なお、<xref:System.Windows.Forms.Button>のサイズの中に、幅を小さくする最初の列内のコントロールがサイズ変更、 <xref:System.Windows.Forms.Button> 2 番目の列内のコントロールは変更されません。  
  
5. 2 つの列間の垂直方向のサイズ変更ハンドルをドラッグし、右に移動します。 なお、<xref:System.Windows.Forms.Button>最初の列内のコントロールは、元のサイズに戻るときに、 <xref:System.Windows.Forms.Button> 2 番目の列内のコントロールが右に移動されます。  
  
6. パネル内のコントロールへの影響を確認するには、上下の水平方向のサイズ変更ハンドルを移動します。  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>ドッキングと固定を使用してセル内のコントロールの配置  
 子コントロールのアンカーの動作を<xref:System.Windows.Forms.TableLayoutPanel>他のコンテナー コントロールでの動作とは異なります。 子コントロールのドッキング動作では、他のコンテナー コントロールの場合と同じです。  
  
#### <a name="positioning-controls-within-cells"></a>セル内のコントロールの配置  
  
1. 最初の選択<xref:System.Windows.Forms.Button>コントロール。 <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Fill>に変更します。 なお、<xref:System.Windows.Forms.Button>コントロールを拡張すると、そのセルを入力します。  
  
2. その他のいずれかを選択<xref:System.Windows.Forms.Button>コントロール。 <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を <xref:System.Windows.Forms.AnchorStyles.Right>に変更します。 右の境界線がセルの右境界線に近いように移動はことに注意してください。 境界線の間の距離の合計は、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティと、パネルの<xref:System.Windows.Forms.Control.Padding%2A>プロパティ。  
  
3. 値を変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを<xref:System.Windows.Forms.AnchorStyles.Right>と<xref:System.Windows.Forms.AnchorStyles.Left>します。 コントロールのサイズが、セルの幅に注意してください、<xref:System.Windows.Forms.Control.Margin%2A>と<xref:System.Windows.Forms.Control.Padding%2A>値を考慮します。  
  
4. 手順 2 と 3 を繰り返して、<xref:System.Windows.Forms.AnchorStyles.Top>と<xref:System.Windows.Forms.AnchorStyles.Bottom>スタイル。  
  
## <a name="setting-row-and-column-properties"></a>設定の行と列のプロパティ  
 使用して行および列の個別のプロパティを設定することができます、<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>と<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>コレクション。  
  
#### <a name="to-set-row-and-column-properties"></a>行と列のプロパティを設定するには  
  
1. 選択、<xref:System.Windows.Forms.TableLayoutPanel>を制御、 **Windows フォーム デザイナー**します。  
  
2. **プロパティ**開いているウィンドウ、 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 、省略記号ボタンをクリックしてコレクション (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) ボタン次に、**列**エントリ。  
  
3. 最初の列を選択しの値を変更、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティを<xref:System.Windows.Forms.SizeType.AutoSize>します。 クリックして**OK**して変更を受け入れます。 最初の列の幅が合わせてに減少することに注意してください、<xref:System.Windows.Forms.Button>コントロール。 また、列の幅がサイズ変更可能でないことに注意してください。  
  
4. **プロパティ**ウィンドウを開いて、<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>コレクションと、最初の列を選択します。 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> プロパティの値を <xref:System.Windows.Forms.SizeType.Percent>に変更します。 クリックして**OK**して変更を受け入れます。 サイズ変更、<xref:System.Windows.Forms.TableLayoutPanel>の幅を制御し、最初の列の幅が拡大することに注意してください。 サイズ変更、<xref:System.Windows.Forms.TableLayoutPanel>制御幅を小さくして、最初の列のボタンがセルに合わせてサイズを調整するに注意してください。 また、列の幅がサイズ変更可能なことに注意してください。  
  
5. **プロパティ**ウィンドウを開いて、<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>収集と表示されているすべての列を選択します。 値の設定すべて<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティを<xref:System.Windows.Forms.SizeType.Percent>します。 クリックして**OK**して変更を受け入れます。 繰り返し、<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>コレクション。  
  
6. 角にあるサイズ変更ハンドルを取得し、幅と高さのサイズを変更、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 行と列としてサイズ変更に注意してください、<xref:System.Windows.Forms.TableLayoutPanel>コントロールのサイズを変更します。 行と列の値は水平方向サイズ変更可能なサイズ変更ハンドルを垂直方向にも注意してください。  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>コントロールを使って行および列にまたがりメモリ割り当てください。  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、デザイン時にコントロールをいくつかの新しいプロパティを追加します。 これらのプロパティの 2 つは`RowSpan`と`ColumnSpan`します。 これらのプロパティを使用すると、コントロールの範囲より 1 つの行または列を作成します。  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>行と列を制御する  
  
1. 選択、<xref:System.Windows.Forms.Button>最初の行および第 1 列内のコントロール。  
  
2. **プロパティ**windows での値を変更する、`ColumnSpan`プロパティを**2**します。 なお、<xref:System.Windows.Forms.Button>コントロールが最初の列と 2 番目の列を入力します。 この変更に対応するために、余分な行が追加されたよりも注意してください。  
  
3. 手順 2. を繰り返します、`RowSpan`プロパティ。  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>ツールボックスでのダブルクリックによるコントロールの挿入  
 <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **でコントロールをダブルクリックすると、** コントロールに内容を挿入できます。  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>ツールボックスでダブルクリックしてコントロールを挿入するには  
  
1. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2. <xref:System.Windows.Forms.Button> ツールボックス **の**コントロール アイコンをダブルクリックします。 新しいボタン コントロールが含まれているメモ、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの最初のセル。  
  
3. **ツールボックス**でさらにいくつかのコントロールをダブルクリックします。 新しいコントロールに順次表示されることに注意してください、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの使用されていないセル。 また、<xref:System.Windows.Forms.TableLayoutPanel>コントロールを拡張すると、使用可能なセルがない場合に、新しいコントロールに対応します。  
  
## <a name="automatic-handling-of-overflows"></a>オーバーフローの自動処理  
 コントロールを挿入するときに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール、可能性がありますが不足する空のセル、新しいコントロールにします。 <xref:System.Windows.Forms.TableLayoutPanel>コントロールこのような状況は自動的に処理のセルの数を増やすことで。  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>オーバーフローの自動処理を確認するには  
  
1. まだ空のセルがある場合、<xref:System.Windows.Forms.TableLayoutPanel>コントロールを新しい挿入<xref:System.Windows.Forms.Button>まで制御、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが完全にします。  
  
2. 1 回、<xref:System.Windows.Forms.TableLayoutPanel>コントロールは完全なをダブルクリックして、<xref:System.Windows.Forms.Button>アイコン、**ツールボックス**別に挿入する<xref:System.Windows.Forms.Button>コントロール。 なお、<xref:System.Windows.Forms.TableLayoutPanel>コントロールは、新しいコントロールを対応するために新しいセルを作成します。 さらに、いくつかのコントロールを挿入し、サイズ変更動作を確認します。  
  
3. <xref:System.Windows.Forms.TableLayoutPanel> コントロールの <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> プロパティの値を <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize> に変更します。 ダブルクリックして、<xref:System.Windows.Forms.Button>アイコン、**ツールボックス**を挿入する<xref:System.Windows.Forms.Button>まで制御、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが完全にします。 ダブルクリックして、<xref:System.Windows.Forms.Button>アイコン、**ツールボックス**もう一度です。 エラー メッセージが表示されることに注意してください、 **Windows フォーム デザイナー**追加の行と列を作成できないことを通知します。  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>アウトラインの描画によるコントロールの挿入  
 セルにアウトラインを描画すると、コントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールに挿入し、サイズを指定できます。  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>アウトラインを描画してコントロールを挿入するには  
  
1. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2. **ツールボックス**で <xref:System.Windows.Forms.Button> コントロール アイコンをクリックします。 フォームにドラッグしないでください。  
  
3. <xref:System.Windows.Forms.TableLayoutPanel> コントロールにマウス ポインターを置きます。 ポインターが <xref:System.Windows.Forms.Button> コントロール アイコンが付いた十字カーソルに変わることにご注意ください。  
  
4. マウス ボタンを押したままにします。  
  
5. マウス ポインターをドラッグして、 <xref:System.Windows.Forms.Button> コントロールのアウトラインを描画します。 適切なサイズのアウトラインを描画したら、マウス ボタンを離します。 なお、<xref:System.Windows.Forms.Button>コントロールのアウトラインを描画したセルにコントロールが作成されます。  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>セル内の複数のコントロールが許可されていません  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、1 つのセルの 1 つだけの子コントロールを含めることができます。  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>示すセル内の複数のコントロールは許可されていません  
  
-   ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**に、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、占有されたセルの 1 つにドロップします。 なお、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが削除を許可していない、<xref:System.Windows.Forms.Button>占有されたセルにコントロール。  
  
## <a name="swapping-controls"></a>コントロールの交換  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールでは、2 つの異なるセルを占有しているコントロールをスワップすることができます。  
  
#### <a name="to-swap-controls"></a>コントロールをスワップするには  
  
-   1 つをドラッグ、<xref:System.Windows.Forms.Button>占有されたもう 1 つのセルにドロップしてセルを占有からコントロール。 他の 2 つのコントロールが 1 つのセルから移動したことに注意してください。  
  
## <a name="next-steps"></a>次の手順  
 レイアウト パネルとコントロールを組み合わせて使用すると、複雑なレイアウトを作成できます。 さらに詳しく調べるための推奨事項を次に示します。  
  
-   いずれかのサイズを変更して、<xref:System.Windows.Forms.Button>コントロール サイズを大きくし、レイアウトへの影響に注意してください。  
  
-   選択した複数のコントロールに貼り付けて、<xref:System.Windows.Forms.TableLayoutPanel>制御し、コントロールを挿入する方法に注意してください。  
  
-   レイアウト パネルには、別のレイアウト パネルを含めることができます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールを既存のコントロールにドロップしてみます。  
  
-   <xref:System.Windows.Forms.TableLayoutPanel> コントロールを親フォームにドッキングします。 フォームのサイズを変更し、レイアウトの変化を確認します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond、WA:Microsoft Press、1999 年。 (USBN:0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [チュートリアル: データ エントリのサイズ変更可能な Windows フォームを作成します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [チュートリアル: ローカライズ可能な Windows フォームを作成します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [TableLayoutPanel コントロールの推奨される手順](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize プロパティの概要](autosize-property-overview.md)
- [方法: Windows フォーム上のコントロールをドッキングする](how-to-dock-controls-on-windows-forms.md)
- [方法: Windows フォームにコントロールを固定する](how-to-anchor-controls-on-windows-forms.md)
- [チュートリアル: Padding、Margin、AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](windows-forms-controls-padding-autosize.md)
