---
title: '方法: タブ ページを無効化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 888228c28dce591b237be16b6a321afee0105208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967150"
---
# <a name="how-to-disable-tab-pages"></a>方法: タブ ページを無効化する
場合によっては、Windows フォームアプリケーション内で使用できるデータへのアクセスを制限する必要があります。 この例の1つとして、タブコントロールのタブページにデータが表示されている場合があります。管理者は、ゲストまたは下位レベルのユーザーから制限するタブページに関する情報を持つことができます。  
  
### <a name="to-disable-tab-pages-programmatically"></a>プログラムによってタブページを無効にするには  
  
1. タブコントロールの<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>イベントを処理するコードを記述します。 これは、ユーザーが1つのタブから次のタブに切り替えたときに発生するイベントです。  
  
2. 資格情報を確認します。 表示される情報に応じて、ユーザーがタブを表示できるようにする前に、ユーザーがログインしたユーザー名または他の形式の資格情報を確認することができます。  
  
3. ユーザーが適切な資格情報を持っている場合は、クリックされたタブを表示します。 ユーザーが適切な資格情報を持っていない場合は、メッセージボックスまたはその他のユーザーインターフェイスを表示して、アクセス権がないことを示し、最初のタブに戻ります。  
  
    > [!NOTE]
    > 実稼働アプリケーションにこの機能を実装する場合は、フォームの<xref:System.Windows.Forms.Form.Load>イベント中にこの資格情報の確認を実行できます。 これにより、ユーザーインターフェイスを表示する前にタブを非表示にすることができます。これは、プログラミングの方法としてははるかに簡潔です。 次に示す方法 (資格情報を確認し、 <xref:System.Windows.Forms.TabControl.SelectedIndexChanged>イベント中にタブを無効にする) は、説明を目的としています。  
  
4. 2つ以上のタブページがある場合は、必要に応じて、元のタブページとは異なるタブページを表示します。  
  
     次の例では、 <xref:System.Windows.Forms.CheckBox>資格情報を確認する代わりにコントロールを使用しています。タブへのアクセス条件はアプリケーションによって異なります。 イベントが発生すると、資格情報の確認が true (つまり、チェックボックスがオン) になっており、選択し`TabPage2`たタブが ( `TabPage2`この例では機密情報が含まれているタブ)、が表示されます。 <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> それ以外`TabPage3`の場合は、が表示され、適切なアクセス特権がないことを示すメッセージボックスがユーザーに表示されます。 次のコードは、 <xref:System.Windows.Forms.CheckBox>コントロール (`CredentialCheck`) <xref:System.Windows.Forms.TabControl>と、3つのタブページを持つコントロールを持つフォームを前提としています。  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _   
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _   
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _   
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))   
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     (ビジュアルC#、ビジュアルC++)フォームのコンストラクターに次のコードを配置して、イベントハンドラーを登録します。  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>関連項目

- [TabControl コントロールの概要](tabcontrol-control-overview-windows-forms.md)
- [方法: タブページにコントロールを追加する](how-to-add-a-control-to-a-tab-page.md)
- [方法: Windows フォーム TabControl を使用してタブを追加および削除する](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [方法: Windows フォーム TabControl の外観を変更する](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
