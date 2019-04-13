---
title: '方法: テクスチャを使用して塗りつぶした直線を描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: c0f90c298f48aeb96893bb09241faddc08d8a49d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186908"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>方法: テクスチャを使用して塗りつぶした直線を描画する
純色で直線を描画するには、代わりに、テクスチャを使用して線を描画できます。 直線とテクスチャを使用して曲線を描画するには、作成、<xref:System.Drawing.TextureBrush>オブジェクト、および渡す<xref:System.Drawing.TextureBrush>オブジェクトを<xref:System.Drawing.Pen.%23ctor%2A>コンス トラクター。 テクスチャ ブラシに関連付けられたビットマップは、平面のタイルを (表示) を使用し、ペンのストロークが特定のピクセルのタイルのテクスチャを得るため、ペンでは、直線または曲線を描画、ときにします。  
  
## <a name="example"></a>例  
 次の例では、作成、<xref:System.Drawing.Bitmap>ファイルからオブジェクト`Texture1.jpg`します。 そのビットマップが構築に使用される、<xref:System.Drawing.TextureBrush>オブジェクト、および<xref:System.Drawing.TextureBrush>オブジェクトが構築するために使用、<xref:System.Drawing.Pen>オブジェクト。 呼び出し<xref:System.Drawing.Graphics.DrawImage%2A>でその左上隅のビットマップを描画します (0, 0)。 呼び出し<xref:System.Drawing.Graphics.DrawEllipse%2A>を使用して、<xref:System.Drawing.Pen>テクスチャ楕円を描画するオブジェクト。  
  
 次の図は、ビットマップ、テクスチャの楕円を示します。  
  
 ![ビットマップ、およびテクスチャの楕円を示すスクリーン ショット。](./media/how-to-draw-a-line-filled-with-a-texture/bitmap-textured-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingAPen#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 Windows フォームを作成し、フォームの処理<xref:System.Windows.Forms.Control.Paint>イベント。 上記のコードを貼り付け、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。 置換`Texture.jpg`イメージ システム上で有効にします。  
  
## <a name="see-also"></a>関連項目

- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
