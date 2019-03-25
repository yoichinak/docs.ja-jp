---
title: '方法: 成型された Windows フォームを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], rounded
- Windows Forms, custom shapes
- Windows Forms, shaped
- shaped forms
- forms [Windows Forms], changing the shape of
- forms [Windows Forms], circular
- forms [Windows Forms], nonrectangular
- Windows Forms, nonrectangular shape
- Windows Forms, rounded
- Windows Forms, circular
- forms [Windows Forms], custom shapes
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
ms.openlocfilehash: a130614b0977aab6191f195c93454c527e6be9b8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710070"
---
# <a name="how-to-create-a-shaped-windows-form"></a>方法: 成型された Windows フォームを作成します。
この例では、フォームのサイズを変更する楕円形フォームを示します。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System.Windows.Forms> 名前空間と <xref:System.Drawing> 名前空間への参照。  
  
 この例は、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは、フォームの形状を変更します。 このコードを使用するには、メソッドの宣言とメソッドの内部の描画コードをコピーします。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Region>
- <xref:System.Drawing>
- <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>
- <xref:System.Windows.Forms.Control.Region%2A>
- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
