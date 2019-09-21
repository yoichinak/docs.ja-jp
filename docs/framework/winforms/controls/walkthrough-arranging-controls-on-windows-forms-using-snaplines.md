---
title: 'チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 83f0365ffb7335cb67c729c5a113e550c119191a
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987001"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置

フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。 Windows フォームデザイナーには、これを実現するための多数のレイアウトツールが用意されています。 最も重要なものの1つ<xref:System.Windows.Forms.Design.Behavior.SnapLine>は、機能です。

スナップ線を使用すると、他のコントロールとコントロールを整列する場所を正確に確認できます。 また、 [Windows ユーザーインターフェイスのガイドライン](/windows/win32/uxguide/guidelines)に従って、コントロール間の余白の推奨される距離も示しています。

スナップ線を使用すると、コントロールの配置が簡単になり、プロフェッショナルな外観と動作 (ルックアンドフィール) がわかりやすくなります。

## <a name="create-the-project"></a>プロジェクトの作成

1. Visual Studio で、"SnaplineExample" という名前の Windows ベースのアプリケーションプロジェクトを作成します。

2. フォームデザイナーでフォームを選択します。

## <a name="space-and-align-controls"></a>[スペースとコントロールの整列]

スナップ線を使用すると、フォーム上にコントロールを配置するための正確で直感的な方法が提供されます。 これは、選択したコントロールを、別のコントロールまたはコントロールのセットと一致する位置の近くに移動するときに表示されます。 他のコントロールを移動すると、選択した位置が提案された位置に "スナップ" されます。

### <a name="to-arrange-controls-using-snaplines"></a>スナップ線を使用してコントロールを配置するには

1. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。

2. コントロールを<xref:System.Windows.Forms.Button>フォームの右下隅に移動します。 <xref:System.Windows.Forms.Button>コントロールとして表示されるスナップ線は、フォームの下と右の境界線に近づいています。 これらのスナップ線には、コントロールの境界線とフォームとの間の推奨される距離が表示されます。

3. フォームの<xref:System.Windows.Forms.Button>境界線を囲むようにコントロールを移動し、スナップ線が表示される場所をメモします。 <xref:System.Windows.Forms.Button>操作が完了したら、フォームの中央付近にコントロールを移動します。

4. <xref:System.Windows.Forms.Button> **ツールボックス**から別のコントロールをフォームにドラッグします。

5. 2番目<xref:System.Windows.Forms.Button>のコントロールを、最初のコントロールとほぼ同じになるまで移動します。 両方のボタンのテキストベースラインに表示されるスナップ線に注目してください。移動しようとしているコントロールは、他のコントロールと正確に同じ位置にスナップします。

6. 最初のコントロール<xref:System.Windows.Forms.Button>のすぐ上に配置されるまで、2番目のコントロールを移動します。 両方のボタンの左端と右端に表示されるスナップ線に注目してください。移動するコントロールは、他のコントロールと正確に一致する位置にスナップされることに注意してください。

7. <xref:System.Windows.Forms.Button>コントロールの1つを選択し、ほぼタッチするまで、そのコントロールの近くに移動します。 これらの間に表示されるスナップ線に注意してください。 この距離は、コントロールの境界線の間の推奨される距離です。 また、移動しようとしているコントロールがこの位置にスナップされることにも注意してください。

8. <xref:System.Windows.Forms.Panel> **ツールボックス**からフォームに2つのコントロールをドラッグします。

9. <xref:System.Windows.Forms.Panel>コントロールの1つを、最初のコントロールの最上位レベルまで移動します。 両方のコントロールの上端と下端に表示されるスナップ線に注目します。また、移動しようとしているコントロールは、他のコントロールと正確に同じ位置にスナップします。

## <a name="align-to-form-and-container-margins"></a>フォームとコンテナーの余白に合わせる

スナップ線を使用すると、一貫した方法でコントロールを配置し、コンテナーの余白を整えることができます。

