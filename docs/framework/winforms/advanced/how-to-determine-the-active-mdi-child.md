---
title: '方法: アクティブな MDI 子を決定します。'
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
ms.openlocfilehash: 95958491d624052922df9af37b188b9515480397
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714328"
---
# <a name="how-to-determine-the-active-mdi-child"></a>方法: アクティブな MDI 子を決定します。
場合によっては、現在アクティブな子フォームでフォーカスのあるコントロールを操作するコマンドを指定するします。 たとえば、子フォームのテキスト ボックスから選択したテキストをクリップボードにコピーするとします。 クリップボードを使用して、選択したテキストをコピーするプロシージャを作成すると、<xref:System.Windows.Forms.Control.Click>の編集 メニューの標準的なコピー メニュー項目のイベント。  
  
 MDI アプリケーションが同じ子フォームの多くのインスタンスを持てないため、プロシージャを使用するフォームを把握する必要があります。 正しい形式を指定するには、使用、<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>プロパティで、フォーカスのある、または最後にアクティブだった子フォームを返します。  
  
 フォーム上のいくつかのコントロールがある場合は、どのコントロールがアクティブかを指定する必要があります。 ように、<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>プロパティ、<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>プロパティは、アクティブな子フォームにフォーカスを持つコントロールを返します。 次の手順は、子フォームのメニューで、MDI フォームまたはツール バー ボタンのメニューから呼び出すことができるコピー手順を示しています。  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>アクティブな MDI 子ウィンドウ (そのテキストをクリップボードにコピー) を決定するには  
  
1.  メソッド内には、アクティブな子フォームのアクティブなコントロールのテキストをクリップボードにコピーします。  
  
    > [!NOTE]
    >  この例では、MDI 親フォームがある (`Form1`) を含む 1 つまたは複数の MDI 子ウィンドウを持つ、<xref:System.Windows.Forms.RichTextBox>コントロール。 詳細については、次を参照してください。 [MDI 親フォームを作成する](how-to-create-mdi-parent-forms.md)します。  
  
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
- [方法: MDI 親フォームを作成します。](how-to-create-mdi-parent-forms.md)
- [方法: MDI 子フォームを作成します。](how-to-create-mdi-child-forms.md)
- [方法: アクティブな MDI 子ウィンドウにデータを送信します。](how-to-send-data-to-the-active-mdi-child.md)
- [方法: MDI 子フォームを配置します。](how-to-arrange-mdi-child-forms.md)
