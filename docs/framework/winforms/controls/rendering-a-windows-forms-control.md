---
title: Windows フォーム コントロールのレンダリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: b24fbefac0dcfb666e25ad1d1726ef2cf8a5d84e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968275"
---
# <a name="rendering-a-windows-forms-control"></a>Windows フォーム コントロールのレンダリング
レンダリングとは、ユーザーの画面で視覚的表現を作成するプロセスを指します。 Windows フォームは、GDI (新しい Windows グラフィックスライブラリ) を使用してレンダリングを行います。 GDI へのアクセスを提供するマネージクラスは、 <xref:System.Drawing?displayProperty=nameWithType>名前空間とその副名前空間にあります。  
  
 コントロールのレンダリングには、次の要素が含まれます。  
  
- 基本クラス<xref:System.Windows.Forms.Control?displayProperty=nameWithType>によって提供される描画機能。  
  
- GDI グラフィックスライブラリの重要な要素。  
  
- 描画領域のジオメトリ。  
  
- グラフィックスリソースを解放する手順。  
  
## <a name="drawing-functionality-provided-by-control"></a>コントロールによって提供される描画機能  
 基底クラス<xref:System.Windows.Forms.Control>は、 <xref:System.Windows.Forms.Control.Paint>イベントを通じて描画機能を提供します。 コントロールは、表示<xref:System.Windows.Forms.Control.Paint>を更新する必要があるときに常にイベントを発生させます。 .NET Framework のイベントの詳細については、「[イベントの処理と発生](../../../standard/events/index.md)」を参照してください。  
  
 <xref:System.Windows.Forms.Control.Paint>イベントのイベントデータクラスは、コントロールを描画するために必要なデータ (グラフィックスオブジェクトへのハンドル、および描画する領域を表す四角形オブジェクトを保持します) を保持します。 <xref:System.Windows.Forms.PaintEventArgs> これらのオブジェクトは、次のコードフラグメントに太字で示されています。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics>は、このトピックの後半の「GDI の説明」で説明されているように、描画機能をカプセル化するマネージクラスです。 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>は<xref:System.Drawing.Rectangle>構造体のインスタンスであり、コントロールが描画できる領域を定義します。 コントロール開発者は、この<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>トピックで<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>後述する「ジオメトリの説明」で説明されているように、コントロールのプロパティを使用してを計算できます。  
  
 コントロールは、継承元<xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control>のメソッドをオーバーライドすることにより、レンダリングロジックを提供する必要があります。 <xref:System.Windows.Forms.Control.OnPaint%2A>グラフィックスオブジェクトと、 <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>に渡される<xref:System.Windows.Forms.PaintEventArgs>インスタンスのプロパティを通じて描画する四角形へのアクセスを取得します。  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 基底<xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control.Paint>クラスのメソッドは描画機能を実装しませんが、イベントに登録されているイベントデリゲートを呼び出すだけです。 <xref:System.Windows.Forms.Control> をオーバーライド<xref:System.Windows.Forms.Control.OnPaint%2A>する場合は、通常、基本<xref:System.Windows.Forms.Control.OnPaint%2A>クラスのメソッドを呼び出して、登録されて<xref:System.Windows.Forms.Control.Paint>いるデリゲートがイベントを受け取るようにする必要があります。 ただし、画面全体を描画するコントロールでは、基本クラスの<xref:System.Windows.Forms.Control.OnPaint%2A>を呼び出さないでください。これにより、ちらつきが発生します。 <xref:System.Windows.Forms.Control.OnPaint%2A>イベントをオーバーライドする例につい[ては、「方法:進行状況](how-to-create-a-windows-forms-control-that-shows-progress.md)を表示する Windows フォームコントロールを作成します。  
  
