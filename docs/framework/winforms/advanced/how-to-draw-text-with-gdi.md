---
title: '方法: GDI を使用してテキストを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 4577a3fa10b286514a2a7f5691991eab016b58a6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751716"
---
# <a name="how-to-draw-text-with-gdi"></a>方法: GDI を使用してテキストを描画する
<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドで、<xref:System.Windows.Forms.TextRenderer>アクセスできるクラス、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]フォームまたはコントロールにテキストを描画するための機能です。 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] テキストのレンダリング パフォーマンスが向上しより正確なテキストがよりを測定すると通常は[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A>のメソッド、<xref:System.Windows.Forms.TextRenderer>クラスが印刷はサポートされていません。 印刷するときは常に使用して、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラス。  
  
## <a name="example"></a>例  
 次のコード例に示しますを使用して、四角形内の複数の行のテキストを描画する方法、<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッド。  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 テキストを表示するために、<xref:System.Windows.Forms.TextRenderer>必要がある、クラス、<xref:System.Drawing.IDeviceContext>などを<xref:System.Drawing.Graphics>と<xref:System.Drawing.Font>テキストをおよび描画必要がある色を描画する場所。 必要に応じて、テキストを使用して書式設定を指定できます、<xref:System.Windows.Forms.TextFormatFlags>列挙体。  
  
 取得の詳細については、<xref:System.Drawing.Graphics>を参照してください[方法。描画の Graphics オブジェクトを作成](how-to-create-graphics-objects-for-drawing.md)です。 構築の詳細については、<xref:System.Drawing.Font>を参照してください[方法。フォント ファミリとフォント作成](how-to-construct-font-families-and-fonts.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記のコード例が、Windows フォームで使用するために設計されており、必要があります、 <xref:System.Windows.Forms.PaintEventArgs>`e`はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [フォントとテキストの使用](using-fonts-and-text.md)
