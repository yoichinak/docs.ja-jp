---
title: '方法: Windows フォーム TextBox コントロールでテキストを選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 3bb1245cd47084935d632ff345a32058db6074e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013297"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>方法: Windows フォーム TextBox コントロールでテキストを選択する
Windows フォームでテキストをプログラムで選択できる<xref:System.Windows.Forms.TextBox>コントロール。 たとえば、特定の文字列のテキストを検索する関数を作成する場合は、検索した文字列の位置のリーダーを視覚的にアラートを生成するテキストを選択できます。  
  
### <a name="to-select-text-programmatically"></a>プログラムでテキストを選択するには  
  
1. 設定、<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>プロパティを選択するテキストの先頭にします。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>プロパティはテキスト文字列内にカーソルを示す数、0 で、左端の位置をされています。 場合、<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>プロパティの値に文字数以上、テキスト ボックスに、カーソルが最後の文字の後に配置します。  
  
2. 設定、<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>プロパティを選択するテキストの長さにします。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>プロパティとは、カーソルの幅を設定する数値です。 設定、 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 0 によって選択される文字数よりが現在のカーソル位置からの起動に大きい数値にします。  
  
3. (省略可能)アクセスを選択したテキスト、<xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>プロパティ。  
  
     選択次のコード テキストの内容ときにボックス コントロールの<xref:System.Windows.Forms.Control.Enter>イベントが発生します。 この例では、テキスト ボックスに値を持つかどうか、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティが`null`または空の文字列。 テキスト ボックスにフォーカスが移動すると、テキスト ボックスの現在のテキストが選択されます。 `TextBox1_Enter`イベント ハンドラーの詳細については、コントロールにバインドする必要がありますを参照してください[方法。Windows フォームの実行時にイベント ハンドラーを作成](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)です。  
  
     この例をテストするには、テキスト ボックスがあるフォーカスされるまで Tab キーを押してください。 テキスト ボックスをクリックし場合、テキストは選択できません。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- [TextBox コントロールの概要](textbox-control-overview-windows-forms.md)
- [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御します。](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [方法: Windows フォーム TextBox コントロールでパスワード テキスト ボックスを作成します。](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [方法: 読み取り専用テキスト ボックスを作成します。](how-to-create-a-read-only-text-box-windows-forms.md)
- [方法: 文字列に引用符を挿入します。](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [方法: Windows フォームの TextBox コントロールで複数の行を表示します。](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox コントロール](textbox-control-windows-forms.md)
