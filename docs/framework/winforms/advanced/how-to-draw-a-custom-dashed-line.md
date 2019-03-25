---
title: '方法: カスタム破線を描画します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 06555309b8432397e754bc9dfa717c89b052343f
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410226"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>方法: カスタム破線を描画します。
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 記載されているいくつかの破線スタイルを提供します、<xref:System.Drawing.Drawing2D.DashStyle>列挙体。 これらの標準の破線スタイルがニーズに合わないしない場合は、カスタムの破線パターンを作成できます。  
  
## <a name="example"></a>例  
 カスタム破線を描画するために、配列にダッシュと空白の長さを格納し、配列の値として割り当てます、<xref:System.Drawing.Pen.DashPattern%2A>のプロパティを<xref:System.Drawing.Pen>オブジェクト。 次の例では、配列に基づくカスタム破線を描画する`{5, 2, 15, 4}`します。 取得する場合は 5 のペンの幅によって、配列の要素を乗算する`{25, 10, 75, 20}`します。 長さ 25 75 の間で交互に表示されるダッシュと長さが 10 と 20 の間で交互に、スペースです。  
  
 次の図は、結果として得られる、破線を示します。 最終的なダッシュ ボードがで行を終了するようにに 25 よりも短くする必要があるに注意してください (405, 5)。  
  
 ![破線を示す図。](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 Windows フォームを作成し、フォームの処理<xref:System.Windows.Forms.Control.Paint>イベント。 上記のコードを貼り付け、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目
- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
