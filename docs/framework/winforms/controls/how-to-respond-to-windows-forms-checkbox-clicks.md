---
title: CheckBox のクリックに応答する
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
ms.openlocfilehash: 6ff20c443519446d3804b325924cb3c5cbedea97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141927"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>方法 : Windows フォーム CheckBox のクリックに応答する
ユーザーが Windows フォーム<xref:System.Windows.Forms.CheckBox>コントロールをクリックすると<xref:System.Windows.Forms.Control.Click>、イベントが発生します。 チェック ボックスの状態に応じて、何らかのアクションを実行するようにアプリケーションをプログラムできます。  
  
### <a name="to-respond-to-checkbox-clicks"></a>チェック ボックスのクリックに応答するには  
  
1. イベント<xref:System.Windows.Forms.Control.Click>ハンドラーで、プロパティを<xref:System.Windows.Forms.CheckBox.Checked%2A>使用してコントロールの状態を確認し、必要なアクションを実行します。  
  
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
    > ユーザーが<xref:System.Windows.Forms.CheckBox>コントロールをダブルクリックしようとすると、各クリックが個別に処理されます。つまり、<xref:System.Windows.Forms.CheckBox>コントロールはダブルクリック イベントをサポートしていません。  
  
    > [!NOTE]
    > プロパティが<xref:System.Windows.Forms.CheckBox.AutoCheck%2A>`true`(既定値) の場合<xref:System.Windows.Forms.CheckBox>は、 がクリックされると、自動的に選択または選択解除されます。 それ以外の場合は、イベント<xref:System.Windows.Forms.CheckBox.Checked%2A>が発生したときに<xref:System.Windows.Forms.Control.Click>プロパティを手動で設定する必要があります。  
  
     コントロールを<xref:System.Windows.Forms.CheckBox>使用して、アクションの一覧を決定することもできます。  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>チェック ボックスがクリックされたときにアクションのコースを決定するには  
  
1. case ステートメントを使用して、プロパティの値<xref:System.Windows.Forms.CheckBox.CheckState%2A>を照会してアクションの一覧を決定します。 プロパティが<xref:System.Windows.Forms.CheckBox.ThreeState%2A>に`true`設定されている場合、<xref:System.Windows.Forms.CheckBox.CheckState%2A>このプロパティは、チェック ボックス、チェックボックスの選択解除、またはオプションが使用できないことを示す淡色表示でボックスが表示される 3 番目の不確定状態を表す 3 つの可能な値を返す場合があります。  
  
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
    > プロパティが<xref:System.Windows.Forms.CheckBox.ThreeState%2A>に`true`設定されている場合、<xref:System.Windows.Forms.CheckBox.Checked%2A>プロパティは`true`、<xref:System.Windows.Forms.CheckState.Checked>と<xref:System.Windows.Forms.CheckState.Indeterminate>の両方に対して返されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox コントロールの概要](checkbox-control-overview-windows-forms.md)
- [方法 : Windows フォームの CheckBox コントロールでオプションを設定する](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [チェック ボックス コントロール](checkbox-control-windows-forms.md)
