---
title: '方法: Canvas の添付プロパティを使用して子要素を配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: 347c8502bd4c5fafcde7a142327f85bfb75b9954
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159628"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a>方法: Canvas の添付プロパティを使用して子要素を配置する
この例の添付プロパティを使用する方法を示しています。<xref:System.Windows.Controls.Canvas>子要素を配置します。  
  
## <a name="example"></a>例  
 次の例には、4 が加算されます<xref:System.Windows.Controls.Button>要素の親の子要素として<xref:System.Windows.Controls.Canvas>します。 各要素が表される、 <xref:System.Windows.Controls.Canvas.Bottom%2A>、 <xref:System.Windows.Controls.Canvas.Left%2A>、 <xref:System.Windows.Controls.Canvas.Right%2A>、および<xref:System.Windows.Controls.Canvas.Top%2A>します。
各<xref:System.Windows.Controls.Button>が、親に対する相対的な配置されている<xref:System.Windows.Controls.Canvas>とその割り当てプロパティ値に従ってします。  
  
 [!code-cpp[CanvasAttachedProperties#1](~/samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.Canvas.Bottom%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- <xref:System.Windows.Controls.Canvas.Right%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Button>
- [パネルの概要](panels-overview.md)
- [方法のトピック](canvas-how-to-topics.md)
- [添付プロパティの概要](../advanced/attached-properties-overview.md)
