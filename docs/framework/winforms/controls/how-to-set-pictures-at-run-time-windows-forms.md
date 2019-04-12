---
title: '方法: (Windows フォーム) の実行時にピクチャを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: 8ed3ba9050a9117a53b5f4f1cccd26381f55ab32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073599"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>方法: (Windows フォーム) の実行時にピクチャを設定します。
Windows フォームが表示されるイメージをプログラムで設定できる<xref:System.Windows.Forms.PictureBox>コントロール。  
  
### <a name="to-set-a-picture-programmatically"></a>画像をプログラムで設定するには  
  
-   設定、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティを使用して、<xref:System.Drawing.Image.FromFile%2A>のメソッド、<xref:System.Drawing.Image>クラス。  
  
     次の例では、イメージの場所に設定されているパスは、My Documents フォルダーです。 これは、Windows オペレーティング システムを実行しているほとんどのコンピューターにはでこのディレクトリが含まれていると想定できます。 また、このようにすることで、最小限のシステム アクセス レベルしか持たないユーザーもアプリケーションを安全に実行できるようになります。 次の例でフォームを前提としています、<xref:System.Windows.Forms.PictureBox>コントロールが既に追加されています。  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>グラフィックをクリアするには  
  
-   最初に、イメージで使用されているメモリを解放し、グラフィックをオフにします。 メモリ管理が問題になる場合は、ガベージ コレクションがメモリを後で解放されます。  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  使用する必要があります理由の詳細については、<xref:System.Drawing.Image.Dispose%2A>この方法でメソッドを参照してください[アンマネージ リソースのクリーンアップ](../../../standard/garbage-collection/unmanaged.md)します。  
  
     グラフィックは、デザイン時に、コントロールに読み込まれた場合でも、このコードは、イメージにクリアされます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox コントロールの概要 (Windows フォーム)](picturebox-control-overview-windows-forms.md)
- [方法: デザイナーを使用してピクチャを読み込む](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [方法: 実行時にピクチャのサイズまたは配置を変更する](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox コントロール](picturebox-control-windows-forms.md)
