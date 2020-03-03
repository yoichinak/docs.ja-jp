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
ms.openlocfilehash: 522a1012fc7bdd54860b0538064ee073f7a761f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918426"
---
# <a name="constituent-controls"></a>内在コントロール
ユーザー コントロールを構成するコントロール ("*内在コントロール*" と呼ばれます) は、カスタム グラフィックスのレンダリングに関してはそれほど柔軟ではありません。 すべての Windows フォームコントロールは、独自の<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドを使用して独自のレンダリングを処理します。 このメソッドは保護されているため、開発者はアクセスできず、したがってコントロールが描画されるときに実行を防ぐことはできません。 ただし、これは、内在コントロールの外観に影響を与えるコードを追加できないという意味ではありません。 イベント ハンドラーを追加することで、追加のレンダリングを実現できます。 たとえば、という名前<xref:System.Windows.Forms.UserControl> `MyButton`のボタンを使用してを作成したとします。 によって<xref:System.Web.UI.WebControls.Button>提供された内容を超えて追加のレンダリングを使用する場合は、次のようなコードをユーザーコントロールに追加します。  
  
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
> などの一部の Windows フォームコントロール<xref:System.Windows.Forms.TextBox>は、Windows によって直接描画されます。 これらのインスタンス<xref:System.Windows.Forms.Control.OnPaint%2A>では、メソッドは呼び出されません。したがって、上記の例は呼び出されません。  
  
 この例は、`MyButton.Paint` イベントが実行されるたびに実行するメソッドを作成し、それによって追加のグラフィカル表示をコントロールに追加します。 これにより `MyButton.OnPaint` の実行は妨げられないので、カスタム描画に加えて、ボタンによって通常実行されるすべての描画が実行されることに注意してください。 GDI+ テクノロジとカスタム レンダリングについて詳しくは、　[GDI+ を使ったグラフィカル イメージの作成](../advanced/how-to-create-graphics-objects-for-drawing.md) に関するページをご覧ください。 コントロールの表示を独自のものにしたい場合の最善の方法は、継承コントロールを作成し、カスタム レンダリング コードをそこに記述するというものです。 詳しくは、「[ユーザー描画コントロール](user-drawn-controls.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [ユーザー描画コントロール](user-drawn-controls.md)
- [方法: 描画用のグラフィックスオブジェクトを作成する](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
