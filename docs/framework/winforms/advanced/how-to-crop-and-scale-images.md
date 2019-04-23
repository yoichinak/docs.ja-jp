---
title: '方法: イメージをトリミングおよびスケーリングする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: 4257431881565f9160f45795111d374cc680dedd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189906"
---
# <a name="how-to-crop-and-scale-images"></a>方法: イメージをトリミングおよびスケーリングする
<xref:System.Drawing.Graphics>クラスには、いくつか用意されて<xref:System.Drawing.Graphics.DrawImage%2A>イメージのトリミングおよびスケールに使用できる元とコピー先の四角形のパラメーターを持つうちいくつかの方法です。  
  
## <a name="example"></a>例  
 次の例では、構築、 <xref:System.Drawing.Image> Apple.gif ディスク ファイルからのオブジェクト。 コードでは、元のサイズでリンゴのイメージ全体を描画します。 コードを呼び出して、<xref:System.Drawing.Graphics.DrawImage%2A>のメソッドを<xref:System.Drawing.Graphics>が元の apple イメージよりも大きい先の四角形で apple のイメージの一部を描画するオブジェクト。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>メソッドは、5 番目と 6 番目の引数にこの 4 番目に、3 で指定されたソースの四角形を調べることで描画するために apple のどの部分を決定します。 この場合は、apple は、幅の 75% の高さの 75% をトリミングされます。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>トリミング apple を描画する場所とする先の四角形を調べることで、トリミングされた apple 大きさ、これは、メソッドが決定します 2 番目の引数で指定します。 この場合は、先の四角形は、30% の幅と高さのある、元のイメージよりも 30% です。  
  
 次の図は apple をトリミングし、スケーリング、元の apple 示します。  
  
 ![元のイメージと同じ画像をトリミングのスクリーン ショット。](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 置き換えてください`Apple.gif`イメージ ファイル名と、システムで有効なパス。  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
