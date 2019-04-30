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
ms.openlocfilehash: 8de87e17d1baedccfe18bfded3ccab7ab59f0a09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012478"
---
# <a name="rendering-a-windows-forms-control"></a>Windows フォーム コントロールのレンダリング
レンダリングは、ユーザーの画面にビジュアル表現を作成するプロセスを指します。 Windows フォームを使用して[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)](新しい Windows グラフィックス ライブラリ) をレンダリングします。 アクセスを提供するマネージ クラス[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]では、<xref:System.Drawing?displayProperty=nameWithType>名前空間とその下位の名前空間。  
  
 コントロールのレンダリングで、次の要素が含まれます。  
  
- 基本クラスによって提供される描画機能<xref:System.Windows.Forms.Control?displayProperty=nameWithType>します。  
  
- 重要な要素、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]グラフィックス ライブラリ。  
  
- 描画領域のジオメトリ。  
  
- グラフィックス リソースを解放するプロシージャです。  
  
## <a name="drawing-functionality-provided-by-control"></a>描画コントロールによって提供される機能  
 基本クラス<xref:System.Windows.Forms.Control>を通じて描画機能を提供します。 その<xref:System.Windows.Forms.Control.Paint>イベント。 コントロールを有効に、<xref:System.Windows.Forms.Control.Paint>イベントの表示を更新する必要があるたびにします。 .NET Framework のイベントの詳細については、次を参照してください。[処理とイベントの発生](../../../standard/events/index.md)します。  
  
 イベント データ クラスに対する、<xref:System.Windows.Forms.Control.Paint>イベント、<xref:System.Windows.Forms.PaintEventArgs>コントロールを描画するために必要なデータを保持する — グラフィック オブジェクト、および描画する領域を表す四角形オブジェクトを識別するハンドル。 これらのオブジェクトが示すように、次のコード フラグメントでは太字です。  
  
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
  
 <xref:System.Drawing.Graphics> 説明」の説明に従って、描画機能をカプセル化するマネージ クラスは、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]このトピックで後述します。 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>のインスタンスである、<xref:System.Drawing.Rectangle>構造体であり、コントロールの描画に使用できる使用可能な領域を定義します。 コントロールの開発者が計算できる、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>を使用して、 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> geometry このトピックの後半の説明」の説明に従って、コントロールのプロパティ。  
  
 コントロールは、オーバーライドすることでレンダリング ロジックを提供する必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドから継承した<xref:System.Windows.Forms.Control>します。 <xref:System.Windows.Forms.Control.OnPaint%2A> グラフィックス オブジェクトと経由描画する四角形へのアクセスを取得、<xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A>と<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>のプロパティ、<xref:System.Windows.Forms.PaintEventArgs>にインスタンスが渡されます。  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッド ベースの<xref:System.Windows.Forms.Control>クラスは、描画機能を実装していませんが、単に登録されているイベントのデリゲートを呼び出す、<xref:System.Windows.Forms.Control.Paint>イベント。 オーバーライドする場合<xref:System.Windows.Forms.Control.OnPaint%2A>、通常、呼び出す必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>デリゲートを登録するための基本クラスのメソッドの受信、<xref:System.Windows.Forms.Control.Paint>イベント。 ただし、コントロールの表面全体を描画するには、基本クラスが呼び出す必要がない<xref:System.Windows.Forms.Control.OnPaint%2A>ちらつきが導入されます。 オーバーライドする例については、<xref:System.Windows.Forms.Control.OnPaint%2A>イベントを参照してください、[方法。進行状況を示す Windows フォーム コントロールを作成する](how-to-create-a-windows-forms-control-that-shows-progress.md)します。  
  
