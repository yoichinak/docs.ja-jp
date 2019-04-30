---
title: '方法: Windows フォーム ErrorProvider コンポーネントを使用してフォーム妥当性検査でエラー アイコンを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
ms.openlocfilehash: 9487d4f82878ffefe17c576b16f654293ef01106
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972186"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>方法: Windows フォーム ErrorProvider コンポーネントを使用してフォーム妥当性検査でエラー アイコンを表示する
Windows フォームを使用する<xref:System.Windows.Forms.ErrorProvider>無効なデータが入力されたときにエラー アイコンを表示するコンポーネント。 それらの間のタブし、検証コードを呼び出すためにフォーム上の少なくとも 2 つのコントロールが必要です。  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>コントロールの値が有効でないときに、エラー アイコンを表示するには  
  
1. 2 つのコントロールを追加-たとえば、テキスト ボックス: Windows フォームに。  
  
2. 追加、<xref:System.Windows.Forms.ErrorProvider>コンポーネントをフォームにします。  
  
3. 最初のコントロールを選択し、コードを追加してその<xref:System.Windows.Forms.Control.Validating>イベント ハンドラー。 このコードを正常に実行するためには、プロシージャは、イベントに接続する必要があります。 詳細については、「[方法 :Windows フォームの実行時にイベント ハンドラーを作成](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)です。  
  
     次のコードは、ユーザーが入力したデータの有効性をテストします。データが有効でない場合、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッドが呼び出されます。 最初の引数、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッドでは、横にアイコンを表示するコントロールを指定します。 2 番目の引数は、表示するエラー テキストです。  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     (Visual c#、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. プロジェクトを実行します。 最初のコントロールとし、2 番目のタブには、(この例では、数値以外) では無効なデータを入力します。 エラー アイコンが表示されたら、エラー テキストを表示するマウス ポインターでポイントします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [ErrorProvider コンポーネントの概要](errorprovider-component-overview-windows-forms.md)
- [方法: Windows フォーム ErrorProvider コンポーネントで DataSet 内のエラーの表示](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
