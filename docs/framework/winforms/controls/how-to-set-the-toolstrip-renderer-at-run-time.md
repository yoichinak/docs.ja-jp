---
title: '方法: 実行時に ToolStrip レンダラーを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripManager class [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 525e2347-0804-49aa-b9a3-9b2cabbf1c35
ms.openlocfilehash: f0e8668ef46de8cc073663786bcd43b740a1b2f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013063"
---
# <a name="how-to-set-the-toolstrip-renderer-at-run-time"></a>方法: 実行時に ToolStrip レンダラーを設定する
カスタムの `ProfessionalColorTable` クラスを作成することで、<xref:System.Windows.Forms.ToolStrip> コントロールの外観をカスタマイズできます。  
  
## <a name="example"></a>例  
 次のコード例は、カスタムの `ProfessionalColorTable` クラスを作成する方法を示しています このクラスは、<xref:System.Windows.Forms.MenuStrip> コントロールと <xref:System.Windows.Forms.ToolStrip> コントロールのグラデーションを定義します。  
  
 このコード例を使用するには、アプリケーションをコンパイルして実行し、**[色を変更]** をクリックして、カスタムの `ProfessionalColorTable` クラスで定義されているグラデーションを適用します。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="defining-a-custom-professionalcolortable-class"></a>カスタム ProfessionalColorTable クラスを定義する  
 カスタムのグラデーションは、`CustomProfessionalColors` クラスでで定義されます。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#30)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#30)]  
  
## <a name="assigning-a-custom-renderer"></a>カスタム レンダラーの割り当て  
 `CustomProfessionalColors` クラスを使用して `ToolStripProfessionalRenderer` を新規作成し、<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> プロパティに割り当てます。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#22)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#22)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 Visual Basic または Visual C# からこの例をビルドする方法については、[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)、または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.ProfessionalColorTable>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
