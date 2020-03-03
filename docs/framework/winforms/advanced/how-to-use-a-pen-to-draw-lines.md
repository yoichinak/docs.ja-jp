---
title: '方法: ペンを使用して線を描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 263c0fbda377e64753cd2d607f633117b4b44253
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593153"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>方法: ペンを使用して線を描画する
線を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクトと<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトを提供、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、線、色や幅などの機能を格納します。  
  
## <a name="example"></a>例  
 次の例から線を描画します (20, 10) に (300, 100)。 最初のステートメントを使用して、<xref:System.Drawing.Pen.%23ctor%2A>黒のペンを作成するクラスのコンス トラクター。 渡される 1 つの引数、<xref:System.Drawing.Pen.%23ctor%2A>コンス トラクターは、<xref:System.Drawing.Color>オブジェクトを作成した、<xref:System.Drawing.Color.FromArgb%2A>メソッド。 作成に使用される値、<xref:System.Drawing.Color>オブジェクト-(255, 0、0, 0): 色のアルファ、赤、緑、および青のコンポーネントに対応しています。 これらの値は、不透明な黒のペンを定義します。  
  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Pen>
- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+ でのペン、直線、および四角形](pens-lines-and-rectangles-in-gdi.md)
