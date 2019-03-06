---
title: 'チュートリアル: WPF での Windows フォーム コントロールのホスト'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 8ef13ef89072f91c847a05facbcce344dda6ade2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374891"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>チュートリアル: WPF での Windows フォーム コントロールのホスト

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 豊富な機能セットには、多くのコントロールを提供します。 ただしを使用する可能性がありますも[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールに対して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。 たとえば、既存のかなりの投資を必要に応じて[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール、またはする必要があります、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]独自の機能を提供するコントロール。

このチュートリアルは、ホストする方法を示します、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>の control 権限、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コードを使用してページ。

このチュートリアルで示すタスクの完全なコード一覧については、次を参照してください。 [WPF のサンプルでの Windows フォーム コントロールをホストしている](https://go.microsoft.com/fwlink/?LinkID=160057)します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには Visual Studio が必要です。

## <a name="hosting-the-windows-forms-control"></a>Windows フォームのコントロールのホスト

### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox コントロールをホストするには

1.  という名前の WPF アプリケーション プロジェクトを作成する`HostingWfInWpf`します。

2.  次のアセンブリへの参照を追加します。

    -   WindowsFormsIntegration

    -   System.Windows.Forms

3.  MainWindow.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]します。

4.  名前、<xref:System.Windows.Controls.Grid>要素`grid1`します。

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5.  デザイン ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>要素。

6.  [プロパティ] ウィンドウ、**イベント**タブ。

7.  ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。

8.  処理するために次のコードを挿入、<xref:System.Windows.FrameworkElement.Loaded>イベント。

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. 次のコードを追加、ファイルの上部にある`Imports`または`using`ステートメント。

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. **F5** キーを押してアプリケーションをビルドし、実行します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: XAML を使用して、WPF での Windows フォーム コントロールをホストしています。](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [チュートリアル: WPF で Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールをホストしています。](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows フォーム コントロールおよび同等の WPF コントロール](windows-forms-controls-and-equivalent-wpf-controls.md)
- [WPF のサンプル Windows フォーム コントロールのホスト](https://go.microsoft.com/fwlink/?LinkID=160057)
