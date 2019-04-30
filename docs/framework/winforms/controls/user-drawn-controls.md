---
title: ユーザー描画コントロール
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: 06513fc44782c78d2d69b82130542949519c0107
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947954"
---
# <a name="user-drawn-controls"></a>ユーザー描画コントロール
.NET Framework では、独自のコントロールを簡単に開発する機能を提供します。 コードによって結合されて標準のコントロールのセットである、ユーザー コントロールを作成することもをゼロから独自のコントロールをデザインすることができます。 既存のコントロールから継承するコントロールを作成し、本来の機能を追加する継承を使用することもできます。 どのようなアプローチを使用すると、.NET Framework は、任意のコントロールを作成するためのカスタムのグラフィカル インターフェイスを描画するために機能を提供します。  
  
 コントロールの描画には、コントロールのコードの実行、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。 1 つの引数、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは、<xref:System.Windows.Forms.PaintEventArgs>すべての情報と、コントロールのレンダリングに必要な機能を提供するオブジェクト。 <xref:System.Windows.Forms.PaintEventArgs>プロパティとして、コントロールの描画に使用される 2 つのプリンシパル オブジェクトを提供します。  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> オブジェクトの描画されるコントロールの一部を表す四角形。 これには、全体をコントロール、またはコントロールの描画方法に応じたコントロールの一部です。  
  
- <xref:System.Drawing.Graphics> オブジェクト - いくつかのグラフィック指向オブジェクトとコントロールを描画するために必要な機能を提供するメソッドをカプセル化します。  
  
 詳細については、<xref:System.Drawing.Graphics>オブジェクトとそれを使用して、参照してください方法[方法。描画の Graphics オブジェクトを作成](../advanced/how-to-create-graphics-objects-for-drawing.md)です。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>コントロールの描画または画面で、更新されるたびにイベントが発生し、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>オブジェクトが描画を実行、四角形を表します。 コントロール全体を更新する必要がある場合、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>コントロール全体のサイズを表します。 コントロールの一部がただし、更新、する必要があるあれば、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>オブジェクトが再描画する必要があるリージョンのみを表します。 このようなケースの例は、別のコントロールまたはユーザー インターフェイスでのフォーム コントロールの一部が見えない場合になります。  
  
 継承する場合、<xref:System.Windows.Forms.Control>クラスがオーバーライドする必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド内でのグラフィックス レンダリング コードを提供します。 ユーザー コントロールまたは継承されたコントロールにカスタムのグラフィカル インターフェイスを提供する場合もこれを行うオーバーライドすることで、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。 例は、以下に示します。  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
         this.Size));  
   }
}  
```  
  
 前の例では、非常にシンプルなグラフィカル表示コントロールを描画する方法を示します。 呼び出す、<xref:System.Windows.Forms.Control.OnPaint%2A>基底クラスのメソッドを作成、<xref:System.Drawing.Pen>を描画する対象のオブジェクトし、最後に、四角形に楕円を描画しますが定め、<xref:System.Windows.Forms.Control.Location%2A>と<xref:System.Windows.Forms.Control.Size%2A>コントロールの。 この例での使用を示しますが、ほとんどのレンダリング コードは、これよりも大幅に複雑になります、<xref:System.Drawing.Graphics>オブジェクト内に含まれる、<xref:System.Windows.Forms.PaintEventArgs>オブジェクト。 既にグラフィカル表現をなどが含まれるクラスから継承している場合<xref:System.Windows.Forms.UserControl>または<xref:System.Windows.Forms.Button>、その表現をレンダリングに組み込むしたくない、基本クラスを呼び出す必要はありません、 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。  
  
 内のコード、<xref:System.Windows.Forms.Control.OnPaint%2A>および更新は、コントロールが最初に描画されるときに、コントロールのメソッドが実行されます。 サイズを変更するたびに、コントロールが再描画されることを確認するには、コントロールのコンス トラクターに次の行を追加します。  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  使用して、<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>四角形以外のコントロールを実装するプロパティ。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [方法: 描画の Graphics オブジェクトを作成します。](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [内在コントロール](constituent-controls.md)
- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
