---
title: '方法: Windows フォーム コントロールによって表示されるイメージを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 031ddcb3b852e75353fed7420735350e79f23df3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085091"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>方法: Windows フォーム コントロールによって表示されるイメージを設定する
いくつかの Windows フォーム コントロールは、イメージを表示できます。 これらのイメージには、ボタン上のフロッピー ディスク アイコンなど、コントロールの目的を明確にするアイコンがあります、**保存**コマンド。 また、アイコンには、外観と動作を制御するための背景イメージもあります。  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>コントロールによって表示されるイメージを設定するには  
  
1.  コントロールの設定`Image`または`BackgroundImage`プロパティ型のオブジェクトを<xref:System.Drawing.Image>します。 一般に、するはから読み込まれるイメージ ファイルを使用して、<xref:System.Drawing.Image.FromFile%2A>メソッド。  
  
     イメージの場所は次のコード例で、パスが設定、**マイ ピクチャ**フォルダー。 Windows オペレーティング システムを実行しているほとんどのコンピューターでは、このディレクトリが含まれます。 これにより、ユーザーは最小限のシステム アクセスのレベルでアプリケーションを安全に実行がもできます。 次のコード例では、既に使用して、フォームが必要です、<xref:System.Windows.Forms.PictureBox>コントロールを追加します。  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
