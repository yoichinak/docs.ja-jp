---
title: ダブル バッファリングされたグラフィックス
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: 20ec03e6b84110f7ea00c134dc18b23f233c5f58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756014"
---
# <a name="double-buffered-graphics"></a>ダブル バッファリングされたグラフィックス
グラフィックスをプログラミングするときは、ちらつきが一般的な問題になります。 複数の複雑な描画操作を必要とするグラフィックス操作を実行すると、描画されたイメージがちらつきなどによって適切に表示されないことがあります。 このような問題に対処するために、.NET Framework では、ダブル バッファリングを利用できます。  
  
 ダブル バッファリングでは、メモリ バッファーを使用して、複数の描画操作に関連するちらつきの問題に対処します。 ダブル バッファリングを有効にすると、すべての描画操作が画面上の描画サーフェイスではなく、最初にメモリ バッファーに描画されます。 描画操作がすべて完了すると、メモリ バッファーが、関連付けられている描画サーフェイスに直接コピーされます。 画面上で実行されるグラフィックス操作は 1 つだけなので、複雑な描画操作に関連するイメージのちらつきが解消されます。  
  
## <a name="default-double-buffering"></a>既定のダブル バッファリング  
 アプリケーションでダブル バッファリングを使用するには、.NET Framework に用意されている、フォームやコントロールに対する既定のダブル バッファリングを使用するのが最も簡単です。 既定のダブル バッファリング、Windows フォームを有効にすることができ、設定が Windows コントロールを作成した、<xref:System.Windows.Forms.Control.DoubleBuffered%2A>プロパティを`true`またはを使用して、<xref:System.Windows.Forms.Control.SetStyle%2A>メソッド。 詳細については、「[方法 :フォームとコントロールのダブル バッファリングによってグラフィックスのちらつきを軽減](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)します。  
  
## <a name="manually-managing-buffered-graphics"></a>バッファリングされたグラフィックスの手動管理  
 アニメーションや高度なメモリ管理など、より高度なダブル バッファリングのシナリオでは、.NET Framework クラスを使用して独自のダブル バッファリング ロジックを実装できます。 割り当てと管理、個々 のグラフィックス バッファーを担当するクラスは、<xref:System.Drawing.BufferedGraphicsContext>クラス。 すべてのアプリケーション ドメインが独自の既定<xref:System.Drawing.BufferedGraphicsContext>ダブル バッファリングをそのアプリケーション用の既定のすべてを管理するインスタンス。 ほとんどの場合があります、アプリケーションごとに 1 つだけのアプリケーション ドメイン 1 つの既定値は通常、 <xref:System.Drawing.BufferedGraphicsContext> 1 つのアプリケーション。 既定の<xref:System.Drawing.BufferedGraphicsContext>インスタンスで管理されて、<xref:System.Drawing.BufferedGraphicsManager>クラス。 既定値への参照を取得する<xref:System.Drawing.BufferedGraphicsContext>インスタンスを呼び出すことによって、<xref:System.Drawing.BufferedGraphicsManager.Current%2A>します。 作成することも、専用<xref:System.Drawing.BufferedGraphicsContext>インスタンスで、視覚的に処理を要するアプリケーションのパフォーマンスを向上させることができます。 作成する方法については、<xref:System.Drawing.BufferedGraphicsContext>インスタンスは、「[方法。バッファリングされたグラフィックスを手動で管理](how-to-manually-manage-buffered-graphics.md)します。  
  
## <a name="manually-displaying-buffered-graphics"></a>バッファリングされたグラフィックスの手動表示  
 インスタンスを使用することができます、<xref:System.Drawing.BufferedGraphicsContext>呼び出すことによってグラフィックスのバッファーを作成するクラス、<xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>のインスタンスを返す、<xref:System.Drawing.BufferedGraphics>クラス。 A<xref:System.Drawing.BufferedGraphics>オブジェクトは、フォームやコントロールなどのレンダリング サーフェイスに関連付けられているメモリ バッファーを管理します。  
  
 インスタンス化された後、<xref:System.Drawing.BufferedGraphics>クラスは、メモリ内のグラフィックス バッファーへのレンダリングを管理します。 プロパティを通じてメモリ バッファーにグラフィックスを表示するには、 <xref:System.Drawing.BufferedGraphics.Graphics%2A>、公開する、<xref:System.Drawing.Graphics>直接メモリ バッファーを表すオブジェクト。 これを描画できる<xref:System.Drawing.Graphics>オブジェクトと同じように、<xref:System.Drawing.Graphics>描画サーフェイスを表すオブジェクト。 使用することができます、すべてのグラフィックスをバッファーに描画すると、<xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType>画面上の描画サーフェイスにバッファーの内容をコピーします。  
  
 使用しての詳細については、<xref:System.Drawing.BufferedGraphics>クラスを参照してください[バッファリングされたグラフィックスのレンダリング手動で](how-to-manually-render-buffered-graphics.md)します。 グラフィックスの描画の詳細については、「[Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.BufferedGraphics>
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphicsManager>
- [方法: バッファリングされたグラフィックスを手動で描画します。](how-to-manually-render-buffered-graphics.md)
- [方法: フォームとコントロールのダブル バッファリングによってグラフィックスのちらつきを軽減します。](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)
- [方法: バッファリングされたグラフィックスを手動で管理します。](how-to-manually-manage-buffered-graphics.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
