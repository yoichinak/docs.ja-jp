---
title: 変換順序が重要となる理由
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order significance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
ms.openlocfilehash: 08927ebaa460e19e558dce22f39c13c31f0e49d0
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504906"
---
# <a name="why-transformation-order-is-significant"></a>変換順序が重要となる理由
1 つ<xref:System.Drawing.Drawing2D.Matrix>オブジェクトは、1 つの変換または変換のシーケンスを格納できます。 後者を複合変換と呼びます。 複合変換の行列は、個々 の変換行列を掛け合わせることによって取得されます。  
  
## <a name="composite-transform-examples"></a>複合変換の例  
 複合変換の場合は、個々 の変換の順序が重要です。 たとえば、最初回転、拡大縮小、しする変換する場合、最初に平行移動、回転し、スケールよりも、異なる結果が取得します。 GDI + で複合変換が左から右に構築されます。 S、R、および T は、スケール、回転、および平行移動行列をそれぞれが場合、製品 SRT (順序) で複合変換の行列を最初にスケーリングが回転し、変換します。 製品によって生成されたマトリックス SRT は、製品 TRS によって生成されたマトリックスと異なります。  
  
 順序は重要な理由の 1 つは、座標系の原点を基準の回転とスケーリングのような変換が行われることです。 原点を中心とするオブジェクトをスケーリングすると、原点から離れているオブジェクトのスケールよりも異なる結果が生成されます。 同様に、原点を中心とするオブジェクトの回転には、配信元から離れているオブジェクトを回転するよりも異なる結果が生成されます。  
  
 次の例では、複合変換を拡大縮小、回転、および (順序) での翻訳を結合します。 引数<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に渡される、<xref:System.Drawing.Graphics.RotateTransform%2A>メソッドは、拡大縮小、回転を従うことを示します。 同様に、引数<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に渡される、<xref:System.Drawing.Graphics.TranslateTransform%2A>メソッドは、翻訳が回転を従うことを示します。 <xref:System.Drawing.Drawing2D.MatrixOrder.Append> <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>のメンバーである、<xref:System.Drawing.Drawing2D.MatrixOrder>列挙体。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 次の例では、前の例と同じメソッドの呼び出しが呼び出しの順序を反転します。 操作の結果として得られる順序は最初に平行移動、回転スケールで、最初のスケールよりも非常に異なる結果を生成し、回転し、変換します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 複合変換の個々 の変換の順序を反転する 1 つの方法は、メソッド呼び出しのシーケンスの順序を逆です。 操作の順序を制御する 2 番目の方法では、マトリックスの order 引数を変更します。 次の例は、点を除いて、前の例と同じ<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に変更されました<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>します。 SRT、S、R、および T がスケールのマトリックスの順序では、行列乗算を実行してください。、回転、およびそれぞれ変換します。 複合変換の順序は最初の小数点以下桁数、回転、変換します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 直前の例の結果は、このトピックの最初の例の結果と同じです。 これは、メソッドの呼び出しの順序と行列乗算の順序の両方元に戻すためにです。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Drawing2D.Matrix>
- [座標系と変換](coordinate-systems-and-transformations.md)
- [マネージド GDI+ での変換の使用](using-transformations-in-managed-gdi.md)
