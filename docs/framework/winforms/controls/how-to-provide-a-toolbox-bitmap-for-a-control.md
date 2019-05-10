---
title: '方法: コントロールにツールボックス ビットマップを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 7c26e00acd4278ced53ad29c748ac076e0215a23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913212"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>方法: コントロールにツールボックス ビットマップを指定する
コントロールの特別なアイコンを**ツールボックス**に表示させたい場合は、<xref:System.Drawing.ToolboxBitmapAttribute>を使用して特定のイメージを指定できます。 このクラスは"*属性*"であり、他のクラスに追加できる特殊なクラスです。 属性の詳細については、[属性の概要 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)(Visual basic)  または、[属性 (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) (C#) を参照してください。  
  
 使用して、 <xref:System.Drawing.ToolboxBitmapAttribute>16 で 16 ピクセルのビットマップのパスとファイル名を示す文字列を指定することができます。 コントロールを**ツールボックス**に追加すると、このビットマップがコントロールの横に表示されます。 指定することも、 <xref:System.Type>、その種類に関連付けられたビットマップが読み込まれる場合。 両方を指定する場合、<xref:System.Type>文字列、コントロールのイメージ リソースを検索で指定された型を含むアセンブリの文字列パラメーターで指定された名前と、<xref:System.Type>パラメーター。  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>コントロールのツールボックス ビットマップを指定するには  
  
1. <xref:System.Drawing.ToolboxBitmapAttribute>を、コントロールのクラス宣言の Visual Basic の `Class`キーワードの前、および Visual C# のクラス宣言の上に追加します。  
  
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
  
2. プロジェクトをリビルドします。  
  
    > [!NOTE]
    >  ビットマップは、自動生成されたコントロールとコンポーネントのツールボックスには表示されません。 ビットマップを表示するには、**[ツールボックス アイテムの選択]** ダイアログ ボックスを使用してコントロールを再読み込みします。 詳細については、「[チュートリアル:カスタム コンポーネントでツールボックスが自動的に入力](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [チュートリアル: カスタム コンポーネントでツールボックスが自動的に入力](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [デザイン時の Windows フォーム コントロールの開発](developing-windows-forms-controls-at-design-time.md)
- [属性の概要 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [属性 (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
