---
title: '方法: ドッキングされた ToolStrip コントロールの Z オーダーを定義する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: 3347722383b7388c00335683537e00851e642bb6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129169"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a>方法: ドッキングされた ToolStrip コントロールの Z オーダーを定義する
ドッキングを使用して <xref:System.Windows.Forms.ToolStrip> コントロールを正しく配置するには、フォームの z オーダーでコントロールを正しく配置する必要があります。  
  
## <a name="example"></a>例  
 次のコード例は、z オーダーを指定することで、<xref:System.Windows.Forms.ToolStrip> コントロールと、ドッキングされた <xref:System.Windows.Forms.MenuStrip> コントロールを調整する方法を示しています。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 Z オーダーは、<xref:System.Windows.Forms.ToolStrip> と <xref:System.Windows.Forms.MenuStrip> の順序によって決まります。  
  
 コントロールはフォームの <xref:System.Windows.Forms.Control.Controls%2A> コレクションに追加されます。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> メソッドへのこれらの呼び出しの順序を反転し、レイアウトへの影響を示します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 この例をコマンドラインから Visual Basic または Visual C# にビルドする方法の詳細については、[コマンドラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
