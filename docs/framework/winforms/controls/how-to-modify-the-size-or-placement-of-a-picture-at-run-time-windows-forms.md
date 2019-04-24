---
title: '方法: 実行時 (Windows フォーム) にサイズまたは画像の配置を変更します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: d0a86d7fe53dba3da6bd63587561f82877bc2f06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328336"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>方法: 実行時 (Windows フォーム) にサイズまたは画像の配置を変更します。
Windows フォームを使用する場合<xref:System.Windows.Forms.PictureBox>コントロール、フォームで設定することができます、<xref:System.Windows.Forms.PictureBox.SizeMode%2A>をプロパティ。  
  
-   コントロールの左上隅で、画像の左上を揃え  
  
-   コントロール内で画像を中央揃え  
  
-   表示の画像に合わせてコントロールのサイズを調整します。  
  
-   コントロールに合わせて、表示される任意の画像を拡大します。  
  
 (特にビットマップ形式の 1 つ) 画像を拡大すると、イメージの品質の損失を生成できます。 実行時にイメージを描画するためのグラフィックス命令リストのメタファイルはストレッチ ビットマップよりも適しています。  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>実行時に、SizeMode プロパティを設定するには  
  
1. 設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>に<xref:System.Windows.Forms.PictureBoxSizeMode.Normal>(既定)、 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>、 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>、または<xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>します。 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> コントロールの左上隅にある; で、イメージが格納されることを意味します。イメージがコントロールよりも大きい場合は、その右下隅、クリッピングされます。 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> イメージがコントロールの中央に配置する方法イメージがコントロールよりも大きい場合は、画像の外側の縁が切り取られます。 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> コントロールのサイズは、イメージのサイズに調整されることを意味します。 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> 逆の場合は、イメージのサイズは、コントロールのサイズに調整されることを意味します。  
  
     次の例では、イメージの場所に設定されているパスは、My Documents フォルダーです。 これは、Windows オペレーティング システムを実行しているほとんどのコンピューターにはでこのディレクトリが含まれていると想定できます。 また、このようにすることで、最小限のシステム アクセス レベルしか持たないユーザーもアプリケーションを安全に実行できるようになります。 次の例でフォームを前提としています、<xref:System.Windows.Forms.PictureBox>コントロールが既に追加されています。  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.PictureBox>
- [方法: デザイナーを使用してピクチャを読み込む.](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox コントロールの概要](picturebox-control-overview-windows-forms.md)
- [方法: 実行時にピクチャを設定します。](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox コントロール](picturebox-control-windows-forms.md)
