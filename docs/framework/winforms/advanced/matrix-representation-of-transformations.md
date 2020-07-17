---
title: 変換の行列表現
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
ms.openlocfilehash: 24da407de24a924a68466e4301cc3f4a74cb2e94
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044252"
---
# <a name="matrix-representation-of-transformations"></a>変換の行列表現
M × n マトリックスは、m 行と n 列に配置された一連の数値です。 次の図は、いくつかのマトリックスを示しています。  
  
 ![変換](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 個々の要素を追加することにより、同じサイズの2つのマトリックスを追加できます。 次の図は、マトリックスの加算の2つの例を示しています。  
  
 ![変換](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 M × n 行列は n × p 行列で乗算でき、結果は m × p 行列になります。 最初の行列の列数は、2番目の行列の行の数と同じである必要があります。 たとえば、4×2行列を2×3行列で乗算すると、4×3行列が生成されます。  
  
 平面内の点とマトリックスの行と列は、ベクターと考えることができます。 たとえば、(2, 5) は2つのコンポーネントを持つベクターで、(3, 7, 1) は3つのコンポーネントを持つベクターです。 2つのベクトルのドット積は、次のように定義されています。  
  
 (a, b) • (c, d) = ac + bd  
  
 (a, b, c) • (d, e, f) = ad + be + cf  
  
 たとえば、(2, 3) と (5, 4) のドット積は (2) (5) + (3) (4) = 22 です。 (2, 5, 1) と (4, 3, 1) のドット積は、(2) (4) + (5) (3) + (1) (1) = 24 です。 2つのベクトルのドット積は、別のベクトルではなく、数値であることに注意してください。 また、2つのベクトルのコンポーネント数が同じ場合にのみ、ドット積を計算することができます。  
  
 I、j) を i 行目と jth 列のマトリックス A のエントリにします。 たとえば、A (3, 2) は、第3行のマトリックス A と2番目の列のエントリです。 A、B、および C がマトリックスで、AB = C であるとします。C のエントリは次のように計算されます。  
  
 C (i, j) = (A の行 i) • (B の列 j)  
  
 次の図は、マトリックス乗算のいくつかの例を示しています。  
  
 ![変換](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 平面内のポイントが1×2行列であると考えられる場合は、2×2行列を乗算することによってその点を変換できます。 次の図は、点 (2, 1) に適用されるいくつかの変換を示しています。  
  
 ![変換](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 前の図に示されているすべての変換は、線形変換です。 平行移動などの特定の変換は線形的ではなく、2×2行列で乗算として表すことはできません。 たとえば、ポイント (2, 1) で開始し、90°回転し、x 方向に3単位を平行移動し、y 方向に4単位を平行移動するとします。 これを行うには、マトリックス乗算を使用し、その後にマトリックスを追加します。  
  
 ![変換](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 線形変換 (2 ×2行列による乗算) の後に平行移動 (1 ×2行列の追加) は、アフィン変換と呼ばれます。 1組の行列 (線形部用および平行移動用) にアフィン変換を格納する代わりに、3×3行列に変換全体を格納します。 この作業を行うには、プレーンのポイントをダミーの3番目の座標で1×3の行列に格納する必要があります。 通常の方法では、すべての3番目の座標を1に設定します。 たとえば、ポイント (2, 1) は、マトリックス [2 1 1] によって表されます。 次の図は、1つの3×3行列で乗算として表現されたアフィン変換 (90 °回転、x 方向の3単位、y 方向の4単位) を示しています。  
  
 ![変換](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 前の例では、点 (2, 1) がポイント (2, 6) にマップされています。 3×3マトリックスの3番目の列には、0、0、1の数値が含まれていることに注意してください。 これは、アフィン変換の3×3行列の場合に常に当てはまります。 重要な数値は、列1および2の6つの数値です。 マトリックスの左上の2×2部分は、変換の線形部分を表し、3番目の行の最初の2つのエントリは変換を表します。  
  
 ![変換](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 Gdi + では、 <xref:System.Drawing.Drawing2D.Matrix>オブジェクトにアフィン変換を格納できます。 アフィン変換を表す行列の3番目の列は常に (0, 0, 1) であるため、オブジェクトを<xref:System.Drawing.Drawing2D.Matrix>構築するときに、最初の2つの列のうち6つの数値のみを指定します。 ステートメント`Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)`は、前の図に示されているマトリックスを構築します。  
  
## <a name="composite-transformations"></a>複合変換  
 複合変換は、変換のシーケンスであり、その後にもう1つ続きます。 次の一覧にあるマトリックスと変換について考えてみましょう。  
  
|||  
|-|-|  
|マトリックス A|90°回転|  
|マトリックス B|X 方向に2の係数でスケールする|  
|マトリックス C|Y 方向に3単位を平行移動する|  
  
 マトリックス [2 1 1] で表される point (2, 1) を使用して開始し、A に乗算した場合、B、C のように、ポイント (2, 1) は、上記の順序で3つの変換を実行します。  
  
 [2 1 1]ABC = [-2 5 1]  
  
 複合変換の3つの部分を3つの独立した行列に格納するのではなく、A、B、および C を組み合わせて、複合変換全体を格納する1つの3×3行列を取得することができます。 ABC = D とします。次に、D を乗算したポイントは、A、B、C の順に乗算した結果を示します。  
  
 [2 1 1]D = [-2 5 1]  
  
 次の図は、A、B、C、D というマトリックスを示しています。  
  
 ![変換](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 複合変換の行列は、個々の変換行列を乗算することで形成できます。つまり、アフィン変換の任意のシーケンスを1つ<xref:System.Drawing.Drawing2D.Matrix>のオブジェクトに格納できます。  
  
> [!CAUTION]
> 複合変換の順序は重要です。 一般に、回転、スケーリング、および平行移動はスケールと同じではなく、回転してから平行移動します。 同様に、行列乗算の順序も重要です。 一般に、ABC は... と同じではありません。  
  
 クラス<xref:System.Drawing.Drawing2D.Matrix>には、 <xref:System.Drawing.Drawing2D.Matrix.Scale%2A> <xref:System.Drawing.Drawing2D.Matrix.Shear%2A> <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A> <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>複合変換<xref:System.Drawing.Drawing2D.Matrix.Translate%2A>を構築するためのメソッドがいくつか用意されています。、、 、、、およびです。<xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A> 次の例では、最初に30°を回転させてから y 方向の係数2でスケールし、x 方向に5つの単位を平行移動する複合変換の行列を作成します。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 次の図は、マトリックスを示しています。  
  
 ![変換](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>関連項目

- [座標系と変換](coordinate-systems-and-transformations.md)
- [マネージド GDI+ での変換の使用](using-transformations-in-managed-gdi.md)
