---
title: '方法: 結合線'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: a43cfb8a51435aa0c5c3f7aae673d38d3f7792ab
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410876"
---
# <a name="how-to-join-lines"></a>方法: 結合線
直線の接合部は、2 つの行の端を満たすまたはオーバー ラップによって構成される一般的な領域です。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 次の 3 つの行の結合スタイルを提供します。 マイタ、傾斜、およびラウンドします。 直線の接合スタイルのプロパティである、<xref:System.Drawing.Pen>クラス。 直線の接合スタイルを指定すると、<xref:System.Drawing.Pen>オブジェクトのいずれかで接続されているすべての行を結合スタイルが適用されること<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトがそのペンを使用して描画します。  
  
 次の図は、直線のベベル結合の結果を示します。  
  
 ![結合線を示す図。](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a>例  
 使用して直線の接合スタイルを指定することができます、<xref:System.Drawing.Pen.LineJoin%2A>のプロパティ、<xref:System.Drawing.Pen>クラス。 この例では、水平線と垂直線の間の直線の面取り結合を示します。 次のコードでは、値で<xref:System.Drawing.Drawing2D.LineJoin.Bevel>に割り当てられている、<xref:System.Drawing.Pen.LineJoin%2A>プロパティのメンバーである、<xref:System.Drawing.Drawing2D.LineJoin>列挙体。 他のメンバー、<xref:System.Drawing.Drawing2D.LineJoin>列挙体は<xref:System.Drawing.Drawing2D.LineJoin.Miter>と<xref:System.Drawing.Drawing2D.LineJoin.Round>します。  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目
- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
