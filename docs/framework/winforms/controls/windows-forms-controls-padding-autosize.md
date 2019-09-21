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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf0c6495b89033e75c27a1ff0cbceaff9d85f34
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987169"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>チュートリアル: 余白、余白、および AutoSize プロパティを使用してコントロールをレイアウトします

フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。 Visual Studio の**Windows フォームデザイナー**には、これを実現するためのさまざまなレイアウトツールが用意されています。 最も重要なのは<xref:System.Windows.Forms.Control.Margin%2A>、すべての Windows フォームコントロールに存在する、 <xref:System.Windows.Forms.Control.Padding%2A>、、および<xref:System.Windows.Forms.Control.AutoSize%2A>の各プロパティです。

<xref:System.Windows.Forms.Control.Margin%2A> プロパティは、その他のコントロールで、コントロールの枠線からの指定された距離を保持するコントロールの周囲のスペースを定義します。

<xref:System.Windows.Forms.Control.Padding%2A> プロパティは、コントロールの内容 (<xref:System.Windows.Forms.Control.Text%2A> プロパティの値など) で、コントロールの枠線からの指定した距離を保持するコントロールの内部のスペースを定義します。

次の図は、コントロールの <xref:System.Windows.Forms.Control.Padding%2A> プロパティと <xref:System.Windows.Forms.Control.Margin%2A> プロパティを示しています。

![Windows フォーム コントロールのパディングとマージン](./media/vs-winformpadmargin.gif)

プロパティ<xref:System.Windows.Forms.Control.AutoSize%2A>は、コントロールがその内容に自動的にサイズを変更するように指示します。 元<xref:System.Windows.Forms.Control.Size%2A>のプロパティの値よりも小さいサイズになることはなく、 <xref:System.Windows.Forms.Control.Padding%2A>プロパティの値が考慮されます。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには、Visual Studio が必要です。

## <a name="create-the-project"></a>プロジェクトの作成

1. Visual Studio で、という名前`LayoutExample`の**Windows アプリケーション**プロジェクトを作成します。

2. **Windows フォームデザイナー**でフォームを選択します。

## <a name="set-margins-for-controls"></a>コントロールの余白を設定する

コントロール間の既定の距離は、 <xref:System.Windows.Forms.Control.Margin%2A>プロパティを使用して設定できます。 コントロールを別のコントロールに移動すると、2つのコントロールの余白を示すスナップ線が表示されます。 移動するコントロールは、余白で定義されている距離にもスナップされます。

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Margin プロパティを使用してフォーム上のコントロールを配置する

1. <xref:System.Windows.Forms.Button> **ツールボックス**からフォームに2つのコントロールをドラッグします。

2. <xref:System.Windows.Forms.Button>コントロールの1つを選択し、ほぼタッチするまで、そのコントロールの近くに移動します。

   これらの間に表示されるスナップ線を観察します。 この距離は、2つのコントロール<xref:System.Windows.Forms.Control.Margin%2A>の値の合計です。 移動しようとしているコントロールは、この距離にスナップされます。 詳細について[は、「チュートリアル:スナップ線](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)を使用した Windows フォーム上のコントロールの配置。

3. <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.All%2A>[プロパティ] ウィンドウでエントリを展開し、プロパティを**20**に設定して、いずれかのコントロールのプロパティを変更します。<xref:System.Windows.Forms.Control.Margin%2A>

4. <xref:System.Windows.Forms.Button>コントロールの1つを選択し、そのコントロールの近くに移動します。

   余白の値の合計を定義するスナップ線が長くなり、コントロールが他のコントロールから離れた距離にスナップされます。

5. <xref:System.Windows.Forms.Padding.Top%2A> <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Margin%2A> [プロパティ] ウィンドウでエントリを展開し、プロパティを**5**に設定して、選択したコントロールのプロパティを変更します。

6. 選択したコントロールを他のコントロールの下に移動し、スナップ線が短くなっていることを確認します。 選択したコントロールを他のコントロールの左側に移動し、スナップ線が手順 4. で観察した値を保持していることを確認します。

7. <xref:System.Windows.Forms.Control.Margin%2A> プロパティ<xref:System.Windows.Forms.Padding.Top%2A> <xref:System.Windows.Forms.Padding.All%2A> 、 、、、の各側面を異なる値に設定することも、プロパティを使用してすべて同じ値に設定することもできます。<xref:System.Windows.Forms.Padding.Right%2A> <xref:System.Windows.Forms.Padding.Left%2A> <xref:System.Windows.Forms.Padding.Bottom%2A>

## <a name="set-padding-for-controls"></a>コントロールの埋め込みを設定する

