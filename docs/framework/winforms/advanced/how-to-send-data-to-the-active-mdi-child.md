---
title: '方法: アクティブな MDI 子ウィンドウにデータを送信します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: a89956595ff98e8cda717c90a3f96c95abc8118a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707405"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>方法: アクティブな MDI 子ウィンドウにデータを送信します。
コンテキスト内で多くの場合、[マルチ ドキュメント インターフェイス (MDI) アプリケーション](multiple-document-interface-mdi-applications.md)ユーザーが MDI アプリケーションに、クリップボードからデータを貼り付けるときなど、アクティブな子ウィンドウにデータを送信する必要があります。  
  
> [!NOTE]
>  どの子ウィンドウがフォーカスを確認して、その内容をクリップボードに送信する方法については、[アクティブな MDI 子を決定する](how-to-determine-the-active-mdi-child.md)を参照してください。  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>アクティブな MDI 子ウィンドウに、クリップボードからデータを送信するには  
  
1.  メソッド内には、アクティブな子フォームのアクティブなコントロールをクリップボードにテキストをコピーします。  
  
    > [!NOTE]
    >  この例では、MDI 親フォームがある (`Form1`) を含む 1 つまたは複数の MDI 子ウィンドウを持つ、<xref:System.Windows.Forms.RichTextBox>コントロール。 詳細については、[MDI 親フォームを作成する](how-to-create-mdi-parent-forms.md)を参照してください。  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
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
- [方法: MDI 親フォームを作成します。](how-to-create-mdi-parent-forms.md)
- [方法: MDI 子フォームを作成します。](how-to-create-mdi-child-forms.md)
- [方法: アクティブな MDI 子を決定します。](how-to-determine-the-active-mdi-child.md)
- [方法: MDI 子フォームを配置します。](how-to-arrange-mdi-child-forms.md)
