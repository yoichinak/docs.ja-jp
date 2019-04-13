---
title: '方法: ハイブリッド アプリケーションで視覚スタイルを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 7aa5208a4f378408a01a08a2f4c9dbf2edfa5243
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323604"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>方法: ハイブリッド アプリケーションで視覚スタイルを有効にする
このトピックでは、有効にする方法を示しています。[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]で視覚スタイルを、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でホストされているコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーション。  
  
 アプリケーションを呼び出す場合、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドでは、ほとんどの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]、アプリケーションの実行時に、コントロールに視覚スタイルは使用に自動的に[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]します。 詳細については、次を参照してください。 [Visual スタイルを使用しているコントロールのレンダリング](../../winforms/controls/rendering-controls-with-visual-styles.md)します。  
  
 このトピックで示すタスクの完全なコード一覧については、次を参照してください。[ハイブリッド アプリケーションのサンプルの Visual スタイルを有効にする](https://go.microsoft.com/fwlink/?LinkID=159986)します。  
  
## <a name="enabling-windows-forms-visual-styles"></a>Windows フォーム視覚スタイルの有効化  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Windows フォーム視覚スタイルを有効にするには  
  
1. 作成、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]という名前のアプリケーション プロジェクト`HostingWfWithVisualStyles`します。  
  
2. ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3. ツールボックスでダブルクリックして、<xref:System.Windows.Controls.Grid>を配置するにはアイコン、<xref:System.Windows.Controls.Grid>デザイン サーフェイス上の要素。  
  
4. [プロパティ] ウィンドウでの値を設定、<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>プロパティ**自動**します。  
  
5. デザイン ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>します。  
  
6. [プロパティ] ウィンドウ、**イベント**タブ。  
  
7. ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。
  
8. MainWindow.xaml.vb または MainWindow.xaml.cs で、処理するために次のコードを挿入、<xref:System.Windows.FrameworkElement.Loaded>イベント。  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. F5 キーを押してアプリケーションをビルドし、実行します。  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが visual スタイルで塗りつぶされます。  
  
## <a name="disabling-windows-forms-visual-styles"></a>Windows フォーム視覚スタイルの無効化  
 Visual スタイルを無効にするには、単にへの呼び出しを削除、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッド。  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Windows フォーム視覚スタイルを無効にするには  
  
1. コード エディターで MainWindow.xaml.vb または MainWindow.xaml.cs を開きます。  
  
2. 呼び出しをコメント、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッド。  
  
3. F5 キーを押してアプリケーションをビルドし、実行します。  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが既定のシステム スタイルで塗りつぶされます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [visual スタイルが使用されているコントロールのレンダリング](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [チュートリアル: WPF での Windows フォーム コントロールのホスト](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
