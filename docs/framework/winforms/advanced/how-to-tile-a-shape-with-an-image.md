---
title: '方法: イメージを並べたパターンによって図形を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: ad7b8737a63028e533cadfa6db56b063eb943f22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954927"
---
# <a name="how-to-tile-a-shape-with-an-image"></a>方法: イメージを並べたパターンによって図形を塗りつぶす
フロアをカバーする他の横にあるタイルを配置すると同様、(タイル) 図形の塗りつぶし、四角形のイメージを互いの横にある配置できます。 形状の内部を並べて表示するには、テクスチャ ブラシを使用します。 構築する際に、<xref:System.Drawing.TextureBrush>オブジェクトのコンス トラクターに渡す引数の 1 つは、<xref:System.Drawing.Image>オブジェクト。 テクスチャ ブラシを使用して、図形の内部を描画するときにこのイメージのコピーを繰り返し、図形が入力されます。  
  
 ラップ モード プロパティ、<xref:System.Drawing.TextureBrush>方法、画像には、四角形グリッドでこれが繰り返されるオブジェクトを決定します。 行うことができます、グリッド内のタイルがすべて同じ方向、または反転させる 1 つのグリッド位置から、次に、イメージを行うことができます。 反転は、水平、垂直、またはその両方です。 次の例では、さまざまな種類の反転を並べて表示します。  
  
### <a name="to-tile-an-image"></a>イメージを並べて表示  
  
- この例では、次の 75 × 75 イメージを使用して、200 × 200 四角形を並べて表示します。  
  
 ![タイル 1](./media/tile1.gif "tile1")  
  
- 次の図は、四角形がイメージに並べて表示する方法を示します。 すべてのタイルが同じ方向; があることに注意してください。反転はありません。  
  
 ![タイル 2](./media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>水平方向に並べて表示するときにイメージを反転するには  
  
- この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形を入力します。 ラップ モードは、イメージを水平方向に反転に設定されます。 次の図は、四角形がイメージに並べて表示する方法を示します。 次の特定の行に 1 つのタイルから移動すると、イメージ水平方向に反転に注意してください。  
  
 ![タイル 3 の](./media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>垂直方向に並べて表示するときにイメージを反転するには  
  
- この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形を入力します。 ラップ モードは、イメージを垂直方向に反転に設定されます。  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>並べて表示するとき、イメージを水平および垂直方向に反転するには  
  
- この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形を並べて表示します。 ラップ モードは、イメージを水平および垂直方向に反転に設定されます。 次の図は、四角形がイメージと、並べて表示する方法を示します。 次の特定の行に 1 つのタイルから移動する、イメージは水平方向に反転させる、イメージが垂直方向に反転させるように、特定の列に 1 つのタイルから移動するに注意してください。  
  
 ![5 をタイル](./media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>関連項目

- [ブラシを使用した図形の塗りつぶし](using-a-brush-to-fill-shapes.md)
