---
title: '方法: Windows フォームの RichTextBox コントロールのフォント属性を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: a6fe5b30c457fae2d53c946092b214f492fe5e9b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331209"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>方法: Windows フォームの RichTextBox コントロールのフォント属性を設定する
Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールが、表示するテキストを書式設定するためのさまざまなオプションです。 行うことができます、選択した文字太字、下線、または斜体などを使用して、<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>プロパティ。 また、このプロパティを使用して、選択した文字のサイズと書体を変更することもできます。 <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>プロパティでは、選択した文字の色を変更することができます。  
  
### <a name="to-change-the-appearance-of-characters"></a>文字の外観を変更するには  
  
1. 設定、<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>プロパティを適切なフォント。  
  
     ユーザーをアプリケーションでフォント ファミリ、サイズ、および書体を設定できるように、通常使用する、<xref:System.Windows.Forms.FontDialog>コンポーネント。 概要については、「[FontDialog コンポーネントの概要 (Windows フォーム)](fontdialog-component-overview-windows-forms.md)」 (FontDialog コンポーネントの概要) を参照してください。  
  
2. 設定、<xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>プロパティを適切な色にします。  
  
     アプリケーションで色を設定するユーザーを有効にするには通常使用、<xref:System.Windows.Forms.ColorDialog>コンポーネント。 概要については、「[ColorDialog コンポーネントの概要 (Windows フォーム)](colordialog-component-overview-windows-forms.md)」 (ColorDialog コンポーネントの概要) を参照してください。  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  これらのプロパティは選択したテキストにのみ影響します。テキストが選択されていない場合は、現在の挿入ポイントの場所に入力されるテキストに影響します。 プログラムでテキストを選択する方法の詳細については、次を参照してください。<xref:System.Windows.Forms.TextBoxBase.Select%2A>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox コントロール](richtextbox-control-windows-forms.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
