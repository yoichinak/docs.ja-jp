---
title: 変換を使用した色のスケーリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9c8f2392137d04f56096120cec64b60c42c47419
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107986"
---
# <a name="using-transformations-to-scale-colors"></a>変換を使用した色のスケーリング
1 つ以上の数が 4 つの色コンポーネントのスケーリング変換を乗算します。 次の表に、スケーリングを表すカラー行列のエントリが与えられます。  
  
|スケールのコンポーネント|マトリックスのエントリ|  
|----------------------------|------------------|  
|赤|[0][0]|  
|緑|[1][1]|  
|青|[2][2]|  
|[アルファ]|[3][3]|  
  
## <a name="scaling-one-color"></a>1 つの色のスケーリング  
 次の例では、構築、 <xref:System.Drawing.Image> ColorBars2.bmp ファイルからのオブジェクト。 コードは、2 の倍数でイメージ内の各ピクセルの青のコンポーネントをスケーリングします。 変換後のイメージと共に、元のイメージが描画されます。  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 次の図は、右側の左側に、元のイメージおよびスケーリングされたイメージを示します。  
  
 ![元とスケールの色を比較するスクリーン ショット。](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 次の表は、青のスケーリング前に、と後に、4 つのバーの色のベクターを示します。 4 つ目のカラー バーに青のコンポーネント 0.8 から 0.6 をしたことに注意してください。 だ[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]結果の小数部の一部のみが保持されます。 たとえば、(2)(0.8) = 1.6、1.6 の小数部は 0.6 です。 小数部分のみを保持により、結果が、常には [0, 1] 間隔。  
  
|元|スケール|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>複数の色のスケーリング  
 次の例では、構築、 <xref:System.Drawing.Image> ColorBars2.bmp ファイルからのオブジェクト。 コードは、イメージ内の各ピクセルの赤、緑、および青のコンポーネントをスケーリングします。 赤のコンポーネントが 25% に縮小、緑のコンポーネントが 35%、拡大/縮小されます、および青のコンポーネントは 50% に縮小します。  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 次の図は、右側の左側に、元のイメージおよびスケーリングされたイメージを示します。  
  
 ![元とスケールの色を比較するスクリーン ショット。](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 次の表は、赤、緑、青のスケーリング前に、と後に、4 つのバーの色のベクターを示します。  
  
|元|スケール|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [イメージの色の変更](recoloring-images.md)
