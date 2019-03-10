---
title: '方法: Windows フォームに塗りつぶした楕円を描画します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- circular shapes
- drawing [Windows Forms], ellipses
- shapes [Windows Forms], drawing
- forms [Windows Forms], drawing ellipses
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
ms.openlocfilehash: 42316cd0d55b5154b21b4462157e044b30674ebd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716289"
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a>方法: Windows フォームに塗りつぶした楕円を描画します。
この例では、フォームに塗りつぶした楕円を描画します。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このメソッドを呼び出すことはできません、<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。 フォームのサイズを変更または別の形式によって隠されている場合、描画のコンテンツを再描画されませんされます。 コンテンツを自動的に再描画するために、オーバーライドする必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 常に呼び出す必要があります<xref:System.IDisposable.Dispose%2A>などのシステム リソースを消費するすべてのオブジェクトに対する<xref:System.Drawing.Brush>と<xref:System.Drawing.Graphics>オブジェクト。  
  
## <a name="see-also"></a>関連項目
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
- [アルファ ブレンドの直線と塗りつぶし](alpha-blending-lines-and-fills.md)
- [ブラシを使用した図形の塗りつぶし](using-a-brush-to-fill-shapes.md)
