---
title: GDI+ での描画サーフェイスの制限
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: d0508166f905b45789ce638b03d0747dd6fa904e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074964"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>GDI+ での描画サーフェイスの制限
クリッピングでは、描画を四角形または領域を制限します。 次の図、文字列「こんにちは」ハート形の領域にクリップされます。  
  
 ![制限付き描画面](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>領域でクリッピング  
 パスからリージョンを作成し、クリッピングを中抜きの文字列を使用できるように、パスは、文字列のアウトラインを含めることができます。 次の図は、一連の同心構造の省略記号のテキスト文字列の内部に切り取られます。  
  
 ![制限付き描画面](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 クリッピングを描画するには、作成、<xref:System.Drawing.Graphics>オブジェクト、設定、<xref:System.Drawing.Graphics.Clip%2A>プロパティをその描画メソッドを呼び出して同じ<xref:System.Drawing.Graphics>オブジェクト。  
  
 [!code-csharp[LinesCurvesAndShapes#91](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [領域の使用](using-regions.md)
