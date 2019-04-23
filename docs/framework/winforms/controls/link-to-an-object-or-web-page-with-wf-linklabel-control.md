---
title: '方法: Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: edebfaee6f0da6826f4b757568408662f3208d41
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344014"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>方法: Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする
Windows フォーム<xref:System.Windows.Forms.LinkLabel>コントロールをフォーム上で Web スタイルのリンクを作成できます。 リンクがクリックされたときに、リンクにアクセスしたかを示す色を変更できます。 色の変更の詳細については、次を参照してください。[方法。Windows フォーム LinkLabel コントロールの外観を変更する](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)します。  
  
## <a name="linking-to-another-form"></a>別のフォームへのリンク  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>LinkLabel コントロールで別のフォームにリンクするには  
  
1. 設定、<xref:System.Windows.Forms.LinkLabel.Text%2A>プロパティに適切なキャプション。  
  
2. 設定、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティのキャプションのどの部分がリンクとして示されます。 示される方法は、リンク ラベルの外観に関連するプロパティに依存します。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>によって表される値、 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 2 つの数値、文字の開始位置および文字の数を含むオブジェクト。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティ ウィンドウで、または、次のような方法でのコードでプロパティを設定することができます。  
  
    ```vb  
    ' In this code example, the link area has been set to begin  
    ' at the first character and extend for eight characters.  
    ' You may need to modify this based on the text entered in Step 1.  
    LinkLabel1.LinkArea = New LinkArea(0, 8)  
    ```  
  
    ```csharp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1.LinkArea = new LinkArea(0,8);  
    ```  
  
    ```cpp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1->LinkArea = LinkArea(0,8);  
    ```  
  
3. <xref:System.Windows.Forms.LinkLabel.LinkClicked>イベント ハンドラーを呼び出す、<xref:System.Windows.Forms.Form.Show%2A>プロジェクトで、別のフォームを開き、設定する方法、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>プロパティを`true`します。  
  
    > [!NOTE]
    >  インスタンス、<xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs>クラスへの参照を実行する、<xref:System.Windows.Forms.LinkLabel>にキャストする必要はありませんが、クリックしてされたコントロール、`sender`オブジェクト。  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       ' Show another form.  
       Dim f2 As New Form()  
       f2.Show  
       LinkLabel1.LinkVisited = True  
    End Sub  
    ```  
  
    ```csharp  
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       // Show another form.  
       Form f2 = new Form();  
       f2.Show();  
       linkLabel1.LinkVisited = true;  
    }  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Show another form.  
          Form ^ f2 = new Form();  
          f2->Show();  
          linkLabel1->LinkVisited = true;  
       }  
    ```  
  
## <a name="linking-to-a-web-page"></a>Web ページへのリンク  
 <xref:System.Windows.Forms.LinkLabel>コントロールが既定のブラウザーで Web ページを表示することもできます。  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>LinkLabel コントロールで Internet Explorer と Web ページへのリンクを開始するには  
  
1. 設定、<xref:System.Windows.Forms.LinkLabel.Text%2A>プロパティに適切なキャプション。  
  
2. 設定、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティのキャプションのどの部分がリンクとして示されます。  
  
3. <xref:System.Windows.Forms.LinkLabel.LinkClicked>例外処理ブロックでは、途中のイベント ハンドラーを設定する 2 番目のプロシージャを呼び出す、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>プロパティを`true`を使用して、 <xref:System.Diagnostics.Process.Start%2A> URL を使用して、既定のブラウザーを開始する方法。 使用する、<xref:System.Diagnostics.Process.Start%2A>メソッドへの参照を追加する必要がある、<xref:System.Diagnostics?displayProperty=nameWithType>名前空間。  
  
    > [!IMPORTANT]
    >  部分信頼環境で次のコードを実行するかどうか (など、共有ドライブ上)、JIT コンパイラが失敗したときに、`VisitLink`メソッドが呼び出されます。 `System.Diagnostics.Process.Start`ステートメントが失敗した、リンク確認要求があるとします。 例外をキャッチするときに、`VisitLink`メソッドが呼び出されると、次のコードにより、JIT コンパイラに失敗した場合、エラー適切に処理されます。  
  
    ```vb  
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       Try  
          VisitLink()  
       Catch ex As Exception  
          ' The error message  
          MessageBox.Show("Unable to open link that was clicked.")  
       End Try  
    End Sub  
  
    Sub VisitLink()  
       ' Change the color of the link text by setting LinkVisited   
       ' to True.  
       LinkLabel1.LinkVisited = True  
       ' Call the Process.Start method to open the default browser   
       ' with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com")  
    End Sub  
    ```  
  
    ```csharp  
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       try  
       {  
          VisitLink();  
       }  
       catch (Exception ex )  
       {  
          MessageBox.Show("Unable to open link that was clicked.");  
       }  
    }  
  
    private void VisitLink()  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to true.  
       linkLabel1.LinkVisited = true;  
       //Call the Process.Start method to open the default browser   
       //with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com");  
    }  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          try  
          {  
             VisitLink();  
          }  
          catch (Exception ^ ex)  
          {  
             MessageBox::Show("Unable to open link that was clicked.");  
          }  
       }  
    private:  
       void VisitLink()  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to true.  
          linkLabel1->LinkVisited = true;  
          // Call the Process.Start method to open the default browser   
          // with a URL:  
          System::Diagnostics::Process::Start("http://www.microsoft.com");  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [LinkLabel コントロールの概要](linklabel-control-overview-windows-forms.md)
- [方法: Windows フォーム LinkLabel コントロールの外観を変更します。](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel コントロール](linklabel-control-windows-forms.md)
