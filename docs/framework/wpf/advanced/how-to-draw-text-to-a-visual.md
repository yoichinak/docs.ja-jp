---
title: '方法: ビジュアルにテキストを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 1ea31540ad59ab419e209e4133bcb88640cc01fe
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368910"
---
# <a name="how-to-draw-text-to-a-visual"></a>方法: ビジュアルにテキストを描画する
次の例では、テキストを描画する方法を示しています、<xref:System.Windows.Media.DrawingVisual>を使用して、<xref:System.Windows.Media.DrawingContext>オブジェクト。 描画コンテキストが呼び出しによって返される、<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>のメソッドを<xref:System.Windows.Media.DrawingVisual>オブジェクト。 グラフィックスとテキストを描画コンテキストに描画できます。  
  
 描画コンテキストにテキストを描画するために使用して、<xref:System.Windows.Media.DrawingContext.DrawText%2A>のメソッドを<xref:System.Windows.Media.DrawingContext>オブジェクト。 コンテンツを描画コンテキストに描画が完了したら、呼び出し、<xref:System.Windows.Media.DrawingContext.Close%2A>メソッドを描画コンテキストを閉じるし、内容を保持します。  
  
## <a name="example"></a>例  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  上記のコードの抽出元となった完全なコード サンプルについては、「[DrawingVisual を使用したヒット テストのサンプル](https://go.microsoft.com/fwlink/?LinkID=159994)」を参照してください。