1. <xref:System.Windows.Forms.Button>コントロールの1つを選択し、スナップ線が表示されるまで、フォームの右の境界線の近くに移動します。 右の境界線からのスナップ線の距離は、コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティとフォームの<xref:System.Windows.Forms.Control.Padding%2A>プロパティ値の合計です。

   > [!NOTE]
   > フォームの<xref:System.Windows.Forms.Control.Padding%2A>プロパティが0、0、0、0に設定されている場合、Windows フォームデザイナーによって<xref:System.Windows.Forms.Control.Padding%2A> 、フォームには9、9、9、9の影付きの値が与えられます。 この動作をオーバーライドするには、0、0、0、0以外の値を割り当てます。

2. [プロパティ] ウィンドウで<xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Margin%2A>エントリを展開し、 プロパティを0に設定して、コントロールのプロパティの値を変更します。<xref:System.Windows.Forms.Padding.All%2A> 詳細について[は、「チュートリアル:埋め込み、余白、AutoSize プロパティ](windows-forms-controls-padding-autosize.md)を使用して Windows フォームコントロールをレイアウトします。

3. スナップ線<xref:System.Windows.Forms.Button>が表示されるまで、フォームの右境界線の近くにコントロールを移動します。 この距離は、フォームの<xref:System.Windows.Forms.Control.Padding%2A>プロパティの値によって指定されるようになりました。

4. <xref:System.Windows.Forms.GroupBox> ツールボックス **から** コントロールをフォームにドラッグします。

5. [プロパティ] ウィンドウで<xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A>エントリを展開し、 プロパティを10に設定して、コントロールのプロパティの値を変更します。<xref:System.Windows.Forms.Padding.All%2A>

6. コントロールを<xref:System.Windows.Forms.Button> **[ツールボックス]** からコントロールにドラッグします。<xref:System.Windows.Forms.GroupBox>

7. スナップ線が表示されるまで、コントロール<xref:System.Windows.Forms.GroupBox>の右の境界線の近くにコントロールを移動します。<xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button>コントロール内のコントロールを移動し、スナップ線が表示されている場所<xref:System.Windows.Forms.GroupBox>を確認します。

## <a name="align-to-grouped-controls"></a>グループ化されたコントロールに揃える

スナップ線を使用すると、グループ化されたコントロールだけ<xref:System.Windows.Forms.GroupBox>でなく、コントロール内のコントロールも配置できます。

1. フォーム上の2つのコントロールを選択します。 選択範囲を移動し、選択範囲と他のコントロールの間に表示されるスナップ線をメモします。

2. <xref:System.Windows.Forms.GroupBox> ツールボックス **から** コントロールをフォームにドラッグします。

3. コントロールを<xref:System.Windows.Forms.Button> **[ツールボックス]** からコントロールにドラッグします。<xref:System.Windows.Forms.GroupBox>

4. <xref:System.Windows.Forms.Button>コントロールの1つを選択し、 <xref:System.Windows.Forms.GroupBox>コントロールの周囲に移動します。 <xref:System.Windows.Forms.GroupBox>コントロールの端に表示されるスナップ線に注意してください。 また、 <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.GroupBox>コントロールに含まれるコントロールの端に表示されるスナップ線もメモします。 コンテナーコントロールの子であるコントロールは、スナップ線もサポートします。

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>スナップ線を使用して、サイズをアウトラインし、コントロールを配置する

1. **ツールボックス**で <xref:System.Windows.Forms.Button> コントロール アイコンをクリックします。 フォームにドラッグしないでください。

2. フォームのデザイン画面上にマウスポインターを移動します。 ポインターが <xref:System.Windows.Forms.Button> コントロール アイコンが付いた十字カーソルに変わることにご注意ください。 また、 <xref:System.Windows.Forms.Button>コントロールに対して配置された位置を示すために表示されるスナップ線もメモします。

3. マウス ボタンを押したままにします。

4. フォームの周りにマウスポインターをドラッグします。 コントロールの位置とサイズを示すアウトラインが描画されることに注意してください。

5. フォーム上の別のコントロールに合わせて、ポインターをドラッグします。 スナップ線が配置を示すように見えることに注意してください。

