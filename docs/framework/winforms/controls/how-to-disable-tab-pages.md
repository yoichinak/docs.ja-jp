---
title: '方法: タブ ページを無効にします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: a2a0f4084529b1dd2618c1cd6171ee45b8f569d3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705000"
---
# <a name="how-to-disable-tab-pages"></a>方法: タブ ページを無効にします。
状況によっては、Windows フォーム アプリケーション内で使用できるデータ アクセスを制限するされます。 タブ コントロールのタブ ページに表示されるデータがある場合をこの 1 つの例として使用することがあります。管理者には、ゲストまたは低いレベルのユーザーを制限するタブ ページの情報があります。  
  
### <a name="to-disable-tab-pages-programmatically"></a>タブ ページをプログラムで無効にするには  
  
1.  タブ コントロールを処理するコード<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>イベント。 これは、ユーザーが 1 つのタブ、[次へ] を切り替えるときに発生するイベントです。  
  
2.  資格情報を確認します。 によって表示される情報は、タブを表示するユーザーを許可する前に、ユーザーがログインに使用するユーザー名またはその他の何らかの形式の資格情報を確認することがあります。  
  
3.  ユーザーに適切な資格情報がある場合は、クリックされたタブを表示します。 ユーザーは、適切な資格情報を持っていない場合メッセージ ボックスを表示またはのユーザー インターフェイスであることを示すがありません、アクセスして、最初のタブに戻ります。  
  
    > [!NOTE]
    >  フォームの中にこの資格情報のチェックを実行するには、実稼働アプリケーションでこの機能を実装するときに<xref:System.Windows.Forms.Form.Load>イベント。 これによって、プログラミングよりはるかにより明確な方法は、すべてのユーザー インターフェイスが表示される前に、タブを非表示にできます。 以下で使用する方法 (資格情報を確認し、中に、タブを無効にすると、<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>イベント) は、例示を目的として。  
  
4.  必要に応じて、3 つ以上のタブ ページがある場合は、元の別のタブ ページを表示します。  
  
     次の例で、<xref:System.Windows.Forms.CheckBox>コントロールはアプリケーションによって異なりますが、タブへのアクセスの条件として、資格情報を確認する代わりに使用されます。 ときに、<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>資格情報のチェックが true の場合、イベントが発生します (つまり、チェック ボックスをオン)、[選択] タブで、 `TabPage2` (この例では、機密情報をタブ)、し`TabPage2`が表示されます。 それ以外の場合、`TabPage3`表示をユーザーに適切なアクセス特権がないことを示すメッセージ ボックスが表示されます。 次のコードでフォームを前提としています、<xref:System.Windows.Forms.CheckBox>コントロール (`CredentialCheck`) と<xref:System.Windows.Forms.TabControl>3 つのタブ ページを持つコントロール。  
  
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
  
     (Visual C#、Visual C)イベント ハンドラーを登録するフォームのコンス トラクターでは、次のコードを配置します。  
  
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
- [方法: タブ ページにコントロールを追加します。](how-to-add-a-control-to-a-tab-page.md)
- [方法: Windows フォーム tabcontrol のタブ追加および削除](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [方法: Windows フォーム TabControl の外観を変更します。](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
