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
ms.openlocfilehash: cd9c53527429dfc3e7156c4023b52509452b96cd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046252"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>方法: Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする

Windows フォーム<xref:System.Windows.Forms.LinkLabel>コントロールを使用すると、フォーム上に Web スタイルのリンクを作成できます。 リンクをクリックすると、その色を変更してリンクがアクセスされたことを示すことができます。 色の変更の詳細については[、「方法:Windows フォーム LinkLabel コントロール](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)の外観を変更します。

## <a name="linking-to-another-form"></a>リンク (別のフォームに)

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>LinkLabel コントロールを使用して別のフォームにリンクするには

1. <xref:System.Windows.Forms.LinkLabel.Text%2A>プロパティを適切なキャプションに設定します。

2. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティを設定して、キャプションのどの部分がリンクとして示されるかを決定します。 どのように表示されるかは、リンクラベルの外観に関連するプロパティによって異なります。 値は、2つの<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>数値、開始文字の位置、および文字数を含むオブジェクトによって表されます。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティは、次のような方法でプロパティウィンドウまたはコードで設定できます。

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

3. イベントハンドラーで、 <xref:System.Windows.Forms.Form.Show%2A>メソッドを呼び出して、 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>プロジェクト内の別のフォームを開き、プロパティをに`true`設定します。 <xref:System.Windows.Forms.LinkLabel.LinkClicked>

    > [!NOTE]
    > <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs>クラスのインスタンスは、クリックされた<xref:System.Windows.Forms.LinkLabel>コントロールへの参照を保持しているため、 `sender`オブジェクトをキャストする必要はありません。

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

<xref:System.Windows.Forms.LinkLabel>コントロールを使用して、既定のブラウザーで Web ページを表示することもできます。

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Internet Explorer を起動し、LinkLabel コントロールを使用して Web ページにリンクするには

1. <xref:System.Windows.Forms.LinkLabel.Text%2A>プロパティを適切なキャプションに設定します。

2. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティを設定して、キャプションのどの部分がリンクとして示されるかを決定します。

3. イベントハンドラーでは、例外処理ブロックの途中で、2番目のプロシージャを呼び出します。この<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>プロシージャは`true` 、 <xref:System.Diagnostics.Process.Start%2A>プロパティをに設定し、メソッドを使用して URL で既定のブラウザーを起動します。 <xref:System.Windows.Forms.LinkLabel.LinkClicked> <xref:System.Diagnostics.Process.Start%2A>メソッドを使用するには、 <xref:System.Diagnostics?displayProperty=nameWithType>名前空間への参照を追加する必要があります。

    > [!IMPORTANT]
    > 以下のコードを部分信頼環境 (共有ドライブなど) で実行すると、 `VisitLink`メソッドが呼び出されたときに JIT コンパイラが失敗します。 ステートメント`System.Diagnostics.Process.Start`により、リンク確認要求が失敗します。 `VisitLink`メソッドが呼び出されたときに例外をキャッチすることにより、次のコードは、JIT コンパイラが失敗した場合にエラーが適切に処理されることを確認します。

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
- [方法: Windows フォーム LinkLabel コントロールの外観を変更する](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel コントロール](linklabel-control-windows-forms.md)
