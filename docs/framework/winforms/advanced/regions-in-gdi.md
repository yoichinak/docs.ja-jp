---
title: GDI+ での領域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: 31c0e4b1509c478786d075b127f0b181d5cdd1c6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724974"
---
# <a name="regions-in-gdi"></a>GDI+ での領域
リージョンは、出力デバイスの表示領域の一部を示します。 リージョンは、単純な (1 つの四角形) または複合 (多角形と閉じた曲線の組み合わせ) を指定できます。 次の図は、2 つのリージョン: 四角形から構築された 1 つと、パスから構築されました。  
  
 ![リージョン](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>領域の使用  
 リージョンは、クリッピングは多くの場合、使用され、ヒット テストします。 クリッピングでは、更新する必要がある部分は、通常、表示領域の特定の領域に描画を制限します。 ヒット テストには、マウス ボタンが押されたときにカーソルが、画面の特定のリージョン内かどうかを判断する必要があります。  
  
 四角形またはパスからリージョンを構築できます。 既存のリージョンを組み合わせることで、複雑な領域を作成することもできます。 <xref:System.Drawing.Region>クラスは領域を結合するために、次のメソッドを提供します。 <xref:System.Drawing.Region.Intersect%2A>、 <xref:System.Drawing.Region.Union%2A>、 <xref:System.Drawing.Region.Xor%2A>、 <xref:System.Drawing.Region.Exclude%2A>、および<xref:System.Drawing.Region.Complement%2A>します。  
  
 2 つのリージョンの積集合は、両方のリージョンに属しているすべての点のセットです。 共用体は、1 つまたはもう一方または両方のリージョンに属しているすべての点のセットです。 領域の補数は、一連のリージョンにないすべてのポイントです。 次の図は、前の図に示すように 2 つのリージョンの和集合、積集合を示します。  
  
 ![リージョン](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A>のリージョンのペアに適用される、メソッドが 1 つのリージョンまたは両方ではなく、その他に属しているすべてのポイントを格納する領域を生成します。 <xref:System.Drawing.Region.Exclude%2A>のリージョンのペアに適用される、メソッドが 2 番目のリージョンにない最初のリージョン内のすべてのポイントが含まれる領域が生成されます。 次の図は、適用することに起因するリージョン、<xref:System.Drawing.Region.Xor%2A>と<xref:System.Drawing.Region.Exclude%2A>メソッドをこのトピックの冒頭で示した 2 つのリージョン。  
  
 ![リージョン](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 領域の塗りつぶしにする必要があります、<xref:System.Drawing.Graphics>オブジェクト、<xref:System.Drawing.Brush>オブジェクト、および<xref:System.Drawing.Region>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトを提供、<xref:System.Drawing.Graphics.FillRegion%2A>メソッド、および<xref:System.Drawing.Brush>オブジェクトは、塗りつぶしの色またはパターンなどの属性を格納します。 次の例では、純色で領域を塗りつぶします。  
  
 [!code-csharp[LinesCurvesAndShapes#61](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [領域の使用](using-regions.md)
