---
title: '方法: アクティブな MDI 子フォームを特定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 91100b37e4cae9041479b209e40034efe376df5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946216"
---
# <a name="how-to-determine-the-active-mdi-child"></a>方法: アクティブな MDI 子フォームを特定する
場合によっては、現在アクティブな子フォームにフォーカスがあるコントロールを操作するコマンドを用意する必要があります。 たとえば、選択したテキストを子フォームのテキストボックスからクリップボードにコピーするとします。 標準の [編集] メニューの [コピー] メニュー項目の<xref:System.Windows.Forms.Control.Click>イベントを使用して、選択したテキストをクリップボードにコピーするプロシージャを作成します。  
  
 MDI アプリケーションは、同じ子フォームのインスタンスを多数持つことができるため、使用するフォームをプロシージャが認識している必要があります。 正しいフォームを指定するには、 <xref:System.Windows.Forms.Form.ActiveMdiChild%2A>プロパティを使用します。このプロパティは、フォーカスのある子フォーム、または最も最近アクティブだった子フォームを返します。  
  
 フォームに複数のコントロールがある場合は、アクティブなコントロールを指定する必要もあります。 プロパティと同様に、 <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>プロパティは、アクティブな子フォームにフォーカスがあるコントロールを返します。 <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> 次の手順は、子フォームメニュー、MDI フォームのメニュー、またはツールバーボタンから呼び出すことができるコピー手順を示しています。  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>アクティブな MDI 子を特定するには (テキストをクリップボードにコピーする場合)  
  
1. メソッド内で、アクティブな子フォームのアクティブなコントロールのテキストをクリップボードにコピーします。  
  
    > [!NOTE]
    > この例では、`Form1` <xref:System.Windows.Forms.RichTextBox>コントロールを含む mdi 子ウィンドウが1つ以上ある mdi 親フォーム () があることを前提としています。 詳細については、「 [MDI 親フォームの作成](how-to-create-mdi-parent-forms.md)」を参照してください。  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a>関連項目

- [マルチ ドキュメント インターフェイス (MDI) アプリケーション](multiple-document-interface-mdi-applications.md)
- [方法: MDI 親フォームを作成する](how-to-create-mdi-parent-forms.md)
- [方法: MDI 子フォームを作成する](how-to-create-mdi-child-forms.md)
- [方法: アクティブな MDI 子フォームにデータを送信する](how-to-send-data-to-the-active-mdi-child.md)
- [方法: MDI 子フォームを配置する](how-to-arrange-mdi-child-forms.md)
