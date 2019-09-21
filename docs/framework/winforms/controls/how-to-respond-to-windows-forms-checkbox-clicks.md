---
title: '方法: Windows フォーム CheckBox のクリックに応答する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: 7ff6b2aad9ef0775547af57f11af28839e69637c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914979"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>方法: Windows フォーム CheckBox のクリックに応答する
ユーザーが Windows フォーム<xref:System.Windows.Forms.CheckBox>コントロールをクリックするたび<xref:System.Windows.Forms.Control.Click>に、イベントが発生します。 チェックボックスの状態に応じて、何らかのアクションを実行するようにアプリケーションをプログラミングできます。  
  
### <a name="to-respond-to-checkbox-clicks"></a>チェックボックスのクリックに応答するには  
  
1. イベントハンドラーで、 <xref:System.Windows.Forms.CheckBox.Checked%2A>プロパティを使用してコントロールの状態を確認し、必要な操作を実行します。 <xref:System.Windows.Forms.Control.Click>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the   
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the   
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > ユーザーが<xref:System.Windows.Forms.CheckBox>コントロールをダブルクリックしようとすると、各クリックは個別に処理されます。 <xref:System.Windows.Forms.CheckBox>つまり、コントロールはダブルクリックイベントをサポートしていません。  
  
    > [!NOTE]
    > プロパティが`true` (既定値) の場合、が<xref:System.Windows.Forms.CheckBox>クリックされると、が自動的に選択またはクリアされます。 <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> それ以外の場合は、 <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.Control.Click>イベントが発生したときにプロパティを手動で設定する必要があります。  
  
     また、コントロールを使用<xref:System.Windows.Forms.CheckBox>して、一連のアクションを決定することもできます。  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>チェックボックスがクリックされたときの動作を確認するには  
  
1. Case ステートメントを使用して<xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティの値を照会し、一連のアクションを決定します。 プロパティが`true`に<xref:System.Windows.Forms.CheckBox.CheckState%2A>設定されている場合、プロパティは、チェックされているボックス、オフになっているボックス、または淡色表示されたボックスが表示される3番目の不確定状態を表す3つの値を返すことができます。 <xref:System.Windows.Forms.CheckBox.ThreeState%2A>オプションが使用できないことを示す外観。  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select   
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > `true` <xref:System.Windows.Forms.CheckState.Indeterminate> `true` <xref:System.Windows.Forms.CheckState.Checked>プロパティがに<xref:System.Windows.Forms.CheckBox.Checked%2A>設定されている場合、プロパティはとの両方に対してを<xref:System.Windows.Forms.CheckBox.ThreeState%2A>返します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox コントロールの概要](checkbox-control-overview-windows-forms.md)
- [方法: Windows フォーム CheckBox コントロールでオプションを設定する](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox コントロール](checkbox-control-windows-forms.md)
