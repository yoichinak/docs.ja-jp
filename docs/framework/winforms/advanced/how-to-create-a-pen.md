---
title: '方法: ペンを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
ms.openlocfilehash: 3d88824845bf357dd9ee5f1ee8fd02f095aee605
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716921"
---
# <a name="how-to-create-a-pen"></a>方法: ペンを作成します。
この例で作成、<xref:System.Drawing.Pen>オブジェクト。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 などのシステム リソースを消費しているオブジェクトを使用して完了後<xref:System.Drawing.Pen>オブジェクトを呼び出す必要があります<xref:System.Drawing.Pen.Dispose%2A>にします。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Pen>
- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
- [GDI+ でのペン、直線、および四角形](pens-lines-and-rectangles-in-gdi.md)
