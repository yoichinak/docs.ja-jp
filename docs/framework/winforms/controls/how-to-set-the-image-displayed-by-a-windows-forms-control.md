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
ms.openlocfilehash: 99bde4fac7b3057358c7e6a8550efdb4cc351eb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037883"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>方法: Windows フォームコントロールによって表示されるイメージを設定する

いくつかの Windows フォームコントロールでイメージを表示できます。 これらのイメージは、 **[保存]** コマンドを示すボタン上のフロッピーディスクアイコンなど、コントロールの目的を明確にするアイコンにすることができます。 または、アイコンに背景画像を使用して、コントロールの外観と動作を指定することもできます。

## <a name="to-set-the-image-displayed-by-a-control"></a>コントロールによって表示されるイメージを設定するには

1. コントロールの`Image`プロパティまたは`BackgroundImage`プロパティを、型<xref:System.Drawing.Image>のオブジェクトに設定します。 通常は、 <xref:System.Drawing.Image.FromFile%2A>メソッドを使用して、ファイルからイメージを読み込みます。

     次のコード例では、イメージの場所に設定されているパスが **[マイピクチャ**] フォルダーです。 Windows オペレーティングシステムを実行しているほとんどのコンピューターにこのディレクトリが含まれます。 これにより、最小限のシステムアクセスレベルを持つユーザーも、アプリケーションを安全に実行できます。 次のコード例では、 <xref:System.Windows.Forms.PictureBox>コントロールが追加されたフォームが既に存在している必要があります。

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
