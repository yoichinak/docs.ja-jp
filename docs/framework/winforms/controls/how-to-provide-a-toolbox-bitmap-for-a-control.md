---
title: '方法: コントロールにツールボックス ビットマップを指定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 9072f96bd6e3485e759ed72819229b3f0c33d641
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715959"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>方法: コントロールにツールボックス ビットマップを指定します。
コントロールの特別なアイコンを表示する場合、**ツールボックス**、特定のイメージを使用して指定することができます、<xref:System.Drawing.ToolboxBitmapAttribute>します。 このクラスは "*属性*" であり、他のクラスに追加できる特殊なクラスです。 属性の詳細については、次を参照してください。[属性の概要 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) Visual basic または[属性 (c#)](../../../csharp/programming-guide/concepts/attributes/index.md) (C#)。  
  
 使用して、 <xref:System.Drawing.ToolboxBitmapAttribute>16 で 16 ピクセルのビットマップのパスとファイル名を示す文字列を指定することができます。 コントロールを**ツールボックス**に追加すると、このビットマップがコントロールの横に表示されます。 指定することも、 <xref:System.Type>、その種類に関連付けられたビットマップが読み込まれる場合。 両方を指定する場合、<xref:System.Type>文字列、コントロールのイメージ リソースを検索で指定された型を含むアセンブリの文字列パラメーターで指定された名前と、<xref:System.Type>パラメーター。  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>コントロールのツールボックス ビットマップを指定するには  
  
1.  追加、<xref:System.Drawing.ToolboxBitmapAttribute>前に、コントロールのクラス宣言に、 `Class` visual Basic、および Visual c# のクラスの宣言の上のキーワード。  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  プロジェクトをリビルドします。  
  
    > [!NOTE]
    >  ビットマップは、自動生成されたコントロールとコンポーネントのツールボックスには表示されません。 ビットマップを表示するには、**[ツールボックス アイテムの選択]** ダイアログ ボックスを使用してコントロールを再読み込みします。 詳細については、「[チュートリアル:カスタム コンポーネントでツールボックスが自動的に入力](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [チュートリアル: カスタム コンポーネントでツールボックスが自動的に入力](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [デザイン時の Windows フォーム コントロールの開発](developing-windows-forms-controls-at-design-time.md)
- [属性の概要 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [属性 (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