> [!NOTE]
> コントロールから直接<xref:System.Windows.Forms.Control.OnPaint%2A>呼び出すのではなく、(から<xref:System.Windows.Forms.Control>継承<xref:System.Windows.Forms.Control.Invalidate%2A>された) メソッドまたはを呼び出す<xref:System.Windows.Forms.Control.Invalidate%2A>他のメソッドを呼び出します。 メソッド<xref:System.Windows.Forms.Control.Invalidate%2A>が呼び出さ<xref:System.Windows.Forms.Control.OnPaint%2A>れます。 メソッドはオーバーロードされており、に<xref:System.Windows.Forms.Control.Invalidate%2A> `e`指定された引数によっては、コントロールが画面領域の一部またはすべてを再描画します。 <xref:System.Windows.Forms.Control.Invalidate%2A>  
  
 基底<xref:System.Windows.Forms.Control>クラスは、描画に便利な別のメソッド<xref:System.Windows.Forms.Control.OnPaintBackground%2A> (メソッド) を定義します。  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>ウィンドウの背景 (およびその図形) を描画し<xref:System.Windows.Forms.Control.OnPaint%2A>ます。また、個々の描画要求が1つ<xref:System.Windows.Forms.Control.Paint>のイベントに結合され、その結果、すべての領域を対象とするすべての領域をカバーします。描画. たとえば、コントロールのグラデーションカラー <xref:System.Windows.Forms.Control.OnPaintBackground%2A>の背景を描画する必要がある場合は、を呼び出すことができます。  
  
 に<xref:System.Windows.Forms.Control.OnPaintBackground%2A>はイベントのような用語があり、 `OnPaint`メソッドと同じ引数を取り<xref:System.Windows.Forms.Control.OnPaintBackground%2A>ますが、は true のイベントメソッドではありません。 イベントは存在`PaintBackground`せず<xref:System.Windows.Forms.Control.OnPaintBackground%2A> 、イベントデリゲートを呼び出しません。 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>メソッドをオーバーライドする場合、派生クラスは基底クラスの<xref:System.Windows.Forms.Control.OnPaintBackground%2A>メソッドを呼び出す必要がありません。  
  
## <a name="gdi-basics"></a>GDI + の基礎  
 クラス<xref:System.Drawing.Graphics>には、円、三角形、円弧、楕円などのさまざまな図形を描画するためのメソッドと、テキストを表示するためのメソッドが用意されています。 名前<xref:System.Drawing?displayProperty=nameWithType>空間とその副名前空間には、図形 (円、四角形、円弧など)、色、フォント、ブラシなどのグラフィックス要素をカプセル化するクラスが含まれています。 GDI の詳細については、「[マネージグラフィックスクラスの使用](../advanced/using-managed-graphics-classes.md)」を参照してください。 GDI の基本事項については、 [「方法:進行状況](how-to-create-a-windows-forms-control-that-shows-progress.md)を表示する Windows フォームコントロールを作成します。  
  
## <a name="geometry-of-the-drawing-region"></a>描画領域のジオメトリ  
 コントロール<xref:System.Windows.Forms.Control.ClientRectangle%2A>のプロパティは、ユーザーの画面上のコントロールで使用できる四角形の領域を指定します<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 。また<xref:System.Windows.Forms.PaintEventArgs> 、のプロパティは、実際に描画される領域を指定します。 (描画は、引数として<xref:System.Windows.Forms.Control.Paint>インスタンスを<xref:System.Windows.Forms.PaintEventArgs>受け取るイベントメソッドで行われることに注意してください)。 コントロールは、コントロールの表示の小さいセクションが変更された場合のように、使用可能な領域の一部だけを描画する必要がある場合があります。 このような状況では、コントロール開発者は、描画する実際の四角形を計算<xref:System.Windows.Forms.Control.Invalidate%2A>してに渡す必要があります。 引数として<xref:System.Windows.Forms.Control.Invalidate%2A>または<xref:System.Drawing.Region>を<xref:System.Drawing.Rectangle>受け取るのオーバーロードされたバージョンは、その<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>引数を<xref:System.Windows.Forms.PaintEventArgs>使用してプロパティを生成します。  
  
 次のコードフラグメントは、カスタム`FlashTrackBar`コントロールが四角形の領域を計算して描画する方法を示しています。 変数`client`は、プロパティ<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>を表します。 完全なサンプルについて[は、「方法:進行状況](how-to-create-a-windows-forms-control-that-shows-progress.md)を表示する Windows フォームコントロールを作成します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>グラフィックスリソースの解放  
 グラフィックスオブジェクトは、システムリソースを使用するため、コストが高くなります。 このようなオブジェクトには<xref:System.Drawing.Graphics?displayProperty=nameWithType> 、クラスのインスタンスだけで<xref:System.Drawing.Brush?displayProperty=nameWithType>なく<xref:System.Drawing.Pen?displayProperty=nameWithType>、、、およびその他のグラフィックスクラスのインスタンスが含まれます。 グラフィックスリソースは、必要なときにのみ作成し、使用が終了したらすぐにリリースすることが重要です。 <xref:System.IDisposable>インターフェイスを実装する型を作成する場合は、リソース<xref:System.IDisposable.Dispose%2A>を解放するために、メソッドの使用が終了したときにメソッドを呼び出します。  
  
 次のコードフラグメントは、カスタム`FlashTrackBar`コントロールがリソースを<xref:System.Drawing.Brush>作成および解放する方法を示しています。 完全なソースコードについて[は、「方法:進行状況](how-to-create-a-windows-forms-control-that-shows-progress.md)を表示する Windows フォームコントロールを作成します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [方法: 進行状況を表示する Windows フォームコントロールを作成する](how-to-create-a-windows-forms-control-that-shows-progress.md)
