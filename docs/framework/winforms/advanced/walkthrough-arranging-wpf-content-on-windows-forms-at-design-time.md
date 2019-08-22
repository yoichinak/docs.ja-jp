---
title: 'チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658519"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>チュートリアル: デザイン時に Windows フォームに WPF コンテンツを配置する

この記事では、アンカーやスナップ線などの Windows フォームのレイアウト機能を使用して Windows Presentation Foundation (WPF) コントロールを配置する方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには Visual Studio が必要です。

## <a name="create-the-project"></a>プロジェクトの作成

Visual Studio を開き、Visual Basic またはC#という名前`ArrangeElementHost`の新しい Windows フォームアプリケーションプロジェクトを作成します。

> [!NOTE]
> WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。

## <a name="create-the-wpf-control"></a>WPF コントロールの作成

プロジェクトに WPF コントロール型を追加したら、フォーム状に配置できます。

1. 新しい WPF <xref:System.Windows.Controls.UserControl> をプロジェクトに追加します。 コントロール型の既定の名前である `UserControl1.xaml` を使用します。 詳細については、「[チュートリアル:デザイン時](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)に WINDOWS フォームに新しい WPF コンテンツを作成する。

2. デザイン ビューで `UserControl1` が選択されていることを確認します。

3. **[プロパティ]** ウィンドウで、プロパティ<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティの値を**200**に設定します。

4. <xref:System.Windows.Controls.Control.Background%2A>プロパティの値を**Blue**に設定します。

5. プロジェクトをビルドします。

## <a name="host-wpf-controls-in-a-layout-panel"></a>レイアウトパネルで WPF コントロールをホストする

その他の Windows フォーム コントロールを使用するのと同じ方法で、レイアウト パネルで WPF コントロールを使用できます。

1. Windows フォーム デザイナーで `Form1` を開きます。

2. **ツールボックス**で、コントロールを<xref:System.Windows.Forms.TableLayoutPanel>フォームにドラッグします。

3. コントロールのスマートタグパネルで、 **[最終行の削除]** を選択します。 <xref:System.Windows.Forms.TableLayoutPanel>

4. 幅と高さが大きくなるよう <xref:System.Windows.Forms.TableLayoutPanel> コントロールのサイズを変更します。

5. **ツールボックス**で、をダブルクリック`UserControl1`して、 <xref:System.Windows.Forms.TableLayoutPanel>コントロールの`UserControl1`最初のセルにのインスタンスを作成します。

   `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。

6. **ツールボックス**で、をダブルクリック`UserControl1`して、 <xref:System.Windows.Forms.TableLayoutPanel>コントロールの2番目のセルに別のインスタンスを作成します。

7. **[ドキュメントアウトライン]** ウィンドウで、 `tableLayoutPanel1`[] を選択します。

8. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.Control.Padding%2A>プロパティの値を10、10、10、10に設定します。

   両方の <xref:System.Windows.Forms.Integration.ElementHost> コントロールが、新しいレイアウトに収まるようにサイズ変更されました。

## <a name="use-snaplines-to-align-wpf-controls"></a>スナップ線を使用した WPF コントロールの配置

スナップ線により、フォームのコントロールの配置を簡単に調整できます。 スナップ線を使用して、WPF コントロールも配置することができます。 詳細については、「[チュートリアル:スナップ線](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)を使用した Windows フォーム上のコントロールの配置。

1. **ツールボックス**から、の`UserControl1`インスタンスをフォームにドラッグし、コントロールの<xref:System.Windows.Forms.TableLayoutPanel>下の領域に配置します。

   `UserControl1` のインスタンスは、`elementHost3` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。

2. スナップ線を使用して、`elementHost3` の左端を <xref:System.Windows.Forms.TableLayoutPanel> コントロールの左端に揃えます。

3. スナップ線を使用して、`elementHost3` のサイズを <xref:System.Windows.Forms.TableLayoutPanel> コントロールと同じ幅にします。

4. コントロール間に中央揃えのスナップ線が表示されるまで`elementHost3` を <xref:System.Windows.Forms.TableLayoutPanel> コントロールの方へ移動します。

5. **[プロパティ]** ウィンドウで、Margin プロパティの値を20、20、20、20に設定します。

6. 中央揃えのスナップ線がもう一度表示されるまで、`elementHost3` を <xref:System.Windows.Forms.TableLayoutPanel> コントロールから移動します。 中央揃えのスナップ線が、余白 20 を示すようになりました。

7. 左端`elementHost3`がの`elementHost1`左端に揃うまで右に移動します。

8. 右端が `elementHost2` の右端に配置されるまで、`elementHost3` の幅を変更します。

## <a name="anchor-and-dock-wpf-controls"></a>WPF コントロールのアンカーとドッキング

フォームでホストされている WPF コントロールは、他の Windows フォーム コントロールと同じ固定とドッキングの動作を持ちます。

1. `elementHost1` を選択します。

2. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.Control.Anchor%2A>プロパティを [**上]、[下]、[左]、[右**] に設定します。

3. <xref:System.Windows.Forms.TableLayoutPanel> コントロールを大きなサイズに変更します。

   `elementHost1` コントロールがセルを満たすようサイズ変更されます。

4. `elementHost2` を選択します。

5. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.Control.Dock%2A>プロパティの値をに<xref:System.Windows.Forms.DockStyle.Fill>設定します。

   `elementHost2` コントロールがセルを満たすようサイズ変更されます。

6. <xref:System.Windows.Forms.TableLayoutPanel> コントロールを選択します。

7. <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Top> に設定します。

8. `elementHost3` を選択します。

9. <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Fill> に設定します。

   `elementHost3` コントロールが、フォームの残りの領域を満たすようサイズ変更されます。

10. フォームのサイズを変更します。

    3 つすべての <xref:System.Windows.Forms.Integration.ElementHost> コントロールのサイズを適切に変更します。

    詳細については、「[方法 :TableLayoutPanel コントロール](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)に子コントロールを固定およびドッキングします。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [方法: TableLayoutPanel コントロールに子コントロールを固定およびドッキングする](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [方法: デザイン時にコントロールをフォームの端に揃える](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [移行と相互運用性](../../wpf/advanced/migration-and-interoperability.md)
- [WPF コントロールの使用](using-wpf-controls.md)
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
