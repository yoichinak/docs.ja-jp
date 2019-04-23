---
title: '方法: 純色ブラシを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
ms.openlocfilehash: ed9ec1f52b41c83b3cc6e36dedf97f1c00db42e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213442"
---
# <a name="how-to-create-a-solid-brush"></a>方法: 純色ブラシを作成する
この例で作成、<xref:System.Drawing.SolidBrush>で使用できるオブジェクト、<xref:System.Drawing.Graphics>図形を塗りつぶすためのオブジェクト。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 呼び出す必要がありますが、それらを使用して完了後<xref:System.IDisposable.Dispose%2A>ブラシ オブジェクトなどのシステム リソースを消費するオブジェクト。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
- [GDI+ でのブラシと塗りつぶされた図形](brushes-and-filled-shapes-in-gdi.md)
- [ブラシを使用した図形の塗りつぶし](using-a-brush-to-fill-shapes.md)