6. マウスのボタンを離します。 コントロールは、アウトラインによって示される位置とサイズで作成されます。

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>ツールボックスからコントロールをドラッグするときにスナップ線を使用する

1. コントロールを<xref:System.Windows.Forms.Button> **ツールボックス**からフォームにドラッグしますが、マウスボタンを離しません。

2. フォームのデザイン画面上にマウスポインターを移動します。 ポインターは、新しい<xref:System.Windows.Forms.Button>コントロールが作成される位置を示すように変更されることに注意してください。

3. フォームの周りにマウスポインターをドラッグします。 <xref:System.Windows.Forms.Button>コントロールに対して配置された位置を提案するために表示されるスナップ線に注意してください。 他のコントロールに合わせて配置された位置を検索します。

4. マウスのボタンを離します。 コントロールは、スナップ線によって示される位置に作成されます。

## <a name="resize-a-control-using-snaplines"></a>スナップ線を使用したコントロールのサイズ変更

1. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。

2. 角の<xref:System.Windows.Forms.Button>サイズ変更ハンドルとドラッグを取得して、コントロールのサイズを変更します。 詳細については、「[方法: Windows フォーム](how-to-resize-controls-on-windows-forms.md)のコントロールのサイズを変更します。

3. サイズ変更ハンドルをドラッグして、 <xref:System.Windows.Forms.Button>コントロールのいずれかの境界線が別のコントロールに揃うようにします。 スナップ線が表示されることに注意してください。 また、サイズ変更ハンドルはスナップ線によって示される位置にスナップされることにも注意してください。

4. 異なる方向<xref:System.Windows.Forms.Button>にコントロールのサイズを変更し、サイズ変更ハンドルを別のコントロールに揃えます。 整列を示すために、さまざまな向きでスナップ線がどのように表示されるかに注目してください。

## <a name="align-a-label-to-a-controls-text"></a>コントロールのテキストにラベルを揃える

1. <xref:System.Windows.Forms.TextBox> ツールボックス **から** コントロールをフォームにドラッグします。 フォームに<xref:System.Windows.Forms.TextBox>コントロールをドロップするときに、スマートタググリフをクリックし、 **[テキストを textBox1 に設定]** オプションを選択します。 詳細について[は、「チュートリアル:Windows フォームコントロール](performing-common-tasks-using-smart-tags-on-wf-controls.md)でスマートタグを使用して一般的なタスクを実行する。

2. <xref:System.Windows.Forms.Label> ツールボックス **から** コントロールをフォームにドラッグします。

