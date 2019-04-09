---
title: 'チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 4d352ee5c431ba43bbe338a9caf7bd0716e91834
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139790"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置
フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。 Windows フォーム デザイナーでは、これを実現するさまざまなレイアウト ツールを提供します。 最も重要なの 1 つは、<xref:System.Windows.Forms.Design.Behavior.SnapLine>機能します。  
  
 スナップ線では、他のコントロールとコントロールを整列する位置を正確にわかります。 Windows ユーザー インターフェイスのガイドラインを規定に従い、コントロール間の余白の推奨される距離も示します。 詳細については、次を参照してください。[ユーザー インターフェイスの設計と開発](https://go.microsoft.com/FWLink/?LinkId=83878)します。  
  
 スナップ線簡単鮮明で、コントロールを配置するプロフェッショナルな外観と動作 (ルック アンド フィール)。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   スペーシングとスナップ線を使用してコントロールの配置  
  
-   フォームやコンテナーの余白に合わせて調整  
  
-   グループ化されたコントロールに合わせて調整  
  
-   スナップ線を使用して、サイズのアウトラインでコントロールを配置するには  
  
-   コントロールをツールボックスからドラッグしたときに、スナップ線を使用します。  
  
-   スナップ線を使用してコントロールのサイズ変更  
  
-   コントロールのテキストとラベルの整列  
  
-   キーボード ナビゲーションとスナップ線を使用します。  
  
-   スナップ線とレイアウト パネル  
  
-   スナップ線を無効にします。  
  
 完了したら、レイアウトにスナップ線の機能で果たす役割について理解があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  "SnaplineExample"と呼ばれる Windows ベースのアプリケーション プロジェクトを作成する (**ファイル** > **新規** > **プロジェクト** >  **Visual c#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォーム アプリケーション**)。  
  
2.  フォーム デザイナーでフォームを選択します。  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>スペーシングとスナップ線を使用してコントロールの配置  
 スナップ線は、フォーム上のコントロールを配置する、正確かつ直感的な方法を提供します。 別のコントロールまたはコントロールのセット、整列する位置の近くを選択したコントロールまたはコントロールを移動するときに表示されます。 選択内容は「スナップ」推奨の位置を過去の他のコントロールに移動するとします。  
  
#### <a name="to-arrange-controls-using-snaplines"></a>スナップ線を使用してコントロールを配置するには  
  
1.  <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2.  移動、<xref:System.Windows.Forms.Button>フォームの右下隅にコントロール。 注スナップ線として表示される<xref:System.Windows.Forms.Button>下および右の境界線をフォームのコントロールが近づきます。 これらのスナップ線は、コントロールの枠線とフォームの推奨される間隔を表示します。  
  
3.  移動、<xref:System.Windows.Forms.Button>注スナップ線が表示される、フォームの境界線を制御します。 完了したら、移動、<xref:System.Windows.Forms.Button>フォームの中央近くにあるコントロール。  
  
4.  もう 1 つドラッグ<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**フォームにします。  
  
5.  2 つ目の移動<xref:System.Windows.Forms.Button>は最初のほぼレベルまでを制御します。 両方のボタンのテキストのベースラインに表示されるスナップ線をメモし、移動中のコントロールが他のコントロールを使用して正確にレベルの位置にスナップすることに注意してください。  
  
6.  2 つ目の移動<xref:System.Windows.Forms.Button>最初のすぐ上に配置されるまでを制御します。 両方のボタンの左端と右端の端に沿って表示され、コントロールは、その他のコントロールを正確に配置される位置に移動のスナップ、スナップ線に注意してください。  
  
7.  いずれかの選択、<xref:System.Windows.Forms.Button>を制御し、それらはほとんど触れることまで、その他の近くに移動します。 それらの間に表示されるスナップ線に注意してください。 推奨されるコントロールの境界線間この距離です。 この位置に移動するコントロールをスナップすることにも注意してください。  
  
8.  2 つをドラッグして<xref:System.Windows.Forms.Panel>コントロールを**ツールボックス**フォームにします。  
  
9. いずれかの移動、<xref:System.Windows.Forms.Panel>は最初のほぼレベルまでを制御します。 スナップ線が両方のコントロールの上端と下端の端に沿って表示され、移動中のコントロールが他のコントロールを使用して正確にレベルの位置にスナップすることに注意してください。 注意してください。  
  
## <a name="aligning-to-form-and-container-margins"></a>フォームやコンテナーの余白に合わせて調整  
 スナップ線を使用して、一貫した方法でコントロールをフォームとコンテナーの余白を配置するのに役立ちます。  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>フォームとコンテナーの余白にコントロールを配置するには  
  
1.  いずれかの選択、<xref:System.Windows.Forms.Button>を制御し、スナップ線が表示されるまで、フォームの右側の境界線の近くに移動します。 右罫線のスナップ線の距離は、コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティと、フォームの<xref:System.Windows.Forms.Control.Padding%2A>プロパティの値。  
  
> [!NOTE]
>  場合、フォームの<xref:System.Windows.Forms.Control.Padding%2A>0,0,0,0 に設定されて、Windows フォーム デザイナーで、フォームは、シャドウ<xref:System.Windows.Forms.Control.Padding%2A>9,9,9,9 の値。 この動作をオーバーライドするには、0,0,0,0 以外の値を割り当てます。  
  
1.  値を変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Margin%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.All%2A>プロパティを 0 にします。 詳細については、次を参照してください。[チュートリアル。Padding、Margin、および AutoSize プロパティを持つコントロールをフォーム レイアウト Windows](windows-forms-controls-padding-autosize.md)します。  
  
2.  移動、<xref:System.Windows.Forms.Button>スナップ線が表示されるまで、フォームの右側の境界線の近くに制御します。 この距離は、フォームの値によって指定された<xref:System.Windows.Forms.Control.Padding%2A>プロパティ。  
  
3.  <xref:System.Windows.Forms.GroupBox> ツールボックス **から** コントロールをフォームにドラッグします。  
  
4.  値を変更、<xref:System.Windows.Forms.GroupBox>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.All%2A>プロパティを 10 にします。  
  
5.  ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**に、<xref:System.Windows.Forms.GroupBox>コントロール。  
  
6.  移動、<xref:System.Windows.Forms.Button>コントロールの右境界線に近い、<xref:System.Windows.Forms.GroupBox>スナップ線が表示されるまでを制御します。 移動、<xref:System.Windows.Forms.Button>コントロール内の<xref:System.Windows.Forms.GroupBox>コントロールとスナップ線が表示される場所に注意してください。  
  
## <a name="aligning-to-grouped-controls"></a>グループ化されたコントロールに合わせて調整  
 グループ化されたコントロールを配置するスナップ線を使用する内で制御としても、<xref:System.Windows.Forms.GroupBox>コントロール。  
  
#### <a name="to-align-to-grouped-controls"></a>グループ化されたコントロールを配置するには  
  
1.  フォーム上のコントロールの 2 つを選択します。 選択範囲を移動して、選択内容とその他のコントロール間に表示されるスナップ ラインに注意してください。  
  
2.  <xref:System.Windows.Forms.GroupBox> ツールボックス **から** コントロールをフォームにドラッグします。  
  
3.  ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**に、<xref:System.Windows.Forms.GroupBox>コントロール。  
  
4.  いずれかの選択、<xref:System.Windows.Forms.Button>を制御し、移動、<xref:System.Windows.Forms.GroupBox>コントロール。 注スナップ線の端に表示される<xref:System.Windows.Forms.GroupBox>コントロール。 なお、スナップ線の端に表示されますが、<xref:System.Windows.Forms.Button>に格納されているコントロール、<xref:System.Windows.Forms.GroupBox>コントロール。 コンテナー コントロールの子であるコントロールでは、スナップ線もサポートします。  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>スナップ線を使用して、サイズのアウトラインでコントロールを配置するには  
 スナップ線に整列させることとを最初にフォーム上に配置を制御します。  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>によって、サイズのアウトライン コントロールを配置するスナップ線を使用するには  
  
1.  **ツールボックス**で <xref:System.Windows.Forms.Button> コントロール アイコンをクリックします。 フォームにドラッグしないでください。  
  
2.  フォームのデザイン画面上には、マウス ポインターを移動します。 ポインターが <xref:System.Windows.Forms.Button> コントロール アイコンが付いた十字カーソルに変わることにご注意ください。 なお、スナップ線の位置を整列の提案が表示される<xref:System.Windows.Forms.Button>コントロール。  
  
3.  マウス ボタンを押したままにします。  
  
4.  フォーム上にマウス ポインターをドラッグします。 アウトラインを描画することで、位置、およびコントロールのサイズを示すに注意してください。  
  
5.  フォーム上の別のコントロールと揃うまでドラッグします。 スナップ線を合図が表示されることに注意してください。  
  
6.  マウスのボタンを離します。 アウトラインで示されるサイズ、位置にあるコントロールを作成します。  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>コントロールをツールボックスからドラッグしたときに、スナップ線を使用します。  
 スナップ線に整列させることを制御からそれらをドラッグすると、**ツールボックス**フォームにします。  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>ツールボックスからコントロールをドラッグするときに、スナップ線を使用するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**フォーム上にマウス ボタンを押したままです。  
  
2.  フォームのデザイン画面上には、マウス ポインターを移動します。 位置を示すために、ポインターが変わることに注意してください。 新しい<xref:System.Windows.Forms.Button>コントロールが作成されます。  
  
3.  フォーム上にマウス ポインターをドラッグします。 提案の整列位置に表示されるスナップ線に注意してください、<xref:System.Windows.Forms.Button>コントロール。 その他のコントロールに配置される位置を検索します。  
  
4.  マウスのボタンを離します。 スナップ線によって示される位置にあるコントロールを作成します。  
  
## <a name="resizing-controls-using-snaplines"></a>スナップ線を使用してコントロールのサイズ変更  
 スナップ線を使用するようにサイズを変更するには、コントロールを配置します。  
  
#### <a name="to-resize-a-control-using-snaplines"></a>スナップ線を使用して、コントロールのサイズを変更するには  
  
1.  <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2.  サイズ変更、<xref:System.Windows.Forms.Button>角をドラッグしてサイズ変更ハンドルの 1 つをグラブを行ったによって制御します。 詳細については、「[方法: Windows フォーム上のコントロールのサイズを変更](how-to-resize-controls-on-windows-forms.md)します。  
  
3.  までのいずれかのサイズ変更ハンドルをドラッグして、<xref:System.Windows.Forms.Button>コントロールの枠線が別のコントロールに揃えられます。 スナップ線が表示されるに注意してください。 また、サイズ変更ハンドルをスナップ線によって示される位置にスナップすることに注意してください。  
  
4.  サイズ変更、<xref:System.Windows.Forms.Button>さまざまな方向を制御し、さまざまなコントロールにサイズ変更ハンドルを整列します。 スナップ線が合図のさまざまな向きで表示する方法に注意してください。  
  
## <a name="aligning-a-label-to-a-controls-text"></a>コントロールのテキストとラベルの整列  
 一部のコントロールは、他のコントロールに表示されるテキストを整列させるためのスナップ線を提供します。  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>コントロールのテキストにラベルを配置するには  
  
1.  <xref:System.Windows.Forms.TextBox> ツールボックス **から** コントロールをフォームにドラッグします。 ドロップすると、<xref:System.Windows.Forms.TextBox>をフォームにコントロール、スマート タグ グリフをクリックし、選択、 **textBox1 にテキストを設定**オプション。 詳細については、次を参照してください。[チュートリアル。フォーム コントロールのスマート タグを使用した Windows での一般的なタスクを実行する](performing-common-tasks-using-smart-tags-on-wf-controls.md)します。  
  
2.  <xref:System.Windows.Forms.Label> ツールボックス **から** コントロールをフォームにドラッグします。  
  
3.  <xref:System.Windows.Forms.Label> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true`に変更します。 コントロールの枠線が表示されるテキストに合わせて調整されることに注意してください。  
  
4.  移動、<xref:System.Windows.Forms.Label>コントロールの左側に、<xref:System.Windows.Forms.TextBox>制御するための下端に揃えて配置されますが、<xref:System.Windows.Forms.TextBox>コントロール。 2 つのコントロールの下端に沿って表示されるスナップ線に注意してください。  
  
5.  移動、<xref:System.Windows.Forms.Label>コントロールまで、少し上向き、<xref:System.Windows.Forms.Label>テキストと<xref:System.Windows.Forms.TextBox>テキストを配置します。 両方のコントロールのテキスト フィールドを配置するときを示す、表示されるスタイルの異なるスナップ線に注意してください。  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>キーボード ナビゲーションとスナップ線を使用します。  
 スナップ線に整列させることは、配置、キーボードの矢印キーを使用してを制御します。  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>キーボード ナビゲーションとスナップ線を使用するには  
  
1.  <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。 フォームの左上隅に配置します。  
  
2.  Ctrl キーを押しながら下方向矢印のキーを押します。 コントロールがフォームを最初の使用可能な水平方向の配置位置を移動するに注意してください。  
  
3.  コントロールがフォームの下部に達するまで、ctrl キーを押しながら下方向キーを押します。 フォームを下に移動するときに占有する位置を確認します。  
  
4.  Ctrl キーを押しながら右方向のキーを押してします。 コントロールが最初の使用可能な垂直方向の配置位置をフォームの全体を移動することに注意してください。  
  
5.  コントロールがフォームの端に達するまでは、ctrl キーを押しながら右方向キーを押します。 フォーム全体を移動する際に占有する位置に注意してください。  
  
6.  方向キーの組み合わせで、コントロールをフォーム上を移動します。 コントロールが占有する位置とそれに伴うスナップ ガイドラインに注意してください。  
  
7.  サイズを変更するには、shift キーを押しながら任意の方向キーを押して、 <xref:System.Windows.Forms.Button> 1 ピクセルずつコントロール。  
  
8.  サイズを変更するには、CTRL + SHIFT + 任意の方向キーを押して、<xref:System.Windows.Forms.Button>スナップ線の単位で制御します。  
  
## <a name="snaplines-and-layout-panels"></a>スナップ線とレイアウト パネル  
 レイアウト パネル内では、スナップ線が無効になります。  
  
#### <a name="to-selectively-disable-snaplines"></a>スナップ線を無効にするには  
  
1.  <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2.  <xref:System.Windows.Forms.Button> ツールボックス **の**コントロール アイコンをダブルクリックします。 新しいボタン コントロールが含まれているメモ、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの最初のセル。  
  
3.  ダブルクリックして、<xref:System.Windows.Forms.Button>コントロール アイコン、**ツールボックス**さらに 2 回です。 これにより、1 つの空のセル、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
4.  ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**の空のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 スナップ線が表示されないに注意してください。  
  
5.  ドラッグ、<xref:System.Windows.Forms.Button>の制御、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、移動、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 スナップ線がもう一度表示されることに注意してください。  
  
## <a name="disabling-snaplines"></a>スナップ線を無効にします。  
 スナップ線は、既定で有効にします。 スナップ線を選択的に、無効にできますか、デザイン環境で無効にできます。  
  
#### <a name="to-selectively-disable-snaplines"></a>スナップ線を無効にするには  
  
-   ALT キーを押しておよびコントロールをフォーム上に移動します。  
  
     スナップ線が表示されないと、コントロールが潜在的な配置位置にスナップいないことに注意してください。  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>デザイン環境のスナップ線を無効にするには  
  
1.  **ツール**メニューを開き、**オプション** ダイアログ ボックス。 Windows フォーム デザイナー ダイアログ ボックスを開きます。 詳細については、「 [全般、Windows フォーム デザイナー、オプション ダイアログ ボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))です。  
  
2.  選択、**全般**ノード。 **レイアウト モード**から選択を変更するセクションで、**スナップ**に**SnapToGrid**します。  
  
3.  設定を適用するには、[ok] をクリックします。  
  
4.  フォーム上のコントロールを選択し、その他のコントロールに移動します。 スナップ線が表示されないことに注意してください。  
  
## <a name="next-steps"></a>次の手順  
 スナップ線は、直観的に、フォームのコントロールの配置を提供します。 さらに詳しく調べるための推奨事項を次に示します。  
  
-   入れ子にしてください、<xref:System.Windows.Forms.GroupBox>内に別のコントロール<xref:System.Windows.Forms.GroupBox>コントロール。 場所、<xref:System.Windows.Forms.Button>子内のコントロール<xref:System.Windows.Forms.GroupBox>制御、および親内の別<xref:System.Windows.Forms.GroupBox>コントロール。 移動、<xref:System.Windows.Forms.Button>スナップ線がコンテナーの境界を越える方法を確認するには、約コントロール。  
  
-   列を作成する<xref:System.Windows.Forms.TextBox>コントロールとの対応する列<xref:System.Windows.Forms.Label>コントロール。 値を設定、<xref:System.Windows.Forms.Label>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`します。 移動するスナップ線を使用して、<xref:System.Windows.Forms.Label>コントロールが表示されるテキスト内のテキストに揃えて配置されますので、<xref:System.Windows.Forms.TextBox>コントロール。  
  
 Windows ユーザー インターフェイスの設計については、ブックを参照してください*Microsoft Windows User Experience, Official Guidelines for ユーザー インターフェイス開発者および設計者*Redmond、WA:。Microsoft Press、1999 年。 (USBN:0-7356-0566-1).  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [チュートリアル: Padding、Margin、AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](windows-forms-controls-padding-autosize.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
