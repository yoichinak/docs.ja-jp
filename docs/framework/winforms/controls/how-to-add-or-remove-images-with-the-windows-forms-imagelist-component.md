---
title: '方法: Windows フォームの ImageList コンポーネントにイメージを追加または削除する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: 430b7f573b115c21b9e2fa87f0ace74205717285
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925118"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>方法: Windows フォームの ImageList コンポーネントにイメージを追加または削除する
Windows フォーム<xref:System.Windows.Forms.ImageList>コンポーネントには、通常、コントロールに関連付けられる前にイメージが設定されます。 ただし、イメージリストをコントロールに関連付けた後に、イメージの追加や削除を行うことができます。  
  
> [!NOTE]
> イメージを削除する場合は、関連<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>付けられているコントロールのプロパティが有効であることを確認します。  
  
### <a name="to-add-images-programmatically"></a>プログラムによってイメージを追加するには  
  
- イメージリストの<xref:System.Windows.Forms.ImageList.Images%2A>プロパティのメソッドを使用します。<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>  
  
     次のコード例では、イメージの場所に設定されたパスが **[マイドキュメント**] フォルダーです。 この場所は、Windows オペレーティングシステムを実行しているほとんどのコンピューターにこのフォルダーを含めることを前提としているために使用されます。 また、この場所を選択すると、システムアクセスレベルを最小限にしたユーザーがアプリケーションをより安全に実行できるようになります。 次のコード例では、 <xref:System.Windows.Forms.ImageList>コントロールが既に追加されているフォームが必要です。  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a>キー値を使用してイメージを追加します。  
  
- キー値を受け取る<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>イメージリストの<xref:System.Windows.Forms.ImageList.Images%2A>プロパティのメソッドのいずれかを使用します。  
  
     次のコード例では、イメージの場所に設定されたパスが **[マイドキュメント**] フォルダーです。 この場所は、Windows オペレーティングシステムを実行しているほとんどのコンピューターにこのフォルダーを含めることを前提としているために使用されます。 また、この場所を選択すると、システムアクセスレベルを最小限にしたユーザーがアプリケーションをより安全に実行できるようになります。 次のコード例では、 <xref:System.Windows.Forms.ImageList>コントロールが既に追加されているフォームが必要です。  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
### <a name="to-remove-all-images-programmatically"></a>プログラムによってすべてのイメージを削除するには  
  
- 1つ<xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>のイメージを削除するには、メソッドを使用します。  
  
     、-または-  
  
     イメージリスト<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>内のすべてのイメージをクリアするには、メソッドを使用します。  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a>キーによってイメージを削除するには  
  
- キーに<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>よって1つのイメージを削除するには、メソッドを使用します。  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>関連項目

- [ImageList コンポーネント](imagelist-component-windows-forms.md)
- [ImageList コンポーネントの概要](imagelist-component-overview-windows-forms.md)
- [イメージ、ビットマップ、メタファイル](../advanced/images-bitmaps-and-metafiles.md)
