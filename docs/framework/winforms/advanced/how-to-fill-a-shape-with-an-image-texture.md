---
title: '方法: イメージ テクスチャによって図形を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911689"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>方法: イメージ テクスチャによって図形を塗りつぶす
<xref:System.Drawing.Image> クラス<xref:System.Drawing.TextureBrush>とクラスを使用して、閉じた図形にテクスチャを埋め込むことができます。  
  
## <a name="example"></a>例  
 次の例では、楕円にイメージを塗りつぶします。 このコードは、 <xref:System.Drawing.Image>オブジェクトを構築し、その<xref:System.Drawing.Image>オブジェクトのアドレスを引数<xref:System.Drawing.TextureBrush.%23ctor%2A>としてコンストラクターに渡します。 3番目のステートメントはイメージをスケーリングし、4番目のステートメントは、拡大縮小されたイメージの繰り返しコピーを楕円に入力します。  
  
 次のコード<xref:System.Drawing.TextureBrush.Transform%2A>では、プロパティには、イメージが描画される前に適用される変換が含まれています。 元のイメージの幅が640ピクセル、高さが480ピクセルであると仮定します。 変換は、水平方向と垂直方向のスケーリング値を設定することによって、イメージを75×75に縮小します。  
  
> [!NOTE]
> 次の例では、イメージのサイズは75×75、楕円のサイズは150×250です。 画像は塗りつぶされている楕円より小さいため、楕円は画像で並べられています。 タイルは、図形の境界に到達するまで、画像が水平方向および垂直方向に繰り返されることを意味します。 タイルの詳細については[、「方法:イメージ](how-to-tile-a-shape-with-an-image.md)を含む図形を並べます。  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- [ブラシを使用した図形の塗りつぶし](using-a-brush-to-fill-shapes.md)
