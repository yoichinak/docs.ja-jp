---
title: パネルの背景を設定する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: 36e552475334c25b9d5a6fafb82155c6ebcba266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182105"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>方法 : Windows フォーム パネルの背景を設定する
Windows フォーム<xref:System.Windows.Forms.Panel>コントロールでは、背景色と背景イメージの両方を表示できます。 この<xref:System.Windows.Forms.Control.BackColor%2A>プロパティは、ラベルやラジオ ボタンなど、含まれているコントロールの背景色を設定します。 このプロパティ<xref:System.Windows.Forms.Control.BackgroundImage%2A>が設定されていない場合、<xref:System.Windows.Forms.Control.BackColor%2A>選択範囲はパネル全体に表示されます。 プロパティが<xref:System.Windows.Forms.Control.BackgroundImage%2A>設定されている場合、含まれているコントロールの背後にイメージが表示されます。  
  
### <a name="to-set-the-background-programmatically"></a>プログラムで背景を設定するには  
  
1. パネルの<xref:System.Windows.Forms.Control.BackColor%2A>プロパティを type<xref:System.Drawing.Color?displayProperty=nameWithType>の値に設定します。  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. クラスのメソッドを使用<xref:System.Windows.Forms.Control.BackgroundImage%2A>して、パネル<xref:System.Drawing.Image.FromFile%2A>のプロパティを<xref:System.Drawing.Image?displayProperty=nameWithType>設定します。  
  
    ```vb  
    ' You should replace the bolded image
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel コントロール](panel-control-windows-forms.md)
- [Panel コントロールの概要](panel-control-overview-windows-forms.md)