アプリケーションに必要な正確なレイアウトを実現するために、コントロールには多くの場合、子コントロールが含まれます。 親コントロールの境界線に対する子コントロールの境界線の距離を指定する場合は、子<xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Margin%2A>コントロールのプロパティと共に親コントロールのプロパティを使用します。 プロパティ<xref:System.Windows.Forms.Control.Padding%2A>は、コントロールのコンテンツ ( <xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティなど) の境界への近接を制御するためにも使用されます。

### <a name="arrange-controls-on-your-form-using-padding"></a>パディングを使用してフォームにコントロールを配置する

1. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。

2. <xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティの値を**true**に変更します。

3. プロパティを<xref:System.Windows.Forms.Control.Padding%2A>変更するには<xref:System.Windows.Forms.Control.Padding%2A> 、 **[プロパティ]** ウィンドウでエントリを<xref:System.Windows.Forms.Padding.All%2A>展開し、プロパティを**5**に設定します。

   コントロールが拡張され、新しい埋め込み用の領域が提供されます。

4. <xref:System.Windows.Forms.GroupBox> ツールボックス **から** コントロールをフォームにドラッグします。 コントロールを<xref:System.Windows.Forms.Button> **[ツールボックス]** からコントロールにドラッグします。<xref:System.Windows.Forms.GroupBox> コントロールを<xref:System.Windows.Forms.GroupBox>コントロールの右下隅になるように配置します。 <xref:System.Windows.Forms.Button>

   コントロールとして表示される<xref:System.Windows.Forms.Button>スナップ線が、 <xref:System.Windows.Forms.GroupBox>コントロールの下と右の境界線に近づいていることを確認します。 これらのスナップ線は<xref:System.Windows.Forms.Control.Margin%2A> 、のプロパティ<xref:System.Windows.Forms.Button>に対応しています。

5. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A> **[プロパティ**] ウィンドウで<xref:System.Windows.Forms.Padding.All%2A>エントリを展開し、プロパティを**20**に設定して、コントロールのプロパティを変更します。<xref:System.Windows.Forms.GroupBox>

6. コントロール内の<xref:System.Windows.Forms.GroupBox>コントロールを選択し、の中央に移動します。 <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.GroupBox>

   スナップ線は、 <xref:System.Windows.Forms.GroupBox>コントロールの境界から離れた位置に表示されます。 この<xref:System.Windows.Forms.Button>距離は、コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティと<xref:System.Windows.Forms.GroupBox>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティの合計です。

## <a name="size-controls-automatically"></a>コントロールを自動的にサイズ変更する

アプリケーションによっては、デザイン時と同じように、実行時にコントロールのサイズが同じになることはありません。 たとえば、 <xref:System.Windows.Forms.Button>コントロールのテキストはデータベースから取得され、その長さは事前にわからない場合があります。

プロパティが<xref:System.Windows.Forms.Control.AutoSize%2A>に`true`設定されている場合、コントロールはその内容に合わせてサイズを変更します。 詳細については、「 [AutoSize プロパティの概要](autosize-property-overview.md)」を参照してください。

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>AutoSize プロパティを使用してフォーム上のコントロールを配置する

1. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。

2. <xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティの値を**true**に変更します。

3. コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティをこのボタンに変更すると、**その Text プロパティに長い文字列が**表示されます。 <xref:System.Windows.Forms.Button>

   変更をコミットすると、新しい<xref:System.Windows.Forms.Button>テキストに合わせてコントロールのサイズが変更されます。

4. <xref:System.Windows.Forms.Button> **ツールボックス**から別のコントロールをフォームにドラッグします。

5. コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティを "**このボタンには、テキストプロパティの長い文字列が含まれています**" に変更します。 <xref:System.Windows.Forms.Button>

   変更をコミットすると、 <xref:System.Windows.Forms.Button>コントロールのサイズが変更されず、テキストがコントロールの右端でクリップされます。

6. プロパティを<xref:System.Windows.Forms.Control.Padding%2A>変更するには<xref:System.Windows.Forms.Control.Padding%2A> 、 **[プロパティ]** ウィンドウでエントリを<xref:System.Windows.Forms.Padding.All%2A>展開し、プロパティを**5**に設定します。

   コントロールの内部のテキストは、4辺すべてにクリップされます。

7. コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを true に変更します。 <xref:System.Windows.Forms.Button>

   コントロール<xref:System.Windows.Forms.Button>は、文字列全体をカバーするようにサイズを変更します。 また、テキストの周囲に埋め込みが追加され<xref:System.Windows.Forms.Button>ているため、コントロールが4つの方向に広がります。

