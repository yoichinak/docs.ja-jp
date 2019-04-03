---
title: '方法: イメージを回転、反転、および傾斜させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: dda03c9c1e1390ca6a5250471f047d3747e989e2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839913"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>方法: イメージを回転、反転、および傾斜させる
回転、反転、および元のイメージの左上隅や右、左下角の終点を指定することで、イメージを傾けることができます。 次の 3 つの終点では、平行四辺形に元の四角形のイメージをマップするアフィン変換を決定します。  
  
## <a name="example"></a>例  
 たとえば、元のイメージ左上隅を四角形は、(0, 0)、右上隅 (100, 0) と左下隅にある (0, 50)。 3 つの点を次のように終点にマップするものとします。  
  
|元のポイント|終点|  
|--------------------|-----------------------|  
|左 (0, 0)|(200, 20)|  
|右 (100, 0)|(110, 100)|  
|左 (0, 50)|(250, 30)|  
  
 次の図は、元のイメージと平行四辺形にマップされているイメージを示します。 元のイメージがされて傾斜した、反映、回転、および翻訳されました。 元のイメージの上端に沿って、x 軸を実行している行にマップされます (200, 20) と (110, 100)。 元のイメージの左の端に沿って、y 軸を実行している行にマップされます (200, 20) と (250, 30)。  
  
 ![元のイメージと平行四辺形にマップされているイメージ。](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-illustration.gif)  
  
 次の図は、写真のイメージに適用するような変換を示しています。  
  
 ![クライマと平行四辺形にマップされている画像の画像。](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-photo.png)  
  
 次の図は、メタファイルに適用するような変換を示しています。  
  
 ![図形とテキストを平行四辺形にマップされている図。](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-metafile.png)  
  
 次の例では、最初の図に示すようにイメージを生成します。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。 置き換えてください`Stripes.bmp`システム上で有効であるイメージへのパス。  
  
## <a name="see-also"></a>関連項目
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
