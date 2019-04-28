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
ms.openlocfilehash: 099bc9f5359f19439f308f28a6766d470956daea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781278"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>方法: イメージ テクスチャによって図形を塗りつぶす
使用してテクスチャを使用して、閉じた形状を入力することができます、<xref:System.Drawing.Image>クラスおよび<xref:System.Drawing.TextureBrush>クラス。  
  
## <a name="example"></a>例  
 次の例では、イメージを使用して楕円を塗りつぶします。 コードを構築します、<xref:System.Drawing.Image>オブジェクト、し、そのアドレスを渡す<xref:System.Drawing.Image>オブジェクトへの引数として、<xref:System.Drawing.TextureBrush.%23ctor%2A>コンス トラクター。 3 番目のステートメントは、イメージを縮小し、4 番目のステートメントがスケーリングされたイメージの繰り返しコピーで楕円を塗りつぶします。  
  
 次のコードで、<xref:System.Drawing.TextureBrush.Transform%2A>プロパティに描画前に、イメージに適用される変換が含まれています。 元のイメージが 640 ピクセルの幅と高さが 480 ピクセルであると仮定します。 変換では、水平および垂直方向のスケーリング値を設定して、イメージを 75 × 75 に縮小します。  
  
> [!NOTE]
>  次の例では、イメージのサイズが 75 × 75、および楕円サイズは 150 × 250。 イメージは、入力は楕円より小さいため、楕円は、イメージを並べて表示されます。 意味するイメージまで繰り返されます水平および垂直に形状の境界をタイルに到達します。 タイルの詳細については、次を参照してください。[方法。イメージに図形をタイル](how-to-tile-a-shape-with-an-image.md)します。  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- [ブラシを使用した図形の塗りつぶし](using-a-brush-to-fill-shapes.md)
