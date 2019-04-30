---
title: グラデーション ブラシを使用した図形の塗りつぶし
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 5771aaabd283d71f5fa6934f86a1c24a57f38dca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954467"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>グラデーション ブラシを使用した図形の塗りつぶし
グラデーション ブラシを使用して、徐々 に変化する色で図形を塗りつぶすことができます。 たとえば、図形を塗りつぶす色、形状の左端から右端に移動する段階的に変化するように、水平方向のグラデーションを使用できます。 左端で黒の四角形を想像してみてください (0, 0, 0 は、赤、緑、および青のコンポーネントによって表される) と、右端が red (255, 0, 0 で表されます)。 四角形が 256 ピクセルである場合は、1 つの左側にピクセルの赤の要素より大きいを特定のピクセルの赤の要素になります。 行の左端のピクセルが (0, 0, 0) の色要素、2 番目のピクセルが (1, 0, 0)、3 番目のピクセルは、(2, 0, 0) というように、(255, 0, 0) の色要素の右端のピクセルが表示されるまでです。 これらの色の補間値は、色のグラデーションを構成します。  
  
 線形グラデーションは、水平、垂直方向に移動するか、指定した斜線を並列に色を変更します。 パス グラデーションは、内部およびパスの境界を移動するように色を変更します。 さまざまな効果を実現するためにパス グラデーションをカスタマイズすることができます。  
  
 次の図は、線状グラデーション ブラシで塗りつぶした四角形とパスのグラデーション ブラシで塗りつぶした楕円を示します。  
  
 ![Gradient](./media/gradient2.png "gradient2")  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 線形グラデーションを作成します。](how-to-create-a-linear-gradient.md)  
 線形グラデーションを使用して、作成する方法を示しています、<xref:System.Drawing.Drawing2D.LinearGradientBrush>クラス。  
  
 [方法: パス グラデーションを作成します。](how-to-create-a-path-gradient.md)  
 パス グラデーションを使用して、作成する方法について説明します、<xref:System.Drawing.Drawing2D.PathGradientBrush>クラス。  
  
 [方法: グラデーションに対してガンマ補正を適用します。](how-to-apply-gamma-correction-to-a-gradient.md)  
 グラデーション ブラシでガンマ補正を使用する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 このクラスの説明を表すし、そのすべてのメンバーへのリンクがあります。  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 このクラスの説明を表すし、そのすべてのメンバーへのリンクがあります。
