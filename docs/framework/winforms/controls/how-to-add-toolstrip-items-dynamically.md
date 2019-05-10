---
title: '方法: ToolStrip の項目を動的に追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 9426c7cb3251dbbd95727b78c57be7a0b71556e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624016"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a>方法: ToolStrip の項目を動的に追加する
メニューが開くときに <xref:System.Windows.Forms.ToolStrip> コントロールのメニュー項目コレクションを動的に設定できます。  
  
## <a name="example"></a>例  
 次のコード例は、<xref:System.Windows.Forms.ContextMenuStrip> コントロールに項目を動的に追加する方法を示しています。 この例は、フォーム上の 3 つの異なるコントロールに同じ <xref:System.Windows.Forms.ContextMenuStrip> を再利用する方法も示しています。  
  
 この例では、<xref:System.Windows.Forms.ToolStripDropDown.Opening> イベント ハンドラーがメニュー項目コレクションを設定します。 
  <xref:System.Windows.Forms.ToolStripDropDown.Opening> イベント ハンドラーは、<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> プロパティと <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> プロパティを調べて、ソース管理を示す <xref:System.Windows.Forms.ToolStripItem> を追加します。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual C# の構築方法の詳細については、[、コマンドラインからビルドする](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
