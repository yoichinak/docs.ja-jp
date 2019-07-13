---
title: '方法: 純色で図形を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: d6fe7a252029ff80f21d99f7342fabb1d29fbe24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781291"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>方法: 純色で図形を塗りつぶす
純色で図形を塗りつぶす、作成、<xref:System.Drawing.SolidBrush>オブジェクト、および渡す<xref:System.Drawing.SolidBrush>オブジェクトの fill メソッドのいずれかの引数として、<xref:System.Drawing.Graphics>クラス。 次の例では、楕円の塗りつぶし色が赤にする方法を示します。  
  
## <a name="example"></a>例  
 次のコードで、<xref:System.Drawing.SolidBrush.%23ctor%2A>コンス トラクターは、<xref:System.Drawing.Color>唯一の引数としてのオブジェクト。 によって使用される値、<xref:System.Drawing.Color.FromArgb%2A>メソッドは、色のアルファ、赤、緑、および青のコンポーネントを表します。 これらの各値は 0 ~ 255 の範囲でなければなりません。 最初の 255 ことを示し、カラーは完全に不透明な 2 つ目の 255 は、最大輝度に赤のコンポーネントがあることを示します。 2 つの 0 は、緑、青のコンポーネントは、両方が 0 の輝度があることを示します。  
  
 渡される 4 つの数字 (0, 0、100, 60)、<xref:System.Drawing.Graphics.FillEllipse%2A>メソッドは、楕円の外接する四角形のサイズと場所を指定します。 四角形が、左上隅の (0, 0)、幅が 100、および 60 の高さ。  
  
 [!code-csharp[System.Drawing.UsingABrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- [ブラシを使用した図形の塗りつぶし](using-a-brush-to-fill-shapes.md)
