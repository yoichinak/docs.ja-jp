---
title: '方法: Windows フォーム CheckBox のクリックに応答します。'
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
ms.openlocfilehash: fff08bebf4e0eeea7dff8146ed8805e9d71247da
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724506"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>方法: Windows フォーム CheckBox のクリックに応答します。
ユーザーが Windows フォームをクリックするたびに<xref:System.Windows.Forms.CheckBox>コントロール、<xref:System.Windows.Forms.Control.Click>イベントが発生します。 チェック ボックスの状態に応じていくつかの操作を実行するアプリケーションをプログラミングできます。  
  
### <a name="to-respond-to-checkbox-clicks"></a>CheckBox のクリックに応答するには  
  
1.  <xref:System.Windows.Forms.Control.Click>イベント ハンドラーを使用して、<xref:System.Windows.Forms.CheckBox.Checked%2A>プロパティをコントロールの状態を確認し、必要なアクションを実行します。  
  
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
    >  ユーザーをダブルクリックする場合、<xref:System.Windows.Forms.CheckBox>コントロール、1 回のクリックを個別に処理されます。 つまり、<xref:System.Windows.Forms.CheckBox>コントロールは、ダブルクリック イベントをサポートしていません。  
  
    > [!NOTE]
    >  ときに、<xref:System.Windows.Forms.CheckBox.AutoCheck%2A>プロパティは`true`(既定)、<xref:System.Windows.Forms.CheckBox>が自動的に選択されているかがクリックされたときにクリアします。 それ以外の場合、手動で設定する必要あります、<xref:System.Windows.Forms.CheckBox.Checked%2A>プロパティと、<xref:System.Windows.Forms.Control.Click>イベントが発生します。  
  
     使用することも、<xref:System.Windows.Forms.CheckBox>一連の措置を決定するコントロール。  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>操作のチェック ボックスを決定するには、がクリックされます。  
  
1.  値をクエリする case ステートメントを使用して、<xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティを一連の措置を決定します。 ときに、<xref:System.Windows.Forms.CheckBox.ThreeState%2A>プロパティに設定されて`true`、<xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティは、チェック ボックスを表す 3 つの値を返す可能性があります ボックスがオフの場合、またはサードパーティ中間状態、ボックスが表示されます、淡色表示に外観をオプションを示すためには、ご利用いただけません。  
  
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
    >  ときに、<xref:System.Windows.Forms.CheckBox.ThreeState%2A>プロパティに設定されて`true`、<xref:System.Windows.Forms.CheckBox.Checked%2A>プロパティが返す`true`両方の<xref:System.Windows.Forms.CheckState.Checked>と<xref:System.Windows.Forms.CheckState.Indeterminate>します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.CheckBox>
- [CheckBox コントロールの概要](checkbox-control-overview-windows-forms.md)
- [方法: Windows フォームの CheckBox コントロールでオプションを設定します。](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox コントロール](checkbox-control-windows-forms.md)
