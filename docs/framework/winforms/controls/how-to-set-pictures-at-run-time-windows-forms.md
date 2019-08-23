---
title: '方法: 実行時に画像を設定する (Windows フォーム)'
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
ms.openlocfilehash: 99d78a275c8ad8f55d9b0832a794545b65da7e20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917528"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>方法: 実行時に画像を設定する (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.PictureBox>コントロールによって表示されるイメージをプログラムで設定できます。  
  
### <a name="to-set-a-picture-programmatically"></a>プログラムによって画像を設定するには  
  
- クラスの<xref:System.Drawing.Image.FromFile%2A> <xref:System.Windows.Forms.PictureBox.Image%2A> メソッドを使用して、プロパティを設定します<xref:System.Drawing.Image> 。  
  
     次の例では、イメージの場所に設定されたパスが [マイドキュメント] フォルダーです。 これは、Windows オペレーティングシステムを実行しているほとんどのコンピューターにこのディレクトリが含まれると想定できるためです。 また、このようにすることで、最小限のシステム アクセス レベルしか持たないユーザーもアプリケーションを安全に実行できるようになります。 次の例では、フォームに<xref:System.Windows.Forms.PictureBox>コントロールが既に追加されていることを前提としています。  
  
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
  
- まず、イメージによって使用されているメモリを解放し、グラフィックをクリアします。 ガベージコレクションでは、メモリ管理が問題になると、メモリが解放されます。  
  
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
    > この方法で<xref:System.Drawing.Image.Dispose%2A>メソッドを使用する理由の詳細については、「[アンマネージリソースのクリーンアップ](../../../standard/garbage-collection/unmanaged.md)」を参照してください。  
  
     このコードは、デザイン時にグラフィックがコントロールに読み込まれた場合でも、イメージをクリアします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox コントロールの概要](picturebox-control-overview-windows-forms.md)
- [方法: デザイナーを使用して画像を読み込む](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [方法: 実行時に画像のサイズまたは配置を変更する](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox コントロール](picturebox-control-windows-forms.md)
