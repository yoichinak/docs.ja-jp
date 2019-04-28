---
title: '方法: メタファイルを読み込んで表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 39b7251b2789c7410e1d59b4aa7990a2f73055fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723219"
---
# <a name="how-to-load-and-display-metafiles"></a>方法: メタファイルを読み込んで表示する
<xref:System.Drawing.Imaging.Metafile>から継承されるクラス、<xref:System.Drawing.Image>クラス、メソッドの記録、表示、およびベクター イメージの検証を提供します。  
  
## <a name="example"></a>例  
 ベクター イメージ (メタファイル) を画面に表示する必要があります、<xref:System.Drawing.Imaging.Metafile>オブジェクトと<xref:System.Drawing.Graphics>オブジェクト。 名前のファイル (またはストリーム) に渡す、<xref:System.Drawing.Imaging.Metafile>コンス トラクター。 作成した後、<xref:System.Drawing.Imaging.Metafile>オブジェクトを渡す<xref:System.Drawing.Imaging.Metafile>オブジェクトを<xref:System.Drawing.Graphics.DrawImage%2A>のメソッドを<xref:System.Drawing.Graphics>オブジェクト。  
  
 例は、作成、 <xref:System.Drawing.Imaging.Metafile> EMF (メタファイル) ファイルからオブジェクトとで、左上隅のイメージが描画されます (60, 10)。  
  
 次の図は、指定した位置に描画するメタファイルを示します。  
  
 ![イメージの位置](./media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
