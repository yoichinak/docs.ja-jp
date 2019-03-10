---
title: '方法: イメージの色を変換します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 81aecddb28903649ff2d59e80fc90368df5e2db4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703024"
---
# <a name="how-to-translate-image-colors"></a>方法: イメージの色を変換します。
翻訳は、4 つの色コンポーネントの 1 つ以上の値を追加します。 翻訳を表すカラー マトリックス エントリは、次の表に付与されます。  
  
|コンポーネントを変換します。|マトリックスのエントリ|  
|--------------------------------|------------------|  
|赤|[4][0]|  
|緑|[4][1]|  
|青|[4][2]|  
|[アルファ]|[4][3]|  
  
## <a name="example"></a>例  
 次の例では、構築、 <xref:System.Drawing.Image> ColorBars.bmp ファイルからのオブジェクト。 コードでは、イメージ内の各ピクセルの赤の要素を 0.75 を追加します。 変換後のイメージと共に、元のイメージが描画されます。  
  
 次の図は、右側の左側に、元のイメージと変換後のイメージを示します。  
  
 ![色を変換](./media/colortrans2.png "colortrans2")  
  
 次の表は、赤の平行移動の前後に 4 つのバーの色のベクターを示します。 色コンポーネントの最大値が 1 であるため、2 行目に赤のコンポーネントが変更されないことに注意してください。 (同様に、色コンポーネントの最小値は 0 です。)  
  
|元|翻訳先|  
|--------------|----------------|  
|黒 (0、0, 0, 1)|(0.75, 0, 0, 1)|  
|赤 (1, 0、0, 1)|(1, 0, 0, 1)|  
|緑 (0, 1、0, 1)|(0.75, 1, 0, 1)|  
|青 (0, 0、1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。 置換`ColorBars.bmp`イメージ ファイル名と、システムで有効なパス。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [イメージの色の変更](recoloring-images.md)
