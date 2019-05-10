---
title: '方法: ToolStripContentPanel にコントロールを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripContentPanel [Windows Forms], adding controls
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
ms.openlocfilehash: 4fbc97502431b681a77d58a112344287f582ff0f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624140"
---
# <a name="how-to-add-a-control-to-a-toolstripcontentpanel"></a>方法: ToolStripContentPanel にコントロールを追加する
<xref:System.Windows.Forms.ToolStripContentPanel> に対して、1 つまたは複数のコントロールをプログラムで追加できます。  
  
## <a name="example"></a>例  
 次のコード例は、<xref:System.Windows.Forms.RichTextBox> を <xref:System.Windows.Forms.ToolStripContentPanel> に追加する方法を示しています。  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
- System、System.Data、および System.Windows.Forms の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual C# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStripContentPanel>
- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStripContainer コントロール](toolstripcontainer-control.md)
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
