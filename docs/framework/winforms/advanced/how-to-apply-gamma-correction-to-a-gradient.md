---
title: '方法: グラデーションに対してガンマ補正を適用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: e812e441233c1d29a67dac639048e20a659549f0
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809492"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>方法: グラデーションに対してガンマ補正を適用する
線状グラデーション ブラシのガンマ補正を有効にするには、ブラシのできます<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>プロパティを`true`します。 ガンマ補正を無効に設定してできます、<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>プロパティを`false`します。 既定では、ガンマ補正が無効です。  
  
## <a name="example"></a>例  

次の例は、コントロールから呼び出されるメソッド<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。 例では、線状グラデーション ブラシを作成し、そのブラシを使用して 2 つの四角形を塗りつぶします。 最初の四角形はガンマ補正を適用せず、ガンマ補正と 2 番目の四角形が入力されます。  
  
 次の図では、2 つの塗りつぶされた四角形を示します。 ガンマ補正が、上部の四角形は、中央の濃いが表示されます。 統一された複数の強度がガンマ補正は、下の四角形が表示されます。  
  
 ![2 つのグラデーションで塗りつぶされた四角形とガンマ補正なし。](./media/how-to-apply-gamma-correction-to-a-gradient/two-rectangles-gamma-gradient.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [グラデーション ブラシを使用した図形の塗りつぶし](using-a-gradient-brush-to-fill-shapes.md)
