---
title: '方法: 線形グラデーションを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: b836659821b54698b675d48acd4e46466001d654
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937923"
---
# <a name="how-to-create-a-linear-gradient"></a>方法: 線形グラデーションを作成する
GDI + 水平、垂直方向、および対角線方向の線形グラデーションを提供します。 既定では、線形グラデーションの色を均一に変更します。 ただし、色が一様でない方法で変更されるように、線形グラデーションをカスタマイズできます。  

> [!NOTE]
> この記事の例では、コントロールから呼び出されるメソッド<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  

次の例では、線、楕円、および水平方向の線状グラデーション ブラシを四角形を塗りつぶします。  
  
<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>コンス トラクターが 4 つの引数を受け取ります。 2 つのポイントと 2 つの色。 (0, 10) は、最初のポイントは最初の色 (赤) に関連付けられていると、2 番目の点 (200, 10) が 2 番目の色 (青) に関連付けられています。 想像どおりから描画される直線 (0, 10) に (200, 10) が赤から青に徐々 に変化します。  
  
 点 (0, 10) と (200, 10) で 10 件が重要ではありません。 2 つのポイントが同じ 2 つ目の座標にあることが重要なは、それらを結ぶ線が水平方向。 楕円と四角形変更も徐々 に赤から青の水平方向の座標が 0 から 200 にようにできます。  
  
 次の図は、線、楕円、四角形を示します。 色のグラデーション繰り返される自体の水平方向座標が 200 を超えるとに注意してください。  
  
 ![線形グラデーション](./media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>水平方向の線形グラデーションを使用するには  
  
- 3 番目と 4 番目の引数として、それぞれ不透明な赤と不透明青を渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 色要素は前の例では 0 の水平座標から 200 の水平座標に移動すると直線的に変更します。 たとえば、最初の座標が 0 と 200 の中間点は、0 から 255 までの中間に位置が青要素があります。  
  
 GDI + を使用すると、調整、他のグラデーションの 1 つのエッジから色が異なります。 黒から次の表に従って赤に変更されるグラデーション ブラシを作成するとします。  
  
|水平方向の座標|RGB コンポーネント|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 水平座標が 0 から 200 の方法の 20% のみである場合に、赤のコンポーネントが半分の強さではことに注意してください。  
  
 次の例のセット、<xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType>に 3 つの相対強度を 3 つの相対位置に関連付けるプロパティ。 上の表のように 0.5 の相対強度は 0.2 の相対位置に関連付けられています。 コードでは、楕円と四角形をグラデーション ブラシを設定します。  
  
 次の図は、結果として得られる楕円と四角形を示します。  
  
 ![線形グラデーション](./media/cslineargradient2.png "cslineargradient2")  

### <a name="to-customize-linear-gradients"></a>線形グラデーションをカスタマイズするには  
  
- 3 番目と 4 番目の引数として、それぞれ不透明な黒と不透明な赤を渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 上記の例のグラデーションを水平にされています。つまり、色は、水平線のいずれかに移動すると、段階的に変更します。 垂直方向のグラデーションと対角線方向のグラデーションを定義することもできます。  
  
 次の例に、点 (0, 0) と (200, 100) を渡す、<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>コンス トラクター。 青色の色が関連付けられている (0, 0) と、緑色の色が関連付けられます (200, 100)。 (ペンの幅が 10)、行と楕円は、線状グラデーション ブラシで塗りつぶされます。  
  
 次の図は、線、楕円を示します。 楕円内色徐々 にに沿って移動すると行のメモが並列に渡される行には (0, 0) と (200, 100)。  
  
 ![線形グラデーション](./media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>対角線方向の線形グラデーションを作成するには  
  
- 3 番目と 4 番目の引数として、それぞれ不透明青と不透明な緑を渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>関連項目

- [グラデーション ブラシを使用した図形の塗りつぶし](using-a-gradient-brush-to-fill-shapes.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
