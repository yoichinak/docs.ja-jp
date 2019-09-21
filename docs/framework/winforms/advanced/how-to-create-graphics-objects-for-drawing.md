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
ms.openlocfilehash: 3d3ab62896f6b799cd38a8180b90f33125a9929b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964340"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>方法: 描画する Graphics オブジェクトを作成する
Gdi + を使用して、線や形状の描画、テキストのレンダリング、イメージの表示と操作を行う<xref:System.Drawing.Graphics>には、オブジェクトを作成する必要があります。 オブジェクト<xref:System.Drawing.Graphics>は gdi + の描画サーフェイスを表し、はグラフィックイメージを作成するために使用されるオブジェクトです。  
  
 グラフィックスを操作するには、次の2つの手順を実行します。  
  
1. オブジェクトを<xref:System.Drawing.Graphics>作成しています。  
  
2. <xref:System.Drawing.Graphics>オブジェクトを使用して、線と形状を描画したり、テキストを表示したり、イメージを表示および操作したりします。  
  
## <a name="creating-a-graphics-object"></a>グラフィックスオブジェクトの作成  
 グラフィックスオブジェクトは、さまざまな方法で作成できます。  
  
#### <a name="to-create-a-graphics-object"></a>グラフィックスオブジェクトを作成するには  
  
- フォームまたはコントロールの<xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint>イベントで、の一部としてグラフィックスオブジェクトへの参照を受け取ります。 これは、通常、コントロールの描画コードを作成するときに、グラフィックスオブジェクトへの参照を取得する方法です。 同様に、の<xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント<xref:System.Drawing.Printing.PrintDocument>を処理するときに、グラフィックスオブジェクトをのプロパティとして取得することもできます。  
  
     \- または -  
  
- コントロールまたはフォームの<xref:System.Drawing.Graphics> メソッドを呼び出して、そのコントロールまたはフォームの描画サーフェイスを表すオブジェクトへの参照を取得します。<xref:System.Windows.Forms.Control.CreateGraphics%2A> 既に存在するフォームまたはコントロールに描画する場合は、このメソッドを使用します。  
  
     \- または -  
  
- <xref:System.Drawing.Graphics> を<xref:System.Drawing.Image>継承する任意のオブジェクトからオブジェクトを作成します。 この方法は、既存のイメージを変更する場合に便利です。  
  
     次のセクションでは、これらの各プロセスについて詳しく説明します。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>描画イベントハンドラーの PaintEventArgs  
 コントロール<xref:System.Windows.Forms.PaintEventHandler> <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>またはのをプログラミングする場合、グラフィックスオブジェクトはまたはのプロパティの1つとして提供されます。 <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>描画イベントの PaintEventArgs からグラフィックスオブジェクトへの参照を取得するには  
  
1. オブジェクトを<xref:System.Drawing.Graphics>宣言します。  
  
2. 変数を割り当てて、 <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs>の一部として渡されたオブジェクトを参照します。  
  
3. フォームまたはコントロールを描画するためのコードを挿入します。  
  
     次の例は、 <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.Control.Paint>イベント<xref:System.Windows.Forms.PaintEventArgs>でからオブジェクトを参照する方法を示しています。  
  
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
 また、コントロールまたは<xref:System.Windows.Forms.Control.CreateGraphics%2A>フォームのメソッドを使用して、そのコントロールまたは<xref:System.Drawing.Graphics>フォームの描画サーフェイスを表すオブジェクトへの参照を取得することもできます。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics メソッドを使用してグラフィックスオブジェクトを作成するには  
  
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
  
## <a name="create-from-an-image-object"></a>イメージオブジェクトから作成する  
 さらに、 <xref:System.Drawing.Image>クラスから派生した任意のオブジェクトからグラフィックスオブジェクトを作成することもできます。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>イメージからグラフィックスオブジェクトを作成するには  
  
- オブジェクト<xref:System.Drawing.Graphics>を<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>作成するイメージ変数の名前を指定して、メソッドを呼び出します。  
  
     次の例は、オブジェクトの<xref:System.Drawing.Bitmap>使用方法を示しています。  
  
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
> オブジェクトを作成<xref:System.Drawing.Graphics>できるのは、16ビット、24ビット、32ビットの .bmp ファイルなど、インデックスのない .bmp ファイルのオブジェクトだけです。 インデックス付けされていない .bmp ファイルの各ピクセルには、カラーテーブルのインデックスを保持するインデックス付き .bmp ファイルのピクセルとは対照的に、色が保持されます。  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>図形とイメージの描画と操作  
 オブジェクトを作成した後<xref:System.Drawing.Graphics> 、オブジェクトを使用して、線や図形の描画、テキストの表示、画像の表示と操作を行うことができます。 <xref:System.Drawing.Graphics>オブジェクトで使用されるプリンシパルオブジェクトは次のとおりです。  
  
- <xref:System.Drawing.Pen>クラス。線の描画、図形のアウトライン表示、またはその他の幾何学的表現のレンダリングに使用されます。  
  
- 塗り<xref:System.Drawing.Brush>つぶされた図形、画像、テキストなど、グラフィックスの領域を塗りつぶすために使用されるクラス。  
  
- <xref:System.Drawing.Font>クラス: テキストを表示するときに使用する図形の説明を提供します。  
  
- 構造<xref:System.Drawing.Color>体は、表示するさまざまな色を表します。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>作成したグラフィックスオブジェクトを使用するには  
  
- 上記の適切なオブジェクトを使用して、必要なものを描画します。  
  
     詳細については、次のトピックを参照してください。  
  
    |レンダリングするには|解決方法|  
    |---------------|---------|  
    |線|[方法: Windows フォーム上に線を描画する](how-to-draw-a-line-on-a-windows-form.md)|  
    |図形|[方法: 輪郭付きの図形を描画する](how-to-draw-an-outlined-shape.md)|  
    |テキスト|[方法: Windows フォームでのテキストの描画](how-to-draw-text-on-a-windows-form.md)|  
    |画像|[方法: GDI + を使用したイメージのレンダリング](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>関連項目

- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [方法: GDI + を使用したイメージのレンダリング](how-to-render-images-with-gdi.md)
