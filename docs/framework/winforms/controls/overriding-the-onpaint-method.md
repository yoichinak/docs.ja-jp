---
title: OnPaint メソッドのオーバーライド
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: b1eb24aaa9ed3bfede41fc5a9a80fcbdc9f749a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936449"
---
# <a name="overriding-the-onpaint-method"></a>OnPaint メソッドのオーバーライド
定義されているすべてのイベントをオーバーライドするための基本的な手順、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]が同じであり、次の一覧にまとめます。  
  
#### <a name="to-override-an-inherited-event"></a>継承されたイベントをオーバーライドするには  
  
1. 保護されたオーバーライド`On` *EventName*メソッド。  
  
2. 呼び出す、 `On` *EventName*から、オーバーライドされた基底クラスのメソッド`On` *EventName*メソッド、デリゲートを登録するため、イベントを受信します。  
  
 <xref:System.Windows.Forms.Control.Paint>イベント詳細についてはここですべての Windows フォーム コントロールをオーバーライドする必要がありますので、<xref:System.Windows.Forms.Control.Paint>イベントから継承した<xref:System.Windows.Forms.Control>します。 基本<xref:System.Windows.Forms.Control>クラスの派生コントロールを描画する必要がある方法がわからないし、描画ロジックを提供しない、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの<xref:System.Windows.Forms.Control>は単に、<xref:System.Windows.Forms.Control.Paint>に登録されているイベント レシーバーのイベント。  
  
 サンプルを実行している場合[方法。単純な Windows フォーム コントロール開発](how-to-develop-a-simple-windows-forms-control.md)、オーバーライドする例を見てきました、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。 次のコード フラグメントは、そのサンプルから取得されます。  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs>クラスにはデータが含まれています、<xref:System.Windows.Forms.Control.Paint>イベント。 次のコードに示すように 2 つのプロパティがあります。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 四角形を描画するのには、および<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>プロパティを指す、<xref:System.Drawing.Graphics>オブジェクト。 内のクラス、<xref:System.Drawing?displayProperty=nameWithType>名前空間は、管理の機能へのアクセスを提供するクラスを[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、新しい Windows グラフィックス ライブラリ。 <xref:System.Drawing.Graphics>オブジェクト ポイント、文字列、線、円弧、省略記号、およびその他の多数の図形を描画するメソッドがあります。  
  
 コントロールを呼び出すその<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド ビジュアル表示を変更する必要があるたびにします。 このメソッドが生成されます、<xref:System.Windows.Forms.Control.Paint>イベント。  
  
## <a name="see-also"></a>関連項目

- [イベント](../../../standard/events/index.md)
- [Windows フォーム コントロールのレンダリング](rendering-a-windows-forms-control.md)
- [イベントの定義](defining-an-event-in-windows-forms-controls.md)
