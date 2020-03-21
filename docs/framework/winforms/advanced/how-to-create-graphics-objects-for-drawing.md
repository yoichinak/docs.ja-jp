---
title: '方法 : 描画する Graphics オブジェクトを作成する'
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
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142434"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>方法 : 描画する Graphics オブジェクトを作成する
線や図形の描画、テキストのレンダリング、GDI+ を使用したイメージの表示と操作を行うには、<xref:System.Drawing.Graphics>オブジェクトを作成する必要があります。 オブジェクト<xref:System.Drawing.Graphics>は GDI+ 描画サーフェイスを表し、グラフィック イメージの作成に使用されるオブジェクトです。  
  
 グラフィックスを操作するには、次の 2 つの手順があります。  
  
1. オブジェクトを<xref:System.Drawing.Graphics>作成する。  
  
2. オブジェクトを<xref:System.Drawing.Graphics>使用して、線や図形の描画、テキストのレンダリング、またはイメージの表示と操作を行います。  
  
## <a name="creating-a-graphics-object"></a>グラフィックス オブジェクトの作成  
 グラフィックス オブジェクトは、さまざまな方法で作成できます。  
  
#### <a name="to-create-a-graphics-object"></a>グラフィックス オブジェクトを作成するには  
  
- フォームまたはコントロールの<xref:System.Windows.Forms.PaintEventArgs><xref:System.Windows.Forms.Control.Paint>イベントの一部として、グラフィックス オブジェクトへの参照を受け取ります。 これは通常、コントロールの描画コードを作成するときに、グラフィックス オブジェクトへの参照を取得する方法です。 同様に、イベントを処理<xref:System.Drawing.Printing.PrintPageEventArgs>するときに、グラフィックス オブジェクトを<xref:System.Drawing.Printing.PrintDocument.PrintPage>プロパティとして取得することもできます。 <xref:System.Drawing.Printing.PrintDocument>  
  
     または  
  
- コントロールまたは<xref:System.Windows.Forms.Control.CreateGraphics%2A>フォームの描画サーフェイスを表すオブジェクトへの参照を<xref:System.Drawing.Graphics>取得するには、コントロールまたはフォームのメソッドを呼び出します。 このメソッドは、既に存在するフォームまたはコントロールに描画する場合に使用します。  
  
     または  
  
- から<xref:System.Drawing.Image>継承<xref:System.Drawing.Graphics>するオブジェクトからオブジェクトを作成します。 この方法は、既存のイメージを変更する場合に便利です。  
  
     以下のセクションでは、これらの各プロセスについて詳しく説明します。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>ペイント イベント ハンドラーのペイント イベント引数  
 for コントロールまたは<xref:System.Windows.Forms.PaintEventHandler><xref:System.Drawing.Printing.PrintDocument.PrintPage>の をプログラミングする<xref:System.Drawing.Printing.PrintDocument>場合は、 または のプロパティ<xref:System.Windows.Forms.PaintEventArgs>の 1 つとして<xref:System.Drawing.Printing.PrintPageEventArgs>グラフィックス オブジェクトが提供されます。  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>ペイント イベントのペイント イベント引数からグラフィックス オブジェクトへの参照を取得するには  
  
1. オブジェクトを<xref:System.Drawing.Graphics>宣言します。  
  
2. の一部として渡される<xref:System.Drawing.Graphics>オブジェクトを参照する変数を<xref:System.Windows.Forms.PaintEventArgs>割り当てます。  
  
3. フォームまたはコントロールを描画するコードを挿入します。  
  
     次の例は、イベント<xref:System.Drawing.Graphics><xref:System.Windows.Forms.PaintEventArgs>内の オブジェクトを参照する<xref:System.Windows.Forms.Control.Paint>方法を示しています。  
  
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
  
## <a name="creategraphics-method"></a>グラフィックス メソッドの作成  
 コントロールまたはフォームのメソッド<xref:System.Windows.Forms.Control.CreateGraphics%2A>を使用して、そのコントロールまたはフォームの描画サーフェイス<xref:System.Drawing.Graphics>を表すオブジェクトへの参照を取得することもできます。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics メソッドを使用してグラフィックス オブジェクトを作成するには  
  
- グラフィックスを<xref:System.Windows.Forms.Control.CreateGraphics%2A>レンダリングするフォームまたはコントロールのメソッドを呼び出します。  
  
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
  
## <a name="create-from-an-image-object"></a>イメージ オブジェクトから作成  
 また、クラスから派生する任意のオブジェクトからグラフィックス オブジェクトを<xref:System.Drawing.Image>作成できます。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>イメージからグラフィックス オブジェクトを作成するには  
  
- オブジェクトを<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>作成する Image 変数の名前を指定して、メソッドを<xref:System.Drawing.Graphics>呼び出します。  
  
     次の例は、オブジェクトの使用方法<xref:System.Drawing.Bitmap>を示しています。  
  
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
> 16 ビット<xref:System.Drawing.Graphics>、24 ビット、32 ビットの .bmp ファイルなど、インデックスを作成していない .bmp ファイルからのみオブジェクトを作成できます。 インデックスが作成されていない .bmp ファイルの各ピクセルは、カラー テーブルへのインデックスを保持するインデックス付きの .bmp ファイルのピクセルとは対照的に、色を保持します。  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>図形とイメージの描画と操作  
 作成後、オブジェクトを<xref:System.Drawing.Graphics>使用して、線やシェイプの描画、テキストのレンダリング、イメージの表示と操作を行うことができます。 <xref:System.Drawing.Graphics>オブジェクトで使用される主なオブジェクトは次のとおりです。  
  
- クラス<xref:System.Drawing.Pen>- 線の描画、シェイプのアウトライン表示、その他のジオメトリ表現のレンダリングに使用されます。  
  
- クラス<xref:System.Drawing.Brush>- 塗りつぶされた図形、イメージ、テキストなどのグラフィックス領域を塗りつぶす場合に使用します。  
  
- クラス<xref:System.Drawing.Font>- テキストをレンダリングするときに使用する図形の説明を提供します。  
  
- 構造<xref:System.Drawing.Color>- 表示するさまざまな色を表します。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>作成した Graphics オブジェクトを使用するには  
  
- 上記の適切なオブジェクトを使用して、必要なものを描画します。  
  
     詳細については、次のトピックを参照してください。  
  
    |レンダリングするには|参照先|  
    |---------------|---------|  
    |路線|[方法 : Windows フォームに直線を描画する](how-to-draw-a-line-on-a-windows-form.md)|  
    |図形|[方法 : 形状のアウトラインを描画する](how-to-draw-an-outlined-shape.md)|  
    |Text|[方法 : Windows フォームにテキストを描画する](how-to-draw-text-on-a-windows-form.md)|  
    |イメージ|[方法 : GDI+ を使用してイメージをレンダリングする](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>関連項目

- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [方法 : GDI+ を使用してイメージをレンダリングする](how-to-render-images-with-gdi.md)
