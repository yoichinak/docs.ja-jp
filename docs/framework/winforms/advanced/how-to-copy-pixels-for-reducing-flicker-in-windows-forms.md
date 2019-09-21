---
title: '方法: ピクセルをコピーして Windows フォームのちらつきを低減する'
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
ms.openlocfilehash: 5a18539153c64a5059d8079f6e245115b026bb91
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950147"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>方法: ピクセルをコピーして Windows フォームのちらつきを低減する
単純なグラフィックをアニメーション化すると、ユーザーがちらつきやその他の望ましくない視覚効果を発生することがあります。 この問題を制限する1つの方法は、グラフィックで "bitblt" プロセスを使用することです。 Bitblt は、原点の四角形からピクセルの移動先の四角形までのカラーデータの "ビットブロック転送" です。  
  
 Windows フォームでは、bitblt は<xref:System.Drawing.Graphics.CopyFromScreen%2A> <xref:System.Drawing.Graphics>クラスのメソッドを使用して実行されます。 メソッドのパラメーターでは、ソースとターゲット (ポイント)、コピーする領域のサイズ、および新しい図形の描画に使用するグラフィックスオブジェクトを指定します。  
  
 次の例では、 <xref:System.Windows.Forms.Control.Paint>イベントハンドラーのフォームに図形が描画されます。 次に、メソッドを使用して図形を複製します。 <xref:System.Drawing.Graphics.CopyFromScreen%2A>  
  
> [!NOTE]
> フォームの<xref:System.Windows.Forms.Control.DoubleBuffered%2A>プロパティをに設定`true`すると、 <xref:System.Windows.Forms.Control.Paint>イベント内のグラフィックスベースのコードがダブルバッファーされるようになります。 以下のコードを使用すると、これによって認識できないパフォーマンスが向上することはありませんが、より複雑なグラフィックス操作コードを使用する場合は注意が必要です。  
  
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
 上記のコードはフォームの<xref:System.Windows.Forms.Control.Paint>イベントハンドラーで実行されるため、フォームが再描画されたときにグラフィックスが保持されます。 そのため、 <xref:System.Windows.Forms.Form.Load>イベントハンドラーでグラフィックス関連のメソッドを呼び出さないでください。フォームのサイズが変更されたり、別の形式によって隠されたりした場合、描画コンテンツは再描画されません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [ペンを使用した直線と図形の描画](using-a-pen-to-draw-lines-and-shapes.md)
