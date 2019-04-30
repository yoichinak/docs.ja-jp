---
title: 'チュートリアル: Padding、Margin、AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト'
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
ms.openlocfilehash: 230c7cb80ce6b8a29f7334ed0f8d297fd829faf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009085"
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>チュートリアル: Padding、Margin、AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト
フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。 **Windows フォーム デザイナー**はこれを実現する多くのレイアウト ツールを提供します。 3 つ最も重要なは、 <xref:System.Windows.Forms.Control.Margin%2A>、 <xref:System.Windows.Forms.Control.Padding%2A>、および<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティで、すべての Windows フォーム コントロールの上に存在します。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> プロパティは、その他のコントロールで、コントロールの枠線からの指定された距離を保持するコントロールの周囲のスペースを定義します。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> プロパティは、コントロールの内容 (<xref:System.Windows.Forms.Control.Text%2A> プロパティの値など) で、コントロールの枠線からの指定した距離を保持するコントロールの内部のスペースを定義します。  
  
 次の図は、コントロールの <xref:System.Windows.Forms.Control.Padding%2A> プロパティと <xref:System.Windows.Forms.Control.Margin%2A> プロパティを示しています。  
  
 ![フォーム コントロールの Windows のパディングとマージン](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A>プロパティは自動的にその内容をそれ自体のサイズのコントロールに指示します。 自身の元の値より小さいサイズがない<xref:System.Windows.Forms.Control.Size%2A>プロパティ、およびそれがの値のアカウントがその<xref:System.Windows.Forms.Control.Padding%2A>プロパティ。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
- Windows フォーム プロジェクトの作成  
  
- コントロールのマージンの設定  
  
- コントロールの埋め込みの設定  
  
- コントロールを自動的にサイズ変更  
  
 終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
- 作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1. 作成、 **Windows アプリケーション**という名前のプロジェクト`LayoutExample`します。 詳細については、「[方法 :Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)です。  
  
2. フォームを選択、 **Windows フォーム デザイナー**します。  
  
## <a name="setting-margins-for-your-controls"></a>コントロールのマージンの設定  
 使用して、コントロールの間で既定の距離を設定することができます、<xref:System.Windows.Forms.Control.Margin%2A>プロパティ。 コントロールを移動するときに、別のコントロールに十分、2 つのコントロールの余白を示すスナップ線が表示されます。 移動中のコントロールも、余白で定義された距離にスナップします。  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Margin プロパティを使用して、フォーム上のコントロールを配置するには  
  
1. 2 つをドラッグして<xref:System.Windows.Forms.Button>コントロールを**ツールボックス**フォームにします。  
  
2. いずれかの選択、<xref:System.Windows.Forms.Button>を制御し、それらはほとんど触れることまで、その他の近くに移動します。  
  
     それらの間に表示されるスナップ線を確認します。 この距離は、2 つのコントロールの<xref:System.Windows.Forms.Control.Margin%2A>値。 移動中のコントロールは、この距離にスナップされます。 詳細については、次を参照してください。[チュートリアル。フォームのスナップ線を使用して Windows 上のコントロール](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)します。  
  
3. 変更、<xref:System.Windows.Forms.Control.Margin%2A>を展開して、コントロールのいずれかのプロパティ、<xref:System.Windows.Forms.Control.Margin%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.All%2A>プロパティを 20 にします。  
  
4. いずれかの選択、<xref:System.Windows.Forms.Button>を制御し、その他の近くに移動します。  
  
     スナップ線を定義する余白の値の合計が長いと、コントロールが他のコントロールからの距離が長くにスナップされます。  
  
5. 変更、<xref:System.Windows.Forms.Control.Margin%2A>を展開して、選択したコントロールのプロパティ、<xref:System.Windows.Forms.Control.Margin%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.Top%2A>プロパティを 5 にします。  
  
6. その他のコントロールの下の選択したコントロールを移動し、スナップ線が短いことを確認します。 選択したコントロールを他のコントロールの左に移動し、スナップ線が手順 4. で計測された値を保持することを確認します。  
  
7. それぞれの側面を設定することができます、<xref:System.Windows.Forms.Control.Margin%2A>プロパティ、 <xref:System.Windows.Forms.Padding.Left%2A>、 <xref:System.Windows.Forms.Padding.Top%2A>、 <xref:System.Windows.Forms.Padding.Right%2A>、 <xref:System.Windows.Forms.Padding.Bottom%2A>、または別の値と同じ値にすべてを設定することができます、<xref:System.Windows.Forms.Padding.All%2A>プロパティ。  
  
## <a name="setting-padding-for-your-controls"></a>コントロールの埋め込みの設定  
 アプリケーションに必要な正確なレイアウトを実現するために、コントロールは多くの場合、子コントロールを含まれます。 親コントロールの境界線に子コントロールの境界線の近接度を指定する場合を使用して、親コントロールの<xref:System.Windows.Forms.Control.Padding%2A>と共に子コントロールのプロパティ<xref:System.Windows.Forms.Control.Margin%2A>プロパティ。 <xref:System.Windows.Forms.Control.Padding%2A>コントロールのコンテンツの近接度を制御するプロパティを使用しても (たとえば、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティ) の境界線にします。  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>パディングを使用して、フォーム上のコントロールを配置するには  
  
1. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true`に変更します。  
  
3. 変更、<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.All%2A>プロパティを 5 にします。  
  
     コントロールを拡張する新しい埋め込みのために確保します。  
  
4. <xref:System.Windows.Forms.GroupBox> ツールボックス **から** コントロールをフォームにドラッグします。 ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**に、<xref:System.Windows.Forms.GroupBox>コントロール。 位置、<xref:System.Windows.Forms.Button>制御の右下隅のフラッシュができるので、<xref:System.Windows.Forms.GroupBox>コントロール。  
  
     として表示されるスナップ線を観察、<xref:System.Windows.Forms.Button>下および右の境界線のコントロールが近づく、<xref:System.Windows.Forms.GroupBox>コントロール。 これらのスナップ線が対応する、<xref:System.Windows.Forms.Control.Margin%2A>のプロパティ、<xref:System.Windows.Forms.Button>します。  
  
5. 変更、<xref:System.Windows.Forms.GroupBox>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.All%2A>プロパティを 20 にします。  
  
6. 選択、<xref:System.Windows.Forms.Button>コントロール内の<xref:System.Windows.Forms.GroupBox>を制御しの中央に移動、<xref:System.Windows.Forms.GroupBox>します。  
  
     枠線から遠隔地にスナップ線が表示される、<xref:System.Windows.Forms.GroupBox>コントロール。 この距離の合計、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティおよび<xref:System.Windows.Forms.GroupBox>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティ。  
  
## <a name="automatically-sizing-your-controls"></a>コントロールを自動的にサイズ変更  
 一部のアプリケーションでコントロールのサイズはいないと同じである実行時にデザイン時にでした。 テキストを<xref:System.Windows.Forms.Button>コントロールなどの可能性がありますがから取得した、データベースをその長さが事前にわかっていません。  
  
 ときに、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティに設定されて`true`、そのコンテンツへ自体、コントロールのサイズが。 詳細については、次を参照してください。 [AutoSize プロパティの概要](autosize-property-overview.md)します。  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>AutoSize プロパティを使用して、フォーム上のコントロールを配置するには  
  
1. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true`に変更します。  
  
3. 変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティを"**このボタンがテキスト プロパティの長い文字列**"。  
  
     変更をコミットすると、<xref:System.Windows.Forms.Button>コントロールでは、新しいテキストが収まるようにサイズ変更されます。  
  
4. もう 1 つドラッグ<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**フォームにします。  
  
5. 変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティを"**このボタンがテキスト プロパティの長い文字列**"。  
  
     変更をコミットすると、<xref:System.Windows.Forms.Button>コントロール サイズ変更されない、自体と、コントロールの右端でのテキストが切り取られます。  
  
6. 変更、<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.All%2A>プロパティを 5 にします。  
  
     コントロールの内部でテキストが、4 辺すべてにつき切り取られます。  
  
7. 変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`します。  
  
     <xref:System.Windows.Forms.Button>自体文字列全体を囲むようにコントロールをサイズ変更します。 テキストを囲むパディングが追加されても、原因、<xref:System.Windows.Forms.Button>コントロールをすべて次の 4 つの方向に展開します。  
  
8. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。 フォームの右下隅近くに配置します。  
  
9. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true`に変更します。  
  
10. 設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを<xref:System.Windows.Forms.AnchorStyles.Right>、<xref:System.Windows.Forms.AnchorStyles.Bottom>します。  
  
11. 変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティを"**このボタンがテキスト プロパティの長い文字列**"。  
  
     変更をコミットすると、<xref:System.Windows.Forms.Button>コントロールは左方向サイズ変更します。 自動サイズ変更が反対方向にコントロールのサイズを大きく一般に、その<xref:System.Windows.Forms.Control.Anchor%2A>プロパティの設定。  
  
## <a name="autosize-and-autosizemode-properties"></a>自動サイズ調整と AutoSizeMode プロパティ  
 一部のコントロールのサポート、`AutoSizeMode`プロパティ、コントロールの自動サイズ変更動作をより細かく管理できます。  
  
#### <a name="to-use-the-autosizemode-property"></a>AutoSizeMode プロパティを使用するには  
  
1. <xref:System.Windows.Forms.Panel> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2. 値を設定、<xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`します。  
  
3. ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**に、<xref:System.Windows.Forms.Panel>コントロール。  
  
4. 場所、<xref:System.Windows.Forms.Button>の右上隅のコントロール、<xref:System.Windows.Forms.Panel>コントロール。  
  
5. 選択、<xref:System.Windows.Forms.Panel>を制御し、右下のサイズ変更ハンドルを取得します。 サイズ変更、<xref:System.Windows.Forms.Panel>コントロールを大きくしたり小さくします。  
  
    > [!NOTE]
    >  サイズを変更することが自由に、<xref:System.Windows.Forms.Panel>コントロールがサイズを調整できないことの位置より小さい、<xref:System.Windows.Forms.Button>コントロールの右上隅にあります。 この動作がの既定値で指定された、`AutoSizeMode`プロパティ<xref:System.Windows.Forms.AutoSizeMode.GrowOnly>します。  
  
6. 値を設定、<xref:System.Windows.Forms.Panel>コントロールの`AutoSizeMode`プロパティを<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>します。  
  
     <xref:System.Windows.Forms.Panel>コントロールのサイズを囲む、<xref:System.Windows.Forms.Button>コントロール。 サイズを変更することはできません、<xref:System.Windows.Forms.Panel>コントロール。  
  
7. ドラッグ、<xref:System.Windows.Forms.Button>コントロールの左上隅に向かって、<xref:System.Windows.Forms.Panel>コントロール。  
  
     <xref:System.Windows.Forms.Panel>にコントロールをサイズ変更、<xref:System.Windows.Forms.Button>コントロールの新しい位置。  
  
## <a name="next-steps"></a>次の手順  
 Windows フォーム アプリケーションでコントロールの配置の他の多くのレイアウト機能があります。 アクセスしてみて、いくつかの組み合わせを次に示します。  
  
- 使用してフォームを構築、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 詳細については、次を参照してください。[チュートリアル。TableLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)します。 値を変更してみて、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティだけでなく<xref:System.Windows.Forms.Control.Margin%2A>その子コントロールのプロパティ。  
  
- 使用して同じ実験を実行してください、<xref:System.Windows.Forms.FlowLayoutPanel>コントロール。 詳細については、次を参照してください。[チュートリアル。FlowLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)します。  
  
- 子コントロールのドッキングを使用した実験を<xref:System.Windows.Forms.Panel>コントロール。 <xref:System.Windows.Forms.Control.Padding%2A>プロパティの全般的な実現は、<xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>プロパティを満たすことが自分子コントロールを配置することで大文字と小文字である、<xref:System.Windows.Forms.Panel>コントロールと子コントロールの設定<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>. 設定、<xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティをさまざまな値の影響に注意してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [AutoSize プロパティの概要](autosize-property-overview.md)
- [チュートリアル: TableLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [チュートリアル: FlowLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [チュートリアル: スナップ線を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
