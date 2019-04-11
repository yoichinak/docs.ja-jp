---
title: 内在コントロール
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 76a5a4f9b02a71616d247a1bb0f03cc0aec1d70d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224878"
---
# <a name="constituent-controls"></a>内在コントロール
ユーザー コントロールを構成するコントロール ("*内在コントロール*" と呼ばれます) は、カスタム グラフィックスのレンダリングに関してはそれほど柔軟ではありません。 すべての Windows フォーム コントロールの処理が自分で独自のレンダリング<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。 このメソッドは保護されているため、開発者はアクセスできず、したがってコントロールが描画されるときに実行を防ぐことはできません。 ただし、これは、内在コントロールの外観に影響を与えるコードを追加できないという意味ではありません。 イベント ハンドラーを追加することで、追加のレンダリングを実現できます。 たとえば、作成された、<xref:System.Windows.Forms.UserControl>という名前のボタンで`MyButton`します。 によって提供されたどのようなレンダリングを追加するさせたいかどうかは、<xref:System.Web.UI.WebControls.Button>コードを次のようなユーザー コントロールを追加するは。  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  などの一部の Windows フォーム コントロール<xref:System.Windows.Forms.TextBox>、Windows によって直接描画されます。 これらのインスタンスで、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドが呼び出されないと、そのため、上記の例では呼び出されない。  
  
 この例は、`MyButton.Paint` イベントが実行されるたびに実行するメソッドを作成し、それによって追加のグラフィカル表示をコントロールに追加します。 これにより `MyButton.OnPaint` の実行は妨げられないので、カスタム描画に加えて、ボタンによって通常実行されるすべての描画が実行されることに注意してください。 GDI+ テクノロジとカスタム レンダリングについて詳しくは、「[Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md)」 (GDI+ でのグラフィカル イメージの作成) をご覧ください。 コントロールの表示を独自のものにしたい場合の最善の方法は、継承コントロールを作成し、カスタム レンダリング コードをそこに記述するというものです。 詳しくは、「[ユーザー描画コントロール](user-drawn-controls.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [ユーザー描画コントロール](user-drawn-controls.md)
- [方法: 描画する Graphics オブジェクトを作成する](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
