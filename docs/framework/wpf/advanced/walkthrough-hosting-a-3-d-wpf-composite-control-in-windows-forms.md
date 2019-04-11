---
title: 'チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: e5b98a33f29759a81ba1cbc1fefbd45c0e5bf736
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330169"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト

このチュートリアルでは、作成する方法、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合を制御し、ホストすることで[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールとフォームを使用して、<xref:System.Windows.Forms.Integration.ElementHost>コントロール。

このチュートリアルでは、実装、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 2 つの子コントロールを格納しています。 <xref:System.Windows.Controls.UserControl> 3 次元 (3 D) の円錐形が表示されます。 3-D オブジェクトのレンダリングが容易、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]よりで[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]します。 そのため、にとってホスト、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>の 3-D グラフィックスを作成するクラス[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]します。

このチュートリアルでは、以下のタスクを行います。

-   作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>します。

-   Windows フォーム ホスト プロジェクトを作成します。

-   ホストしている、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

-   Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>UserControl を作成します。

1. 作成、 **WPF ユーザー コントロール ライブラリ**という名前のプロジェクト`HostingWpfUserControlInWf`します。

2. UserControl1.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]します。

3. 生成されたコードを次のコードに置き換えます。

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     このコードを定義、 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> 2 つの子コントロールを格納しています。 最初の子コントロールは、<xref:System.Windows.Controls.Label?displayProperty=nameWithType>コントロールは、2 つ目は、 <xref:System.Windows.Controls.Viewport3D> 3-D 円錐を表示するコントロール。

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>ホスト プロジェクトを作成します。

1. 追加、 **WPF アプリ (.NET Framework)** という名前のプロジェクト`WpfUserControlHost`をソリューションにします。 詳細については、「[チュートリアル:初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)します。

2. **ソリューション エクスプ ローラー**、WindowsFormsIntegration.dll という WindowsFormsIntegration アセンブリへの参照を追加します。

3. 次に参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

4. `HostingWpfUserControlInWf` への参照をプロジェクトに追加します。

5. ソリューション エクスプローラで、設定、`WpfUserControlHost`プロジェクトをスタートアップ プロジェクトです。

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>ユーザー コントロールをホストします。

1. Windows フォーム デザイナーで、Form1 を開きます。

2. [プロパティ] ウィンドウで次のようにクリックします。**イベント**、し、ダブルクリック、<xref:System.Windows.Forms.Form.Load>イベント ハンドラーを作成するイベント。

     コード エディターが新しく生成されたに`Form1_Load`イベント ハンドラー。

3. Form1.cs のコードを次のコードに置き換えます。

     `Form1_Load`イベント ハンドラーのインスタンスを作成する`UserControl1`し、追加の接続を受け付ける、<xref:System.Windows.Forms.Integration.ElementHost>子コントロールのコントロールのコレクション。 <xref:System.Windows.Forms.Integration.ElementHost>コントロールの子コントロールのフォームのコレクションに追加されます。

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. **F5** キーを押してアプリケーションをビルドし、実行します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Windows フォームのサンプルで WPF 複合コントロールのホスト](https://go.microsoft.com/fwlink/?LinkID=160001)