---
title: '方法: 色の回転'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: d3fa49e6129c93df93378fb2b607a87a5a0be087
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125890"
---
# <a name="how-to-rotate-colors"></a>方法: 色の回転
4 次元色空間で回転は、視覚化が困難です。 できることができます簡単に固定色コンポーネントの 1 つを保持することに同意する回転を視覚化できます。 そうですね、アルファ コンポーネントに 1 に固定の (完全に不透明) を保持するとします。 次の図に示すように赤、緑、および青の軸を持つ 3 次元のカラー スペースを視覚化できます。  
  
 ![赤、緑、および青の軸の回転を示す図。](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 色は、3-D 空間内の点として考えることができます。 たとえば、領域で、ポイント (1, 0, 0) は赤の色を表し領域で、ポイント (0, 1, 0) は、緑の色を表します。  
  
 次の図は、(1, 0, 0) の色を回転する意味を示します、赤、緑のプレーンで 60 度の角度までです。 赤、緑の平面に平行な平面の回転は、青の軸の周りの回転として考えることができます。  
  
 ![青の軸の周りの回転を示す図。](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 次の図は、3 つの座標軸 (赤、緑、青) のそれぞれについての回転を実行するカラー行列を初期化する方法を示します。  
  
 ![3 つの軸を中心として回転を実行するカラー行列を初期化します。](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>例  
 次の例は、イメージを 1 つのすべての色 (1, 0, 0.6) は、青の軸の周りで 60 度回転を適用します。 回転の角度は赤、緑の平面に平行な平面でをスイープします。  
  
 次の図は、左側と右側の色の回転後のイメージで、元のイメージを示しています。  
  
 ![元のイメージとイメージの色の回転を示す図。](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 次の図は、色の回転を次のコード実行の視覚化を示しています。
  
 ![色の回転の視覚エフェクトを示す図。](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。 置換`RotationInput.bmp`イメージ ファイル名とパス、システムでは無効です。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [イメージの色の変更](recoloring-images.md)
