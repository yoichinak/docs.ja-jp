---
title: '方法: 四角形を描画するために、ペンを使用します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: a29cae5a360185b7fa5e70fc0181c0cfaac8fc09
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463190"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>方法: 四角形を描画するために、ペンを使用します。
四角形を描画するためにする必要があります、<xref:System.Drawing.Graphics>オブジェクトと<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトを提供、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、線、色や幅などの機能を格納します。  
  
## <a name="example"></a>例  
 次の例で、左上隅を四角形を描画します (10, 10)。 四角形は、100 の幅と高さを 50 があります。 渡される 2 番目の引数、<xref:System.Drawing.Pen.%23ctor%2A>コンス トラクターの場合、ペンの幅が 5 ピクセルであることを示します。  
  
 四角形が描画されるときに、四角形の境界のペンが中央に配置します。 四角形の辺が 5 ピクセルの描画には、ペンの幅が 5 であるため、その 1 ピクセルの描画など、さまざまには、境界の 2 ピクセルの描画し、2 つのピクセルの外側に描画します。 ペンの配置の詳細については、次を参照してください。[方法。ペンの幅と配置を設定](how-to-set-pen-width-and-alignment.md)します。  
  
 次の図は、結果として得られる四角形を示します。 位置四角形が描画される場合は、ペンの幅が 1 つのピクセルになっていた点線表示します。 四角形の左上隅を拡大表示では、シック黒い線はそれらの点線中心を示します。  
  
 ![黒と点線で描画された四角形を示すスクリーン ショット。](./media/how-to-use-a-pen-to-draw-rectangles/drawn-rectangle-black-lines-dotted-lines.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。  
  
## <a name="see-also"></a>関連項目
- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
