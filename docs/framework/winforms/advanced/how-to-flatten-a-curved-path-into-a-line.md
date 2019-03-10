---
title: '方法: 行に曲線のパスをフラット化します。'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: d4847124c7af2e0b35d6874f53b85be4891b22df
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711045"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>方法: 行に曲線のパスをフラット化します。
A<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトは、一連の行とベジエ スプラインを格納します。 パスに曲線 (省略記号、円弧、カーディナル スプライン) のいくつかの種類を追加できますが、パスに格納する前に、各曲線がベジエ スプラインに変換されます。 パスをフラット化は、パス内の各本のベジエ スプラインを一連の直線に変換するので構成されます。 次の図は前に、とフラット化した後にパスを示します。  
  
 ![直線と曲線](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>パスをフラット化するには  
  
-   呼び出す、<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>のメソッドを<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。 <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>メソッドは、フラット化されたパスと元のパスの最大距離を指定する平坦度引数を受け取ります。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [パスの作成および描画](constructing-and-drawing-paths.md)
