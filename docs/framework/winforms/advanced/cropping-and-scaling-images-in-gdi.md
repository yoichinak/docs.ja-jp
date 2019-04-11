---
title: GDI+ でのイメージのトリミングおよびスケーリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: c3cdb06e99770808461f9266fb5f07df9074149b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183730"
---
# <a name="cropping-and-scaling-images-in-gdi"></a>GDI+ でのイメージのトリミングおよびスケーリング
使用することができます、<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>を描画して、ベクター イメージとラスター イメージを配置するクラス。 <xref:System.Drawing.Graphics.DrawImage%2A> 引数を指定することがいくつかの方法があるため、オーバー ロードされたメソッドであります。  
  
## <a name="drawimage-variations"></a>DrawImage バリエーション  
 1 つのバリエーション、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドは受信、<xref:System.Drawing.Bitmap>と<xref:System.Drawing.Rectangle>します。 四角形を描画操作の出力先を指定しますつまり、イメージを描画する四角形を指定します。 先の四角形のサイズが元のイメージのサイズと異なる場合は、イメージは、移行先の四角形に合わせてスケーリングします。 次のコード例は、3 回、同じイメージを描画する方法を示しています。 スケーリングなしで 1 回、拡張、および圧縮が 1 回。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 次の図は、3 つの画像を示します。  
  
 ![スケーリング](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 いくつかのバリエーション、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドは、先の四角形のパラメーターと同様に、元の四角形のパラメーターがあります。 描画するために、元のイメージの元の四角形のパラメーターを指定します。 先の四角形には、イメージの部分を描画する四角形を指定します。 先の四角形のサイズが元の四角形のサイズと異なる場合は、画像は先の四角形に合わせてスケーリングします。  
  
 次のコード例を作成する方法を示しています、 <xref:System.Drawing.Bitmap> Runner.jpg ファイルから。 イメージ全体がなしでのスケーリングで描画された (0, 0)。 イメージの一部が 2 回描画し、: 圧縮で 1 回、1 回で、拡張します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 次の図は、スケールなしのイメージとイメージの圧縮と展開された部分を示します。  
  
 ![トリミングおよびスケーリング](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、およびメタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
