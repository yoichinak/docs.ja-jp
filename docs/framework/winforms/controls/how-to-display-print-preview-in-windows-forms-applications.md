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
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929007"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>方法: Windows フォーム アプリケーションに印刷プレビューを表示する
<xref:System.Windows.Forms.PrintPreviewDialog>コントロールを使用すると、ユーザーがドキュメントを印刷する前に頻繁に表示することができます。  
  
 これを行うには、 <xref:System.Drawing.Printing.PrintDocument>クラスのインスタンスを指定する必要があります。これは、印刷するドキュメントです。 <xref:System.Drawing.Printing.PrintDocument>コンポーネントで印刷プレビューを使用する方法の詳細につい[ては、「」を参照してください。印刷プレビュー](../advanced/how-to-print-in-windows-forms-using-print-preview.md)を使用して Windows フォームに印刷します。  
  
> [!NOTE]
> 実行時に<xref:System.Windows.Forms.PrintPreviewDialog>コントロールを使用するには、ローカルまたはネットワーク経由でコンピューターにプリンターがインストールされている必要があります。これ<xref:System.Windows.Forms.PrintPreviewDialog>は、印刷時のドキュメントの外観をコンポーネントが決定する方法の一部であるためです。  
  
 コントロール<xref:System.Windows.Forms.PrintPreviewDialog>はクラスを<xref:System.Drawing.Printing.PrinterSettings>使用します。 さらに、 <xref:System.Windows.Forms.PrintPreviewDialog> <xref:System.Windows.Forms.PrintPreviewDialog>コンポーネントと同じ<xref:System.Drawing.Printing.PageSettings>ように、コントロールはクラスを使用します。 <xref:System.Windows.Forms.PrintPreviewDialog>コントロールの<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>プロパティで指定された印刷ドキュメントは、クラス<xref:System.Drawing.Printing.PrinterSettings>と<xref:System.Drawing.Printing.PageSettings>クラスの両方のインスタンスを参照します。これらは、ドキュメントをプレビューウィンドウに表示するために使用されます。  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Printプレビューダイアログコントロールを使用してページを表示するには  
  
- <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用してダイアログ ボックスを表示し、使用する <xref:System.Drawing.Printing.PrintDocument> を指定します。  
  
     次のコード例では、 <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click>コントロールのイベントハンドラーが<xref:System.Windows.Forms.PrintPreviewDialog>コントロールのインスタンスを開きます。 印刷ドキュメントは<xref:System.Windows.Forms.PrintDialog.Document%2A>プロパティで指定されます。 次の例では、印刷ドキュメントが指定されていません。  
  
     この例では、フォーム<xref:System.Windows.Forms.Button>にコントロール<xref:System.Drawing.Printing.PrintDocument> 、という名前`myDocument`の<xref:System.Windows.Forms.PrintPreviewDialog>コンポーネント、およびコントロールが含まれている必要があります。  
  
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
  
     (ビジュアルC#、ビジュアルC++)フォームのコンストラクターに次のコードを配置して、イベントハンドラーを登録します。  
  
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
