---
title: '方法: Windows フォームの CheckBox コントロールでオプションを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: 881996563acef36a1981ca6236c155b8fc56ef0a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307321"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>方法: Windows フォームの CheckBox コントロールでオプションを設定する
Windows フォーム<xref:System.Windows.Forms.CheckBox>コントロールは、True または False のユーザーに付与するために使用またははい/いいえオプションします。 コントロールが選択されているときに、チェック マークを表示します。  
  
### <a name="to-set-options-with-checkbox-controls"></a>CheckBox コントロールでオプションを設定するには  
  
1. 値を調べて、<xref:System.Windows.Forms.CheckBox.Checked%2A>状態を判断およびその値を使用してオプションを設定するプロパティ。  
  
     以下、ときにコード サンプルでは、<xref:System.Windows.Forms.CheckBox>コントロールの<xref:System.Windows.Forms.CheckBox.CheckedChanged>イベントが発生すると、フォームの<xref:System.Windows.Forms.Control.AllowDrop%2A>プロパティに設定されて`false`チェック ボックスをオンにした場合。 これは、ユーザーの操作を制限する場合に便利です。  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox コントロールの概要](checkbox-control-overview-windows-forms.md)
- [方法: Windows フォーム CheckBox のクリックに応答します。](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox コントロール](checkbox-control-windows-forms.md)
