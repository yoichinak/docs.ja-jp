---
title: 'チュートリアル: WPF での ActiveX コントロールのホスト'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: c27449da5ee0351e472eaba7d930a774979db65f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781382"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>チュートリアル: WPF での ActiveX コントロールのホスト
ブラウザーでの強化された操作を有効にするを使用できます[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]でコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーション。 このチュートリアルでは、ホストする方法、[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]上のコントロールとして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。

 このチュートリアルでは、以下のタスクを行います。

- プロジェクトの作成。

- ActiveX コントロールを作成します。

- WPF ページ上の ActiveX コントロールをホストします。

 使用する方法を理解するときに、このチュートリアルを完了すると、[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]でコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーション。

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルを実行するには、次のコンポーネントが必要です。

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] Visual Studio がインストールされているコンピューターにインストールします。

- Visual Studio 2010。

## <a name="creating-the-project"></a>プロジェクトの作成

#### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには

1. という名前の WPF アプリケーション プロジェクトを作成する`HostingAxInWpf`します。

2. Windows フォーム コントロール ライブラリ プロジェクトをソリューションに追加し、プロジェクト名前`WmpAxLib`します。

3. WmpAxLib プロジェクトでは、wmp.dll の名前は、Windows Media Player アセンブリへの参照を追加します。

4. 開く、**ツールボックス**します。

5. 右クリックし、**ツールボックス**、 をクリックし、**アイテムの選択**します。

6. をクリックして、 **COM コンポーネント**] タブで、[、 **Windows Media Player**コントロールをクリックして**OK**。

     Windows Media Player コントロールに追加されます、**ツールボックス**します。

7. ソリューション エクスプ ローラーで右クリックし、 **UserControl1**ファイルを開き、をクリックし、**の名前を変更**します。

8. 名を変更して`WmpAxControl.vb`または`WmpAxControl.cs`、言語によって異なります。

9. すべての参照の名前を変更するメッセージが表示されたら、クリックして**はい**します。

## <a name="creating-the-activex-control"></a>ActiveX コントロールを作成します。
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 自動的に生成、<xref:System.Windows.Forms.AxHost>のラッパー クラスを[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]デザイン サーフェイスにコントロールを追加するときを制御します。 次の手順では、AxInterop.WMPLib.dll という名前のマネージ アセンブリを作成します。

#### <a name="to-create-the-activex-control"></a>ActiveX コントロールを作成するには

1. Windows フォーム デザイナーで、WmpAxControl.vb またはに応じてを開きます。

2. **ツールボックス**、デザイン画面に、Windows Media Player コントロールを追加します。

3. [プロパティ] ウィンドウで、Windows Media Player コントロールの値を設定<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>します。

4. WmpAxLib コントロール ライブラリ プロジェクトをビルドします。

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>WPF ページ上の ActiveX コントロールをホストしています。

#### <a name="to-host-the-activex-control"></a>ActiveX コントロールをホストするには

1. HostingAxInWpf プロジェクトで生成されたへの参照を追加[!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)]相互運用機能アセンブリ。

     このアセンブリは、AxInterop.WMPLib.dll の名前は、Windows Media Player コントロールがインポートされるときに、WmpAxLib プロジェクトの Debug フォルダーに追加されました。

2. これは、WindowsFormsIntegration.dll がという名前 WindowsFormsIntegration アセンブリへの参照を追加します。

3. 参照を追加、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] System.Windows.Forms.dll をという名前のアセンブリ。

4. WPF デザイナーで、MainWindow.xaml を開きます。

5. 名前、<xref:System.Windows.Controls.Grid>要素`grid1`します。

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. デザイン ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>要素。

7. [プロパティ] ウィンドウ、**イベント**タブ。

8. ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。

9. 処理するために次のコードを挿入、<xref:System.Windows.FrameworkElement.Loaded>イベント。

     このコードのインスタンスを作成、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を制御しのインスタンスを追加、`AxWindowsMediaPlayer`の子としてコントロール。

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: WPF で Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールをホストしています。](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
