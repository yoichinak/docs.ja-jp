---
title: '方法: GDI+ を使用してイメージをレンダリングする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: cb43536f941ea7a6e1a48e78046089636360eef5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079449"
---
# <a name="how-to-render-images-with-gdi"></a>方法: GDI+ を使用してイメージをレンダリングする
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用すると、アプリケーションにファイルとして存在するイメージをレンダリングできます。 新しいオブジェクトを作成してこれを行う、<xref:System.Drawing.Image>クラス (など<xref:System.Drawing.Bitmap>)、作成、 <xref:System.Drawing.Graphics> 、使用する描画サーフェイスへの参照オブジェクトし、呼び出し、<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。 イメージは、グラフィックス クラスで表される描画サーフェイス上に描画されます。 イメージ エディターを使用して、デザイン時にイメージ ファイルを作成および編集し、実行時に [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用してレンダリングできます。 詳細については、「[アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)」を参照してください。  
  
### <a name="to-render-an-image-with-gdi"></a>GDI + を使用してイメージをレンダリングするには  
  
1.  表示するイメージを表すオブジェクトを作成します。 このオブジェクトから継承するクラスのメンバーである必要があります<xref:System.Drawing.Image>など<xref:System.Drawing.Bitmap>または<xref:System.Drawing.Imaging.Metafile>します。 次に例を示します。  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the   
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2.  作成、<xref:System.Drawing.Graphics>を使用する描画サーフェイスを表すオブジェクト。 詳細については、「[方法 :描画の Graphics オブジェクトを作成](how-to-create-graphics-objects-for-drawing.md)です。  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of   
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3.  呼び出す、<xref:System.Drawing.Graphics.DrawImage%2A>のイメージを表示するために、グラフィックス オブジェクト。 描画対象のイメージとイメージを描画する場所の座標を指定する必要があります。  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>関連項目

- [グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)
- [方法: 描画する Graphics オブジェクトを作成する](how-to-create-graphics-objects-for-drawing.md)
- [GDI+ でのペン、直線、および四角形](pens-lines-and-rectangles-in-gdi.md)
- [方法: Windows フォームにテキストを描画する](how-to-draw-text-on-a-windows-form.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [線または閉じた図形の描画](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)
