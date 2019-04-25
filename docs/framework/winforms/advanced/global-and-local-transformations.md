---
title: グローバル変換とローカル変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: e4ed103e781cc2e59d62c11f3233357c77b81cb9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213754"
---
# <a name="global-and-local-transformations"></a>グローバル変換とローカル変換
グローバル変換によって描画されるすべての項目に適用される変換とは、指定された<xref:System.Drawing.Graphics>オブジェクト。 これに対し、ローカルの変換は、描画する特定の項目に適用される変換です。  
  
## <a name="global-transformations"></a>グローバル変換  
 グローバル変換を作成するには、構築、<xref:System.Drawing.Graphics>オブジェクト、し、操作、<xref:System.Drawing.Graphics.Transform%2A>プロパティ。 <xref:System.Drawing.Graphics.Transform%2A>プロパティは、<xref:System.Drawing.Drawing2D.Matrix>オブジェクト、アフィン変換の任意のシーケンスを保持できるようにします。 格納されている、変換、<xref:System.Drawing.Graphics.Transform%2A>プロパティはワールド変換と呼ばれます。 <xref:System.Drawing.Graphics>クラスは、複合ワールド変換を構築するためのいくつかのメソッドを提供します。 <xref:System.Drawing.Graphics.MultiplyTransform%2A>、 <xref:System.Drawing.Graphics.RotateTransform%2A>、 <xref:System.Drawing.Graphics.ScaleTransform%2A>、および<xref:System.Drawing.Graphics.TranslateTransform%2A>します。 次の例では、2 回楕円を描きます。 ワールド変換と後に 1 回作成する前に 1 回です。 変換は、y 方向に 0.5 倍でスケーリングし、x 方向で 50 ユニットを変換し、30 度を回転します。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 次の図は、変換に関連する行列を示しています。  
  
 ![Transformations](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  前の例ではクライアント領域の左上隅にある座標系の原点の楕円を回転します。 これには、楕円の中心を回転する場合は、異なる結果が生成されます。  
  
## <a name="local-transformations"></a>ローカルの変換  
 描画する特定の項目にローカルの変換が適用されます。 など、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトには、<xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A>メソッドをそのパスのデータ ポイントを変換することができます。 次の例では、変換を使用して四角形と回転変換を使用したパスを描画します。 (詳しくは、ワールド変換がないことを想定しています)。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 ワールド変換と、さまざまな結果を実現するためにローカルの変換を組み合わせることができます。 たとえば、ワールド変換を使用して、座標系を修正して、ローカルの変換を使用して回転新しい座標システムで描画されるオブジェクトを拡大/縮小することができます。  
  
 クライアント領域の左端からの配信元の 200 ピクセルとクライアント領域の上端から 150 ピクセル座標システムを必要とします。 さらに、測定単位が、x 軸が右と上向きの y 軸を参照する、ピクセルにすることを想定しています。 既定の座標系は、水平軸の反転を実行する必要があるために、下向き、y 軸が。 次の図は、このようなリフレクションのマトリックスを示します。  
  
 ![Transformations](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 次に、右側に翻訳 200 単位と 150 の単位を実行する必要があると仮定します。  
  
 次の例では、確立のワールド変換を設定して上記で説明した座標系、<xref:System.Drawing.Graphics>オブジェクト。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 (前の例の末尾に配置)、次のコードは、新しい座標系の原点を注視の左下隅を含む 1 つの四角形で構成されるパスを作成します。 ローカル変換と変換をローカルに 1 回、1 回、四角形が塗りつぶされます。 ローカルの変換後に 30 度回転して、2 の倍数で水平方向のスケーリングで構成されます。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 次の図は、新しい座標系と 2 つの四角形を示します。  
  
 ![Transformations](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>関連項目

- [座標系と変換](coordinate-systems-and-transformations.md)
- [マネージド GDI+ での変換の使用](using-transformations-in-managed-gdi.md)
