---
title: '方法: 描画する Graphics オブジェクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 79eae4d37c056fc95ac73c78e00dd1a2b68bcd24
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324202"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>方法: 描画する Graphics オブジェクトを作成する
直線と図形を描画することができます、前に、テキストのレンダリングまたは表示し、操作を使用したイメージ[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、作成する必要がある、<xref:System.Drawing.Graphics>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトが表す、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]描画面、およびグラフィカル イメージを作成するために使用するオブジェクトです。  
  
 グラフィックスを操作には、2 つの手順があります。  
  
1. 作成、<xref:System.Drawing.Graphics>オブジェクト。  
  
2. 使用して、<xref:System.Drawing.Graphics>直線と図形の描画、テキストのレンダリングまたは表示、およびイメージを操作するオブジェクト。  
  
## <a name="creating-a-graphics-object"></a>グラフィックス オブジェクトを作成します。  
 グラフィックス オブジェクトは、さまざまな方法で作成できます。  
  
#### <a name="to-create-a-graphics-object"></a>グラフィックス オブジェクトを作成するには  
  
-   一部として、グラフィックス オブジェクトへの参照を受け取る、<xref:System.Windows.Forms.PaintEventArgs>で、<xref:System.Windows.Forms.Control.Paint>フォームまたはコントロールのイベント。 これは、グラフィックス オブジェクトへの参照を取得する方法、コントロールの描画コードを作成するときに、通常は。 同様に、取得することも、グラフィックス オブジェクトのプロパティとして、<xref:System.Drawing.Printing.PrintPageEventArgs>処理するときに、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベントを<xref:System.Drawing.Printing.PrintDocument>します。  
  
     - または -  
  
-   呼び出す、<xref:System.Windows.Forms.Control.CreateGraphics%2A>コントロールまたはフォームへの参照を取得する方法、<xref:System.Drawing.Graphics>コントロールまたはフォームの描画サーフェイスを表すオブジェクト。 フォームまたは既に存在しているコントロールを描画する場合は、このメソッドを使用します。  
  
     - または -  
  
-   作成、<xref:System.Drawing.Graphics>オブジェクトから継承する任意のオブジェクトから<xref:System.Drawing.Image>します。 この方法は、既存のイメージを変更するときに便利です。  
  
     次のセクションでは、これらの各プロセスの詳細を提供します。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>ペイントのイベント ハンドラーで PaintEventArgs  
 プログラミングを行う際、<xref:System.Windows.Forms.PaintEventHandler>コントロールまたは<xref:System.Drawing.Printing.PrintDocument.PrintPage>の<xref:System.Drawing.Printing.PrintDocument>、グラフィックス オブジェクトは、いずれかのプロパティとして提供されます<xref:System.Windows.Forms.PaintEventArgs>または<xref:System.Drawing.Printing.PrintPageEventArgs>します。  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>描画イベントで PaintEventArgs からグラフィックス オブジェクトへの参照を取得するには  
  
1. 宣言、<xref:System.Drawing.Graphics>オブジェクト。  
  
2. 参照する変数を割り当てる、<xref:System.Drawing.Graphics>の一部として渡されたオブジェクト、<xref:System.Windows.Forms.PaintEventArgs>します。  
  
3. フォームまたはコントロールを描画するコードを挿入します。  
  
     次の例を参照する方法を示しています、<xref:System.Drawing.Graphics>オブジェクトから、<xref:System.Windows.Forms.PaintEventArgs>で、<xref:System.Windows.Forms.Control.Paint>イベント。  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,   
       System.Windows.Forms.PaintEventArgs pe)   
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a>CreateGraphics メソッド  
 使用することも、<xref:System.Windows.Forms.Control.CreateGraphics%2A>コントロールまたはフォームへの参照を取得する方法、<xref:System.Drawing.Graphics>コントロールまたはフォームの描画サーフェイスを表すオブジェクト。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics メソッドを使用して、グラフィックス オブジェクトを作成するには  
  
-   呼び出す、<xref:System.Windows.Forms.Control.CreateGraphics%2A>なるグラフィックスをレンダリングするフォームまたはコントロールのメソッド。  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a>イメージ オブジェクトから作成します。  
 さらから派生した任意のオブジェクトから graphics オブジェクトを作成することができます、<xref:System.Drawing.Image>クラス。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>イメージから Graphics オブジェクトを作成するには  
  
-   呼び出す、<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>メソッドを作成したいイメージの変数の名前を指定して、<xref:System.Drawing.Graphics>オブジェクト。  
  
     次の例は、使用する方法を示します、<xref:System.Drawing.Bitmap>オブジェクト。  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and   
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
>  作成できるだけ<xref:System.Drawing.Graphics>16、24 ビットおよび 32 ビットの .bmp ファイルなど、インデックスなしの .bmp ファイルからオブジェクト。 インデックスなしの .bmp ファイルの各ピクセルは、カラー テーブルにインデックスを保持するインデックス付きの .bmp ファイルのピクセルとは異なり、色を保持します。  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>描画と図形と画像の操作  
 作成した後、<xref:System.Drawing.Graphics>オブジェクトは、直線と図形の描画、テキストのレンダリングまたは表示、およびイメージを操作するために使用可能性があります。 使用されるプリンシパルのオブジェクト、<xref:System.Drawing.Graphics>オブジェクトには。  
  
-   <xref:System.Drawing.Pen>クラス: 線を描画、図形のアウトラインまたは他の幾何学的表現のレンダリングに使用します。  
  
-   <xref:System.Drawing.Brush>クラス、塗りつぶされた図形、イメージ、テキストなどのグラフィックスの領域を塗りつぶすときのために使用します。  
  
-   <xref:System.Drawing.Font>クラス-テキストのレンダリング時に使用する図形の内容の説明を提供します。  
  
-   <xref:System.Drawing.Color>構造体などを表示するさまざまな色を表します。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>作成したグラフィック オブジェクトを使用するには  
  
-   必要なものを描画するために上記の適切なオブジェクトを使用します。  
  
     詳細については、次のトピックを参照してください。  
  
    |表示するには|参照トピック|  
    |---------------|---------|  
    |線|[方法: Windows フォームに直線を描画します。](how-to-draw-a-line-on-a-windows-form.md)|  
    |図形|[方法: 形状のアウトラインを描画します。](how-to-draw-an-outlined-shape.md)|  
    |テキスト|[方法: Windows フォーム上のテキストの描画](how-to-draw-text-on-a-windows-form.md)|  
    |イメージ|[方法: GDI + を使用したイメージをレンダリングします。](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>関連項目

- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [方法: GDI + を使用したイメージをレンダリングします。](how-to-render-images-with-gdi.md)
