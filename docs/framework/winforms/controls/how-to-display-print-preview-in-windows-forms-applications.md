---
title: '方法: Windows フォーム アプリケーションに印刷プレビューを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: 22247c941eff575f0f3e5683e46376054ba13bb5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013415"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>方法: Windows フォーム アプリケーションに印刷プレビューを表示する
使用することができます、<xref:System.Windows.Forms.PrintPreviewDialog>印刷する前に多くの場合、ドキュメントを表示するユーザーを有効にするコントロール。  
  
 これを行うには、インスタンスを指定する必要があります、<xref:System.Drawing.Printing.PrintDocument>クラスです。 これは、印刷するドキュメント。 印刷プレビューでの使用の詳細については、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを参照してください[方法。印刷プレビューを使用して Windows フォームにおける印刷](../advanced/how-to-print-in-windows-forms-using-print-preview.md)します。  
  
> [!NOTE]
>  使用する、<xref:System.Windows.Forms.PrintPreviewDialog>コントロール、実行時にユーザーが必要ローカルまたはネットワークを介してコンピューターにインストールされているプリンターは部分的方法、<xref:System.Windows.Forms.PrintPreviewDialog>コンポーネントは、印刷時にドキュメントがどのように表示されるかを決定します。  
  
 <xref:System.Windows.Forms.PrintPreviewDialog>コントロール、<xref:System.Drawing.Printing.PrinterSettings>クラス。 さらに、<xref:System.Windows.Forms.PrintPreviewDialog>コントロール、<xref:System.Drawing.Printing.PageSettings>クラスと同様、<xref:System.Windows.Forms.PrintPreviewDialog>はコンポーネント。 指定された印刷ドキュメント、<xref:System.Windows.Forms.PrintPreviewDialog>コントロールの<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>プロパティが両方のインスタンスを指す、<xref:System.Drawing.Printing.PrinterSettings>と<xref:System.Drawing.Printing.PageSettings>クラス、およびこれらがプレビュー ウィンドウにドキュメントを表示するために使用します。  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>PrintPreviewDialog コントロールを使用してページを表示するには  
  
- <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用してダイアログ ボックスを表示し、使用する <xref:System.Drawing.Printing.PrintDocument> を指定します。  
  
     次のコード例で、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーのインスタンスを開き、<xref:System.Windows.Forms.PrintPreviewDialog>コントロール。 印刷ドキュメントがで指定された、<xref:System.Windows.Forms.PrintDialog.Document%2A>プロパティ。 次の例では、印刷ドキュメントは指定されません。  
  
     この例で、フォームに、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Drawing.Printing.PrintDocument>という名前のコンポーネント`myDocument`と<xref:System.Windows.Forms.PrintPreviewDialog>コントロール。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual c#、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>関連項目

- [PrintDocument コンポーネント](printdocument-component-windows-forms.md)
- [PrintPreviewDialog コントロール](printpreviewdialog-control-windows-forms.md)
- [Windows フォームにおける印刷のサポート](../advanced/windows-forms-print-support.md)
- [Windows フォーム](../index.md)
