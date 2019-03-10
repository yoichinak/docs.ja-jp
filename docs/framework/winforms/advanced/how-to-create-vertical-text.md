---
title: '方法: 垂直方向のテキストを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: b2c26ab220fc9b796c8f8ababdef144847d52698
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710408"
---
# <a name="how-to-create-vertical-text"></a>方法: 垂直方向のテキストを作成します。
使用することができます、<xref:System.Drawing.StringFormat>水平方向にではなく縦方向にテキストを描画することを指定するオブジェクト。  
  
## <a name="example"></a>例  
 次の例には、値が割り当てられます。<xref:System.Drawing.StringFormatFlags.DirectionVertical>を、<xref:System.Drawing.StringFormat.FormatFlags%2A>のプロパティを<xref:System.Drawing.StringFormat>オブジェクト。 ある<xref:System.Drawing.StringFormat>にオブジェクトが渡される、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラス。 値<xref:System.Drawing.StringFormatFlags.DirectionVertical>のメンバーである、<xref:System.Drawing.StringFormatFlags>列挙体。  
  
 次の図は、垂直方向のテキストを示します。  
  
 ![フォント テキスト](./media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e` 、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目
- [方法: GDI を使用してテキストを描画します。](how-to-draw-text-with-gdi.md)