8. <xref:System.Windows.Forms.Button> ツールボックス **から** コントロールをフォームにドラッグします。 フォームの右下隅近くに配置します。

9. <xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティの値を**true**に変更します。

10. コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを、 <xref:System.Windows.Forms.AnchorStyles.Right>に設定します。<xref:System.Windows.Forms.AnchorStyles.Bottom> <xref:System.Windows.Forms.Button>

11. コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティを "**このボタンには、テキストプロパティの長い文字列が含まれています**" に変更します。 <xref:System.Windows.Forms.Button>

   変更をコミットすると、コントロール<xref:System.Windows.Forms.Button>は左に向かってサイズが変更されます。 一般に、自動サイズ変更では、 <xref:System.Windows.Forms.Control.Anchor%2A>プロパティ設定とは逆の方向にコントロールのサイズが増加します。

## <a name="autosize-and-autosizemode-properties"></a>AutoSize および System.windows.forms.datagridviewcolumn.autosizemode プロパティ

 一部のコントロールで`AutoSizeMode`は、プロパティをサポートしています。これにより、コントロールの自動サイズ変更動作をより細かく制御できます。

### <a name="use-the-autosizemode-property"></a>System.windows.forms.datagridviewcolumn.autosizemode プロパティを使用する

1. <xref:System.Windows.Forms.Panel> ツールボックス **から** コントロールをフォームにドラッグします。

2. <xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティの値を**true**に設定します。

3. コントロールを<xref:System.Windows.Forms.Button> **[ツールボックス]** からコントロールにドラッグします。<xref:System.Windows.Forms.Panel>

4. <xref:System.Windows.Forms.Button> コントロール<xref:System.Windows.Forms.Panel>の右下隅の近くにコントロールを配置します。

5. <xref:System.Windows.Forms.Panel>コントロールを選択し、右下のサイズ変更ハンドルを取得します。 コントロールの<xref:System.Windows.Forms.Panel>サイズを大きくしたり小さくしたりします。

   > [!NOTE]
   > <xref:System.Windows.Forms.Panel>コントロールのサイズは自由に変更できますが、 <xref:System.Windows.Forms.Button>コントロールの右下隅の位置よりもサイズを小さくすることはできません。 この動作は、 `AutoSizeMode`プロパティ<xref:System.Windows.Forms.AutoSizeMode.GrowOnly>の既定値であるによって指定されます。

6. <xref:System.Windows.Forms.Panel>コントロール<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>の`AutoSizeMode`プロパティの値をに設定します。

   コントロールは、コントロールを<xref:System.Windows.Forms.Button>囲むようにサイズを調整します。 <xref:System.Windows.Forms.Panel> コントロールの<xref:System.Windows.Forms.Panel>サイズを変更することはできません。

7. <xref:System.Windows.Forms.Button> コントロール<xref:System.Windows.Forms.Panel>の左上隅にコントロールをドラッグします。

   コントロール<xref:System.Windows.Forms.Panel>は、 <xref:System.Windows.Forms.Button>コントロールの新しい位置にサイズ変更されます。

## <a name="next-steps"></a>次の手順

Windows フォームアプリケーションにコントロールを配置するためのレイアウト機能は他にも多数あります。 いくつかの組み合わせを次に示します。

- <xref:System.Windows.Forms.TableLayoutPanel>コントロールを使用してフォームを作成します。 詳細について[は、「チュートリアル:TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)を使用して Windows フォームのコントロールを配置する。 <xref:System.Windows.Forms.TableLayoutPanel>コントロール<xref:System.Windows.Forms.Control.Margin%2A>の<xref:System.Windows.Forms.Control.Padding%2A>プロパティの値、および子コントロールのプロパティを変更してみてください。

- <xref:System.Windows.Forms.FlowLayoutPanel>コントロールを使用して同じ実験を試してみてください。 詳細について[は、「チュートリアル:FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)を使用して Windows フォームのコントロールを配置する。

- <xref:System.Windows.Forms.Panel>コントロールにドッキングされた子コントロールを試してみてください。 プロパティは、 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>プロパティのより一般的な実現方法であり、子コントロールを<xref:System.Windows.Forms.Panel>コントロールに配置し、子コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティをに設定することによって、このことを満たすことができます。 <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティをさまざまな値に設定し、効果を確認します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [AutoSize プロパティの概要](autosize-property-overview.md)
- [チュートリアル: TableLayoutPanel を使用した Windows フォームでのコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [チュートリアル: FlowLayoutPanel を使用した Windows フォームでのコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
