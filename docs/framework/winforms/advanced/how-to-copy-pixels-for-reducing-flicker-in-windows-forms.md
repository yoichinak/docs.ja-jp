---
title: '方法: ピクセルをコピーして Windows フォームのちらつきを低減します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
ms.openlocfilehash: d03a9b79dc2c0ec61bbafe2ff09b5aba7fffc57b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719248"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>方法: ピクセルをコピーして Windows フォームのちらつきを低減します。
単純なグラフィックをアニメーション化するとユーザーことができます、ちらつき、またはその他の望ましくない視覚効果発生場合があります。 この問題を制限する方法の 1 つでは、グラフィック"bitblt"プロセスを使用します。 Bitblt 関数は、「ビット ブロック転送」カラー データのピクセルの四角形を配信元からのピクセルの四角形に。  
  
 使用して Windows フォーム、bitblt 関数が実行は、<xref:System.Drawing.Graphics.CopyFromScreen%2A>のメソッド、<xref:System.Drawing.Graphics>クラス。 メソッドのパラメーターでは、ソースと宛先 (ポイント単位) として、コピーされる領域のサイズに新しい図形を描画するために使用するグラフィックス オブジェクトを指定します。  
  
 次の例でのフォームの形状を描画、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。 次に、<xref:System.Drawing.Graphics.CopyFromScreen%2A>メソッドを使用して、図形が重複しています。  
  
> [!NOTE]
>  フォームの設定<xref:System.Windows.Forms.Control.DoubleBuffered%2A>プロパティを`true`でグラフィックス ベースのコードになります、<xref:System.Windows.Forms.Control.Paint>ダブル バッファーされたイベントがあります。 認識できるようなパフォーマンス上のメリットは、次のコードを使用するときにこれがないより複雑なグラフィックス操作のコードを使用する場合に留意すべきことです。  
  
## <a name="example"></a>例  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記のコードは、フォームの実行は<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー、フォームが再描画されるときに、グラフィックスが持続するようにします。 そのため、呼び出さないでくださいグラフィックに関連するメソッド、<xref:System.Windows.Forms.Form.Load>イベント ハンドラーでは、フォームのサイズを変更または別の形式によって隠されている場合、描画のコンテンツは描画しないためです。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
