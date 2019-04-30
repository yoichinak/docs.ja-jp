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
ms.openlocfilehash: faaa48051c80b6dfd330f15f72a38297ff2d1b9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941584"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>方法: Windows フォームの RichTextBox コントロールを使用して Web スタイルのリンクを表示する
Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールは、カラーや下線が引かれたとしての Web リンクを表示できます。 リンクがクリックされたときに、リンク テキストに指定された Web サイトを表示するブラウザー ウィンドウを開いてコードを記述することができます。  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>RichTextBox コントロールでの Web ページにリンクするには  
  
1. 設定、<xref:System.Windows.Forms.RichTextBox.Text%2A>プロパティを有効な URL を含む文字列に (たとえば、"http://www.microsoft.com/")。  
  
2. 必ず、<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>プロパティに設定されて`true`(既定)。  
  
3. 場合は、新しいグローバル インスタンスを作成、<xref:System.Diagnostics.Process>オブジェクト。  
  
4. イベント ハンドラーを記述、<xref:System.Windows.Forms.RichTextBox.LinkClicked>目的のテキストをブラウザーに送信するイベントです。  
  
     次の例で、<xref:System.Windows.Forms.RichTextBox.LinkClicked>イベントで指定された URL を Internet Explorer のインスタンスを開き、<xref:System.Windows.Forms.RichTextBox.Text%2A>のプロパティ、<xref:System.Windows.Forms.RichTextBox>コントロール。 この例では使用して、フォーム、<xref:System.Windows.Forms.RichTextBox>コントロール。  
  
    > [!IMPORTANT]
    >  呼び出し元に、<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>が発生、メソッド、<xref:System.Security.SecurityException>特権がないため、部分的に信頼されたコンテキストでコードを実行している場合は例外です。 詳しくは、「[コード アクセス セキュリティの基礎](../../misc/code-access-security-basics.md)」をご覧ください。  
  
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
  
     ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) プロセスを初期化する必要があります`p`フォームのコンス トラクターに次のステートメントを含めることで実行できます。  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     (Visual c#、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
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
  
     作業が完了したら作成したプロセスをすぐに停止するのには重要です。 上に示したコードを指すようこのプロセスを停止するコードになります。  
  
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