> [!NOTE]
>  呼び出さないでください<xref:System.Windows.Forms.Control.OnPaint%2A>を直接コントロールの代わりに、起動、<xref:System.Windows.Forms.Control.Invalidate%2A>メソッド (から継承された<xref:System.Windows.Forms.Control>) または他の方法を呼び出す<xref:System.Windows.Forms.Control.Invalidate%2A>します。 <xref:System.Windows.Forms.Control.Invalidate%2A>メソッドが呼び出されます<xref:System.Windows.Forms.Control.OnPaint%2A>します。 <xref:System.Windows.Forms.Control.Invalidate%2A>メソッドをオーバー ロードしてに渡される引数に応じて<xref:System.Windows.Forms.Control.Invalidate%2A> `e`、一部またはすべての画面領域のコントロールを再描画します。  
  
 基本<xref:System.Windows.Forms.Control>クラス描画のために役立つもう 1 つのメソッドを定義する —、<xref:System.Windows.Forms.Control.OnPaintBackground%2A>メソッド。  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 背景を描画 (これにより、図形) ウィンドウの中に、高速にすることが保証されます<xref:System.Windows.Forms.Control.OnPaint%2A>詳細を描画し、個々 の描画要求が 1 つに結合されますので、遅い場合があります<xref:System.Windows.Forms.Control.Paint>に必要なすべての領域をカバーするイベント再描画されます。 呼び出したい場合があります、<xref:System.Windows.Forms.Control.OnPaintBackground%2A>コントロールのグラデーションの色の背景を描画する場合。  
  
 中に<xref:System.Windows.Forms.Control.OnPaintBackground%2A>、イベントのような命名規則がありと同じ引数を受け取り、`OnPaint`メソッド、 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> true イベント メソッドではありません。 ない`PaintBackground`イベントと<xref:System.Windows.Forms.Control.OnPaintBackground%2A>イベント デリゲートは呼び出されません。 オーバーライドする場合、<xref:System.Windows.Forms.Control.OnPaintBackground%2A>メソッドでは、派生クラスに呼び出す必要はありません、<xref:System.Windows.Forms.Control.OnPaintBackground%2A>基底クラスのメソッド。  
  
## <a name="gdi-basics"></a>GDI + の基本  
 <xref:System.Drawing.Graphics>クラスには、円、三角形、弧、および楕円などのさまざまな図形を描画するためのメソッドとテキストを表示するためのメソッドが用意されています。 <xref:System.Drawing?displayProperty=nameWithType>名前空間とそのサブ図形 (円、四角形、弧、および他のユーザー)、色、フォント、ブラシなどのグラフィックス要素をカプセル化するクラスが含まれています。 詳細については[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]を参照してください[マネージ グラフィックス クラスを使用して](../advanced/using-managed-graphics-classes.md)します。 Essentials[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]も記載されて、[方法。進行状況を示す Windows フォーム コントロールを作成する](how-to-create-a-windows-forms-control-that-shows-progress.md)します。  
  
## <a name="geometry-of-the-drawing-region"></a>描画領域のジオメトリ  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A>コントロールのプロパティは、ユーザーの画面で、コントロールで使用できる四角形の領域を指定します中に、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>プロパティの<xref:System.Windows.Forms.PaintEventArgs>が実際に描画される領域を指定します。 (で描画を行うことに注意してください、<xref:System.Windows.Forms.Control.Paint>を受け取るイベント メソッドを<xref:System.Windows.Forms.PaintEventArgs>インスタンスの引数として)。 コントロールは、コントロールの表示の変更の場合と小さいセクションと同様、使用可能な領域では、一部だけを描画する必要があります。 これらの状況では、コントロールの開発者が実際の四角形を描画しに渡さを計算する必要があります<xref:System.Windows.Forms.Control.Invalidate%2A>します。 オーバー ロードされたバージョンの<xref:System.Windows.Forms.Control.Invalidate%2A>を受け取る、<xref:System.Drawing.Rectangle>または<xref:System.Drawing.Region>を引数としてその引数を使用して生成する、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>プロパティの<xref:System.Windows.Forms.PaintEventArgs>します。  
  
 次のコード フラグメントを示していますが、どのように`FlashTrackBar`カスタム コントロールを描画する四角形の領域を計算します。 `client`変数を表します、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>プロパティ。 完全なサンプルを参照してください。[方法。進行状況を示す Windows フォーム コントロールを作成する](how-to-create-a-windows-forms-control-that-shows-progress.md)します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>グラフィックス リソースの解放  
 グラフィックス オブジェクトは、システム リソースを使用するために高価です。 このようなオブジェクトのインスタンスを含む、<xref:System.Drawing.Graphics?displayProperty=nameWithType>クラスのインスタンスと<xref:System.Drawing.Brush?displayProperty=nameWithType>、 <xref:System.Drawing.Pen?displayProperty=nameWithType>、およびその他のグラフィックス クラス。 必要がありますが、リリースする場合にのみ、グラフィックス リソースを作成することが重要になりますがそれを使用して終了するとすぐにします。 実装する型を作成する場合、<xref:System.IDisposable>インターフェイスを呼び出してその<xref:System.IDisposable.Dispose%2A>リソースを解放するために操作を終了したらメソッド。  
  
 次のコード フラグメントを示しています、`FlashTrackBar`カスタム コントロールを作成して、解放、<xref:System.Drawing.Brush>リソース。 完全なソース コードでは、次を参照してください。[方法。進行状況を示す Windows フォーム コントロールを作成する](how-to-create-a-windows-forms-control-that-shows-progress.md)します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [方法: 進行状況を示す Windows フォーム コントロールを作成します。](how-to-create-a-windows-forms-control-that-shows-progress.md)
