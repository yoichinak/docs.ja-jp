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
ms.openlocfilehash: a35f2b4062edb18914c55046a69dcd9b8825d778
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353841"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト

このチュートリアルでは、@no__t 0 の複合コントロールを作成し、<xref:System.Windows.Forms.Integration.ElementHost> コントロールを使用して [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールおよびフォームでホストする方法について説明します。

このチュートリアルでは、2つの子コントロールを含む @no__t 0 <xref:System.Windows.Controls.UserControl> を実装します。 @No__t-0 は、3次元 (3-d) の円錐を表示します。 3-d オブジェクトのレンダリングは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] よりも @no__t 0 を使用する方がはるかに簡単です。 したがって、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> クラスをホストして [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] で3-d グラフィックスを作成することは理にかなっています。

このチュートリアルでは、以下のタスクを行います。

- @No__t-0 <xref:System.Windows.Controls.UserControl> を作成しています。

- Windows フォームホストプロジェクトを作成しています。

- @No__t-0 <xref:System.Windows.Controls.UserControl> をホストしています。

## <a name="prerequisites"></a>前提条件

このチュートリアルを実行するには、次のコンポーネントが必要です。

- Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>UserControl を作成する

1. @No__t-1 という名前の**WPF ユーザーコントロールライブラリ**プロジェクトを作成します。

2. @No__t-0 で UserControl1 を開きます。

3. 生成されたコードを次のコードに置き換えます。

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     このコードは、2つの子コントロールを含む @no__t 0 を定義します。 最初の子コントロールは @no__t 0 のコントロールです。2つ目は、3-d 円錐を表示する @no__t 1 コントロールです。

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>ホストプロジェクトを作成する

1. @No__t-1 という名前の**Windows フォーム App (.NET Framework)** プロジェクトをソリューションに追加します。

2. **ソリューションエクスプローラー**で、windowsフォーム統合アセンブリへの参照を追加します。このアセンブリには、windowsフォーム integration .dll という名前が付けられています。

3. 次の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アセンブリへの参照を追加します。

    - PresentationCore

    - PresentationFramework

    - WindowsBase

4. `HostingWpfUserControlInWf` への参照をプロジェクトに追加します。

5. ソリューションエクスプローラーで、`WpfUserControlHost` プロジェクトをスタートアッププロジェクトとして設定します。

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>UserControl をホストする

1. Windows フォームデザイナーで、Form1 を開きます。

2. プロパティウィンドウで、 **[イベント]** をクリックし、<xref:System.Windows.Forms.Form.Load> イベントをダブルクリックしてイベントハンドラーを作成します。

     コードエディターが開き、新しく生成された `Form1_Load` イベントハンドラーが表示されます。

3. Form1.cs のコードを次のコードに置き換えます。

     @No__t-0 イベントハンドラーは、`UserControl1` のインスタンスを作成し、そのインスタンスを @no__t 2 つの子コントロールのコレクションに追加します。 @No__t-0 コントロールは、フォームの子コントロールのコレクションに追加されます。

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. **F5** キーを押してアプリケーションをビルドし、実行します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Windows フォームサンプルでの WPF 複合コントロールのホスト](https://go.microsoft.com/fwlink/?LinkID=160001)