3. <xref:System.Windows.Forms.Label> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true`に変更します。 コントロールの境界線は、表示テキストに合わせて調整されることに注意してください。

4. コントロールをコントロールの一番左<xref:System.Windows.Forms.TextBox>に移動し、コントロールの<xref:System.Windows.Forms.TextBox>下端に揃えます。 <xref:System.Windows.Forms.Label> 2つのコントロールの下端に沿って表示されるスナップ線に注意してください。

5. <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Label>テキストと<xref:System.Windows.Forms.TextBox>テキストが揃うまで、コントロールを少し上に移動します。 表示される別のスタイルのスナップ線を確認すると、両方のコントロールのテキストフィールドがアラインされたことを示します。

## <a name="use-snaplines-with-keyboard-navigation"></a>キーボードナビゲーションでスナップ線を使用する

1. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。 フォームの左上隅に配置します。

2. Ctrl+キーを押し**ながら下方向**キーを押します。 コントロールが、最初に使用可能な水平方向の配置位置にフォームを下方向に移動することに注意してください。

3. コントロールがフォームの下部に達するまで、 **Ctrl**+キーを押し**ながら下方向**キーを押します。 フォームの下に移動すると、その位置に注意してください。

4. Ctrl キーを押し**ながら**+**右方向**キーを押します。 コントロールは、フォーム上で、最初に使用可能な垂直方向の配置位置に移動することに注意してください。

5. コントロールがフォームの側に到達するまで、Ctrl キーを押し**ながら**+**右方向**キーを押します。 フォーム間を移動するときに占有される位置に注意してください。

6. 方向キーの組み合わせを使用して、コントロールをフォームの周囲に移動します。 コントロールが占有する位置と、コントロールに付随するスナップ線をメモします。

7. <xref:System.Windows.Forms.Button> **Shift**+**方向キー**を押して、コントロールのサイズを1ピクセルずつ増やします。

8. <xref:System.Windows.Forms.Button> **Ctrl**+Shift方向+**キー**を押して、スナップ線のインクリメントでコントロールのサイズを変更します。

## <a name="selectively-disable-snaplines"></a>スナップガイドラインを選択的に無効にする

1. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。

2. <xref:System.Windows.Forms.Button> ツールボックス **の**コントロール アイコンをダブルクリックします。 <xref:System.Windows.Forms.TableLayoutPanel>コントロールの最初のセルに新しいボタンコントロールが表示されることに注意してください。

3. **ツールボックス**のコントロール<xref:System.Windows.Forms.Button>アイコンを2回ダブルクリックします。 これにより、 <xref:System.Windows.Forms.TableLayoutPanel>コントロールに1つの空のセルが残されます。

4. コントロールを<xref:System.Windows.Forms.Button> **[ツールボックス]** から<xref:System.Windows.Forms.TableLayoutPanel>コントロールの空のセルにドラッグします。 スナップ線は表示されないことに注意してください。

5. コントロールをコントロール<xref:System.Windows.Forms.TableLayoutPanel>の外にドラッグ<xref:System.Windows.Forms.TableLayoutPanel>し、コントロールの周囲に移動します。 <xref:System.Windows.Forms.Button> スナップ線が再び表示されることに注意してください。

## <a name="disable-snaplines"></a>スナップガイドラインの無効化

**Alt**キーを押しながら、コントロールをフォームの上に移動します。

スナップ線は表示されず、コントロールは潜在的な配置位置にスナップされません。

### <a name="to-disable-snaplines-in-the-design-environment"></a>デザイン環境でスナップガイドラインを無効にするには

1. **[ツール]** メニューの **[オプション]** ダイアログボックスを開きます。 **[Windows フォームデザイナー]** を選択します。

2. **[全般]** ノードを選択します。 **[レイアウトモード]** セクションで、選択範囲を**スナップガイドライン**から**SnapToGrid**に変更します。

3. **[OK]** を選択して設定を適用します。

4. フォーム上のコントロールを選択し、他のコントロールの周囲に移動します。 スナップ線が表示されないことに注意してください。

## <a name="next-steps"></a>次の手順

スナップ線は、フォーム上にコントロールを配置するための直感的な手段を提供します。 さらに詳しく調べるための推奨事項を次に示します。

- コントロールを別<xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.GroupBox>のコントロール内に入れ子にしてみてください。 <xref:System.Windows.Forms.Button>子<xref:System.Windows.Forms.GroupBox>コントロール内にコントロールを配置し、もう1つは親コントロール内に配置します。 <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Button>コントロールを移動して、スナップ線がコンテナーの境界を越えていることを確認します。

- コントロールの列<xref:System.Windows.Forms.TextBox>と、コントロールの<xref:System.Windows.Forms.Label>対応する列を作成します。 <xref:System.Windows.Forms.Label> `true`コントロールのプロパティの値をに設定します。<xref:System.Windows.Forms.Control.AutoSize%2A> コントロールを移動するに<xref:System.Windows.Forms.Label>は、スナップ線を使用して、表示される<xref:System.Windows.Forms.TextBox>テキストがコントロール内のテキストに合わせられるようにします。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [チュートリアル: FlowLayoutPanel を使用した Windows フォームでのコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [チュートリアル: TableLayoutPanel を使用した Windows フォームでのコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [チュートリアル: パディング、余白、AutoSize プロパティを使用して Windows フォームコントロールをレイアウトする](windows-forms-controls-padding-autosize.md)
