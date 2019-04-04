---
title: '方法: ContextMenuStrip のチェックの余白とイメージの余白'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], configuring check and image margins
- ContextMenuStrips [Windows Forms], configuring check and image margins
- margins [Windows Forms], setting check and image in Windows Forms ContextMenuStrips
ms.assetid: 3391c4c2-0c9e-4aa4-9492-13ff7644bdf2
ms.openlocfilehash: 8527c8f2195c586ba7d9c61c5c2ea1fa26bf53f8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715219"
---
# <a name="how-to-configure-contextmenustrip-check-margins-and-image-margins"></a>方法: ContextMenuStrip のチェックの余白とイメージの余白
<xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> プロパティと <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> プロパティをさまざまな組み合わせで設定することにより、<xref:System.Windows.Forms.ContextMenuStrip> をカスタマイズできます。  
  
## <a name="example"></a>例  
 次のコード例では、<xref:System.Windows.Forms.ContextMenuStrip> のチェックの余白とイメージの余白をカスタマイズする方法について説明します。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
- [方法: ContextMenuStrip コントロールでチェックの余白とイメージを有効にします。](how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
