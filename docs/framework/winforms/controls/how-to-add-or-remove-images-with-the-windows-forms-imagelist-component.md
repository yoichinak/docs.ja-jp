---
title: '方法: 追加または削除のイメージを Windows フォームの ImageList コンポーネント'
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
ms.openlocfilehash: 81c85186d2f15917a6aa1067814a0119edf3f460
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705169"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>方法: 追加または削除のイメージを Windows フォームの ImageList コンポーネント
Windows フォーム<xref:System.Windows.Forms.ImageList>コンポーネントには通常、イメージ前に、コントロールに関連付けられています。 ただし、追加し、イメージ リスト コントロールとの関連付けの後イメージを削除することができます。  
  
> [!NOTE]
>  イメージを削除するとことを確認します。、<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>の関連付けられたコントロールのプロパティは引き続き有効です。  
  
### <a name="to-add-images-programmatically"></a>プログラムでイメージを追加するには  
  
-   使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>メソッドのイメージ リストの<xref:System.Windows.Forms.ImageList.Images%2A>プロパティ。  
  
     イメージの場所は次のコード例で、パスが設定、 **My Documents**フォルダー。 この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターにはでこのフォルダーが含まれていると想定できるために使用されます。 この場所を選択すると、最小限のシステム アクセス レベル、アプリケーションを安全に実行を持つユーザーもできます。 次のコード例では、使用して、フォームが必要です、<xref:System.Windows.Forms.ImageList>コントロールが既に追加されています。  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>キー値を持つイメージを追加します。  
  
-   いずれかを使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>メソッドのイメージ リストの<xref:System.Windows.Forms.ImageList.Images%2A>キーの値を受け取るプロパティです。  
  
     イメージの場所は次のコード例で、パスが設定、 **My Documents**フォルダー。 この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターにはでこのフォルダーが含まれていると想定できるために使用されます。 この場所を選択すると、最小限のシステム アクセス レベル、アプリケーションを安全に実行を持つユーザーもできます。 次のコード例では、使用して、フォームが必要です、<xref:System.Windows.Forms.ImageList>コントロールが既に追加されています。  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>すべてのイメージをプログラムで削除するには  
  
-   使用して、 <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> 1 つのイメージを削除する方法  
  
     、または、  
  
     使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>イメージ リスト内のすべてのイメージをクリアします。  
  
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
  
### <a name="to-remove-images-by-key"></a>キーによるイメージを削除するには  
  
-   使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>キーで 1 つのイメージを削除する方法。  
  
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
