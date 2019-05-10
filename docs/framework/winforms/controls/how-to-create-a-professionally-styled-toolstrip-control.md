---
title: '方法: プロフェッショナル スタイルの ToolStrip コントロールを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 6ba5d948b99889e26f620363b7fefbe2e63ffd2d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616008"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>方法: プロフェッショナル スタイルの ToolStrip コントロールを作成する
<xref:System.Windows.Forms.ToolStripProfessionalRenderer> 型から派生する独自のクラスを記述することで、アプリケーションの <xref:System.Windows.Forms.ToolStrip> コントロールにプロフェッショナルな外観と動作 (操作性) を与えることができます。  
  
 Visual Studio でこの機能の広範なサポートがあります。  
  
 「[チュートリアル:プロフェッショナル スタイルの ToolStrip コントロールの作成](walkthrough-creating-a-professionally-styled-toolstrip-control.md)です。  
  
## <a name="example"></a>例  
 次のコード例は、使用する方法を示します<xref:System.Windows.Forms.ToolStrip>似た複合コントロールを作成するコントロール、**ナビゲーション ウィンドウ**Microsoft® Outlook® で提供されます。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual C# の構築方法の詳細については、[、コマンドラインからビルドする](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  [チュートリアル: プロフェッショナル スタイルの ToolStrip コントロールの作成](walkthrough-creating-a-professionally-styled-toolstrip-control.md)です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
- [方法: フォームに標準メニュー項目を提供します。](how-to-provide-standard-menu-items-to-a-form.md)
