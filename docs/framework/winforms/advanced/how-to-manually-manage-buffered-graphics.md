---
title: '方法: バッファリングされたグラフィックスを手動で管理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968598"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>方法: バッファリングされたグラフィックスを手動で管理する
より高度なダブルバッファリングのシナリオでは、.NET Framework クラスを使用して、独自のダブルバッファリングロジックを実装できます。 個々のグラフィックスバッファーの割り当てと管理を行うクラスは<xref:System.Drawing.BufferedGraphicsContext> 、クラスです。 すべてのアプリケーションには、 <xref:System.Drawing.BufferedGraphicsContext>そのアプリケーションのすべての既定のダブルバッファリングを管理する独自の既定値があります。 このインスタンスへの参照を取得するには、 <xref:System.Drawing.BufferedGraphicsManager.Current%2A>を呼び出します。  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>既定の BufferedGraphicsContext への参照を取得するには  
  
- 次のコード例に示すように、プロパティを設定します。<xref:System.Drawing.BufferedGraphicsManager.Current%2A>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > クラスから<xref:System.Drawing.BufferedGraphicsContext> `Dispose` 受け取る参照に対してメソッドを呼び出す必要はありません<xref:System.Drawing.BufferedGraphicsManager> 。 は<xref:System.Drawing.BufferedGraphicsManager> 、既定<xref:System.Drawing.BufferedGraphicsContext>のインスタンスのメモリ割り当てと分布をすべて処理します。  
  
     アニメーションなどのグラフィックを多用するアプリケーションの場合は、 <xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsManager>ではなく<xref:System.Drawing.BufferedGraphicsContext>専用のを使用して、パフォーマンスを向上させることができます。 これにより、アプリケーションに関連付けられている他のすべてのバッファリングされたグラフィックスを管理する際のパフォーマンスオーバーヘッドを発生させずに、グラフィックスバッファーを個別に作成して管理できます。ただし、アプリケーションで使用されるメモリの方が多くなります。  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>専用の BufferedGraphicsContext を作成するには  
  
- 次のコード例に示すように<xref:System.Drawing.BufferedGraphicsContext> 、クラスの新しいインスタンスを宣言して作成します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.BufferedGraphicsContext>
- [ダブル バッファリングされたグラフィックス](double-buffered-graphics.md)
- [方法: バッファリングされるグラフィックスを手動でレンダリングする](how-to-manually-render-buffered-graphics.md)
