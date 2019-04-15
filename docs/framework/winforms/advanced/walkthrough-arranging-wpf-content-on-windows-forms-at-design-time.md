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
ms.openlocfilehash: 306c042fe432f0c087ceb1b5ff6b5aec0fe0bbc7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327309"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置
このチュートリアルでは、固定やスナップ線などの Windows フォームのレイアウト機能を使用して、Windows Presentation Foundation (WPF) コントロールを配置する方法を説明します。

 このチュートリアルでは次のタスクを実行します。

-   プロジェクトを作成する。

-   WPF コントロールを作成する。

-   レイアウト パネルで WPF コントロールをホストする。

-   WPF コントロールを配置するスナップ線を使用する。

-   WPF コントロールを固定してドッキングする。

> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 まず、Windows フォーム プロジェクトを作成します。  
  
> [!NOTE]
>  WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
-   Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成する`ArrangeElementHost`します。  
  
## <a name="creating-the-wpf-control"></a>WPF コントロールの作成  
 プロジェクトに WPF コントロール型を追加したら、フォーム状に配置できます。  
  
#### <a name="to-create-wpf-controls"></a>WPF コントロールを作成するには  
  
1. 新しい WPF <xref:System.Windows.Controls.UserControl> をプロジェクトに追加します。 コントロール型の既定の名前である `UserControl1.xaml` を使用します。 詳細については、「[チュートリアル:デザイン時に Windows フォームで新しい WPF コンテンツを作成する](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)します。  
  
2. デザイン ビューで `UserControl1` が選択されていることを確認します。 詳細については、「[方法 :選択し、デザイン サーフェイス上の要素の移動](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))します。  
  
3. **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`します。  
  
4. <xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `Blue` に設定します。  
  
5. プロジェクトをビルドします。  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>レイアウト パネルで WPF コントロールをホストする  
 その他の Windows フォーム コントロールを使用するのと同じ方法で、レイアウト パネルで WPF コントロールを使用できます。  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>レイアウト パネルで WPF コントロールをホストするには  
  
1. Windows フォーム デザイナーで `Form1` を開きます。  
  
2. **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>コントロールをフォームにします。  
  
3. <xref:System.Windows.Forms.TableLayoutPanel>コントロールのスマート タグ パネルで、**最後の行を削除**します。  
  
4. 幅と高さが大きくなるよう <xref:System.Windows.Forms.TableLayoutPanel> コントロールのサイズを変更します。  
  
5. **ツールボックス**、ダブルクリックして`UserControl1`のインスタンスを作成する`UserControl1`の最初のセルで、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
6. **ツールボックス**、ダブルクリックして`UserControl1`の 2 番目のセルで別のインスタンスを作成する、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
7. **ドキュメント アウトライン**ウィンドウで、`tableLayoutPanel1`します。 詳細については、次を参照してください。[ドキュメント アウトライン ウィンドウ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf)します。  
  
8. **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Forms.Control.Padding%2A>プロパティを`10, 10, 10, 10`します。  
  
     両方の <xref:System.Windows.Forms.Integration.ElementHost> コントロールが、新しいレイアウトに収まるようにサイズ変更されました。  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>WPF コントロールを配置するスナップ線を使用する  
 スナップ線により、フォームのコントロールの配置を簡単に調整できます。 スナップ線を使用して、WPF コントロールも配置することができます。 詳細については、「[チュートリアル:フォームのスナップ線を使用して Windows 上のコントロール](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)します。  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>WPF コントロールを配置するスナップ線を使用するには  
  
1. **ツールボックス**のインスタンスをドラッグ`UserControl1`をフォームに下の領域に配置し、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
     `UserControl1` のインスタンスは、`elementHost3` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
2. スナップ線を使用して、`elementHost3` の左端を <xref:System.Windows.Forms.TableLayoutPanel> コントロールの左端に揃えます。  
  
3. スナップ線を使用して、`elementHost3` のサイズを <xref:System.Windows.Forms.TableLayoutPanel> コントロールと同じ幅にします。  
  
4. コントロール間に中央揃えのスナップ線が表示されるまで`elementHost3` を <xref:System.Windows.Forms.TableLayoutPanel> コントロールの方へ移動します。  
  
5. **プロパティ**ウィンドウで、余白プロパティの値を設定する`20, 20, 20, 20`します。  
  
6. 中央揃えのスナップ線がもう一度表示されるまで、`elementHost3` を <xref:System.Windows.Forms.TableLayoutPanel> コントロールから移動します。 中央揃えのスナップ線が、余白 20 を示すようになりました。  
  
7. 左端が `elementHost1` の左端に配置されるまで、`elementHost3` を右に移動します。  
  
8. 右端が `elementHost2` の右端に配置されるまで、`elementHost3` の幅を変更します。  
  
## <a name="anchoring-and-docking-wpf-controls"></a>WPF コントロールの固定およびドッキング  
 フォームでホストされている WPF コントロールは、他の Windows フォーム コントロールと同じ固定とドッキングの動作を持ちます。  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>WPF コントロールを固定してドッキングするには  
  
1. `elementHost1` を選択します。  
  
2. **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを**Top、Bottom、Left、Right**します。  
  
3. <xref:System.Windows.Forms.TableLayoutPanel> コントロールを大きなサイズに変更します。  
  
     `elementHost1` コントロールがセルを満たすようサイズ変更されます。  
  
4. `elementHost2` を選択します。  
  
5. **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>します。  
  
     `elementHost2` コントロールがセルを満たすようサイズ変更されます。  
  
6. <xref:System.Windows.Forms.TableLayoutPanel> コントロールを選択します。  
  
7. <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Top> に設定します。  
  
8. `elementHost3` を選択します。  
  
9. <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Fill> に設定します。  
  
     `elementHost3` コントロールが、フォームの残りの領域を満たすようサイズ変更されます。  
  
10. フォームのサイズを変更します。  
  
     3 つすべての <xref:System.Windows.Forms.Integration.ElementHost> コントロールのサイズを適切に変更します。  
  
     詳細については、「[方法 :固定およびドッキング TableLayoutPanel コントロールで子コントロール](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [方法: デザイン時にフォームの端に合わせてコントロールを配置する](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [移行と相互運用性](../../wpf/advanced/migration-and-interoperability.md)
- [WPF コントロールの使用](using-wpf-controls.md)
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
