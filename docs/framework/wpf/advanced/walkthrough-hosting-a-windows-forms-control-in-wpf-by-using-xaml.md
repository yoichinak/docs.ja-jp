---
title: 'チュートリアル: XAML を使用して、WPF での Windows フォーム コントロールをホストしています。'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 1566f27703e2603a5d70cf8cfc7a01a08c407f6a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379537"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>チュートリアル: XAML を使用して、WPF での Windows フォーム コントロールをホストしています。
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 豊富な機能セットには、多くのコントロールを提供します。 ただしを使用する可能性がありますも[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールに対して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。 たとえば、既存のかなりの投資を必要に応じて[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール、またはする必要があります、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]独自の機能を提供するコントロール。  
  
 このチュートリアルは、Windows フォームをホストする方法を示します<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>の control 権限、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用してページ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、[を使用して XAML サンプルで WPF での Windows フォーム コントロールをホストしている](https://go.microsoft.com/fwlink/?LinkID=160000)を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  

このチュートリアルを完了するには Visual Studio が必要です。  
  
## <a name="hosting-the-windows-forms-control"></a>Windows フォームのコントロールのホスト  
  
#### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox コントロールをホストするには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`HostingWfInWpfWithXaml`します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  MainWindow.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]します。  
  
4.  <xref:System.Windows.Window>要素では、次の名前空間マッピングを追加します。 `wf`名前空間のマッピングは、Windows フォーム コントロールを格納するアセンブリへの参照を確立します。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <xref:System.Windows.Controls.Grid>要素は、次の XAML を追加します。  
  
     <xref:System.Windows.Forms.MaskedTextBox>コントロールの子として作成されますが、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: WPF での Windows フォーム コントロールのホスト](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [チュートリアル: WPF で Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールをホストしています。](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows フォーム コントロールおよび同等の WPF コントロール](windows-forms-controls-and-equivalent-wpf-controls.md)
- [XAML のサンプルを使用して、WPF での Windows フォーム コントロールをホストしています。](https://go.microsoft.com/fwlink/?LinkID=160000)
