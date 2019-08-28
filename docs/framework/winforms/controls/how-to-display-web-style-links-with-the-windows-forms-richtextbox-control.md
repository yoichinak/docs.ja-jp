---
title: '方法: Windows フォームの RichTextBox コントロールを使用して Web スタイルのリンクを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: ce71981f7b233d3e168689c766128646eed3e981
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046186"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>方法: Windows フォームの RichTextBox コントロールを使用して Web スタイルのリンクを表示する

Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールでは、Web リンクを色分けおよび下線付きで表示できます。 リンクがクリックされたときに、リンクテキストで指定された Web サイトを表示するブラウザーウィンドウを開くコードを記述できます。

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>RichTextBox コントロールを使用して Web ページにリンクするには

1. プロパティを、有効な URL (たとえば "http://www.microsoft.com/") を含む文字列に設定します。 <xref:System.Windows.Forms.RichTextBox.Text%2A>

2. <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>プロパティが (既定値) に設定されていることを`true`確認します。

3. <xref:System.Diagnostics.Process>オブジェクトの新しいグローバルインスタンスを作成します。

4. 目的のテキストをブラウザーに<xref:System.Windows.Forms.RichTextBox.LinkClicked>送信するイベントのイベントハンドラーを作成します。

    次の例では、 <xref:System.Windows.Forms.RichTextBox.LinkClicked>イベントによって、Internet Explorer のインスタンスが、 <xref:System.Windows.Forms.RichTextBox>コントロールの<xref:System.Windows.Forms.RichTextBox.Text%2A>プロパティで指定された URL に開かれます。 この例では、フォームに<xref:System.Windows.Forms.RichTextBox>コントロールがあることを前提としています。

    > [!IMPORTANT]
    > 権限が不十分<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>であるために部分信頼<xref:System.Security.SecurityException>コンテキストでコードを実行している場合、メソッドを呼び出すと例外が発生します。 詳しくは、「[コード アクセス セキュリティの基礎](../../misc/code-access-security-basics.md)」をご覧ください。

    ```vb
    Public p As New System.Diagnostics.Process
    Private Sub RichTextBox1_LinkClicked _
       (ByVal sender As Object, ByVal e As _
       System.Windows.Forms.LinkClickedEventArgs) _
       Handles RichTextBox1.LinkClicked
          ' Call Process.Start method to open a browser
          ' with link text as URL.
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)
    End Sub
    ```

    ```csharp
    public System.Diagnostics.Process p = new System.Diagnostics.Process();

    private void richTextBox1_LinkClicked(object sender,
    System.Windows.Forms.LinkClickedEventArgs e)
    {
       // Call Process.Start method to open a browser
       // with link text as URL.
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);
    }
    ```

    ```cpp
    public:
       System::Diagnostics::Process ^ p;

    private:
       void richTextBox1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkClickedEventArgs ^  e)
       {
          // Call Process.Start method to open a browser
          // with link text as URL.
          p = System::Diagnostics::Process::Start("IExplore.exe",
             e->LinkText);
       }
    ```

    (ビジュアルC++)プロセス`p`を初期化する必要があります。これを行うには、次のステートメントをフォームのコンストラクターに含めます。

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    (ビジュアルC#、ビジュアルC++)フォームのコンストラクターに次のコードを配置して、イベントハンドラーを登録します。

    ```csharp
    this.richTextBox1.LinkClicked += new
       System.Windows.Forms.LinkClickedEventHandler
       (this.richTextBox1_LinkClicked);
    ```

    ```cpp
    this->richTextBox1->LinkClicked += gcnew
       System::Windows::Forms::LinkClickedEventHandler
       (this, &Form1::richTextBox1_LinkClicked);
    ```

    作業が終了したら、作成したプロセスをすぐに停止することが重要です。 上記のコードを参照すると、プロセスを停止するためのコードは次のようになります。

    ```vb
    Public Sub StopWebProcess()
       p.Kill()
    End Sub
    ```

    ```csharp
    public void StopWebProcess()
    {
       p.Kill();
    }
    ```

    ```cpp
    public: void StopWebProcess()
    {
       p->Kill();
    }
    ```

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox コントロール](richtextbox-control-windows-forms.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
