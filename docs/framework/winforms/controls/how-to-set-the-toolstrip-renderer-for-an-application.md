---
title: '方法: アプリケーションの ToolStrip レンダラーを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: 8f3d2f2ed290c61c898a9f6159f213a8f68731ee
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707288"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a>方法: アプリケーションの ToolStrip レンダラーを設定します。
<xref:System.Windows.Forms.ToolStrip> コントロールの外観を個別にカスタマイズすることも、アプリケーションのすべての <xref:System.Windows.Forms.ToolStrip> コントロールをカスタマイズすることもできます。  
  
## <a name="example"></a>例  
 次のコード例は、カスタムのレンダラーを <xref:System.Windows.Forms.ToolStrip> コントロールと <xref:System.Windows.Forms.MenuStrip> コントロールに選択的に適用する方法を示します。  
  
 このコード例を使用するには、アプリケーションをコンパイルして実行し、<xref:System.Windows.Forms.ComboBox> コントロールからのカスタム表示の範囲を選択します。 **[適用]** をクリックしてレンダラーを設定します。  
  
 カスタム メニュー項目のレンダリングを表示するには、選択、<xref:System.Windows.Forms.MenuStrip>オプションを<xref:System.Windows.Forms.ComboBox>コントロールをクリックします**適用**を開き、**ファイル**メニュー項目。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 アプリケーションのすべての <xref:System.Windows.Forms.ToolStrip> コントロールにカスタム レンダラーを適用するよう <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> プロパティを設定します。  
  
 カスタム レンダラーを各 <xref:System.Windows.Forms.ToolStrip> コントロールに適用するよう <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> プロパティを設定します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# の構築方法の詳細については、次を参照してください。 [、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)します。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
