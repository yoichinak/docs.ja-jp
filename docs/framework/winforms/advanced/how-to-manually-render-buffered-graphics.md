---
title: '方法: バッファリングされたグラフィックスを手動で描画します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: f9763620d5fe56a0720d5d5f4ad53ec2ef18531c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705806"
---
# <a name="how-to-manually-render-buffered-graphics"></a>方法: バッファリングされたグラフィックスを手動で描画します。
独自のバッファリングされたグラフィックスを管理している場合は、グラフィックス バッファーを作成して表示できるようにする必要があります。 <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> メソッドを呼び出すことで、画面の描画サーフェイスに関連付けられている <xref:System.Drawing.BufferedGraphics> クラスのインスタンスを作成できます。 このメソッドは、フォームやコントロールなど、特定の表示サーフェイスに関連付けられている <xref:System.Drawing.BufferedGraphics> インスタンスを作成します。 <xref:System.Drawing.BufferedGraphics> インスタンスを作成した後、<xref:System.Drawing.BufferedGraphics.Graphics%2A> プロパティを通じて表すバッファーにグラフィックスを描画することができます。 グラフィックスのすべての操作を実行した後で、<xref:System.Drawing.BufferedGraphics.Render%2A> メソッドを呼び出すことで、バッファーの内容を画面にコピーできます。  
  
> [!NOTE]
>  独自の表示を実行する場合、わずかですがメモリ消費量が増加します。  
  
### <a name="to-manually-display-buffered-graphics"></a>バッファリングされたグラフィックスを手動で描画するには  
  
1.  
  <xref:System.Drawing.BufferedGraphicsContext> クラスのインスタンスへの参照を取得します。 詳細については、「[方法 :バッファリングされたグラフィックスを手動で管理](how-to-manually-manage-buffered-graphics.md)します。  
  
2.  次のコード例に示すように、<xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> メソッドを呼び出して <xref:System.Drawing.BufferedGraphics> クラスのインスタンスを作成します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  
  <xref:System.Drawing.BufferedGraphics.Graphics%2A> プロパティを設定することで、グラフィックスのバッファーにグラフィックスを描画します。 例:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  グラフィックス バッファーへのすべての描画操作が完了したら、次のコード例に示すように、<xref:System.Drawing.BufferedGraphics.Render%2A> メソッドを呼び出して、そのバッファーに関連付けられている描画サーフェイス、または指定された描画サーフェイスのいずれかにバッファーを表示します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  グラフィックのレンダリングが完了した後、<xref:System.Drawing.BufferedGraphics> インスタンスの `Dispose` メソッドを呼び出し、システム リソースを解放します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [ダブル バッファリングされたグラフィックス](double-buffered-graphics.md)
- [方法: バッファリングされたグラフィックスを手動で管理します。](how-to-manually-manage-buffered-graphics.md)
