---
title: '方法: ペンの色を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: ee2d3f8cdf6dd10ca2a9ff0dd3e66b164c84f21b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637002"
---
# <a name="how-to-set-the-color-of-a-pen"></a>方法: ペンの色を設定する
この例は、既存の色を変更<xref:System.Drawing.Pen>オブジェクト  
  
## <a name="example"></a>例  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- A<xref:System.Drawing.Pen>という名前のオブジェクト`myPen`します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 呼び出す必要があります<xref:System.Drawing.Pen.Dispose%2A>システム リソースを消費するオブジェクト (など<xref:System.Drawing.Pen>オブジェクト) を使用してそれらが完了した後。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Pen>
- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
- [方法: ペンを作成します。](how-to-create-a-pen.md)
- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+ でのペン、直線、および四角形](pens-lines-and-rectangles-in-gdi.md)
