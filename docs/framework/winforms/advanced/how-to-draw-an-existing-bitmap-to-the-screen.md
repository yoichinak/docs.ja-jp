---
title: '方法: 既存のビットマップを画面に描画します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: d2e06aa382bc2b01a4308f99735ca533e7a9a3ea
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653822"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>方法: 既存のビットマップを画面に描画します。
既存のイメージは、画面に簡単に描画できます。 まずを作成する必要があります、<xref:System.Drawing.Bitmap>オブジェクトは、ファイル名を受け取り、ビットマップ コンス トラクターを使用して<xref:System.Drawing.Bitmap.%23ctor%28System.String%29>します。 このコンス トラクターは、BMP、GIF、JPEG、PNG、TIFF など、いくつかの異なるファイル形式を使用したイメージを受け入れます。 作成した後、<xref:System.Drawing.Bitmap>オブジェクトを渡す<xref:System.Drawing.Bitmap>オブジェクトを<xref:System.Drawing.Graphics.DrawImage%2A>のメソッドを<xref:System.Drawing.Graphics>オブジェクト。  
  
## <a name="example"></a>例  
 この例で作成、 <xref:System.Drawing.Bitmap> JPEG ファイルからオブジェクトとで、左上隅のビットマップが描画されます (60, 10)。  
  
 次の図は、指定した位置に描画されるビットマップを示しています。  
  
 ![指定した位置にあるイメージを示すスクリーン ショット。](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
