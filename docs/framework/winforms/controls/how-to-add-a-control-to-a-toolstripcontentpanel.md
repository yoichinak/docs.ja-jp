---
title: '方法: ToolStripContentPanel にコントロールを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripContentPanel [Windows Forms], adding controls
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
ms.openlocfilehash: d228300e00a5c2be9cf530cd921865a01accab05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011217"
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
  
 Visual Basic または Visual C# からこの例をビルドする方法については、[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)、または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStripContentPanel>
- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStripContainer コントロール](toolstripcontainer-control.md)
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
