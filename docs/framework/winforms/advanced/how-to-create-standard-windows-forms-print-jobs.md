---
title: '方法: 標準の Windows フォーム印刷ジョブを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938242"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>方法: 標準の Windows フォーム印刷ジョブを作成する
Windows フォームでの印刷の基礎は、 <xref:System.Drawing.Printing.PrintDocument>特<xref:System.Drawing.Printing.PrintDocument.PrintPage>にイベントであるコンポーネントです。 <xref:System.Drawing.Printing.PrintDocument.PrintPage>イベントを処理するコードを記述することによって、印刷する内容と印刷方法を指定できます。  
  
### <a name="to-create-a-print-job"></a>印刷ジョブを作成するには  
  
1. コンポーネントを<xref:System.Drawing.Printing.PrintDocument>フォームに追加します。  
  
2. <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントを処理するコードを記述します。  
  
     独自の印刷ロジックをコーディングする必要があります。 また、印刷する素材を指定する必要があります。  
  
     次のコード例では、赤い四角形の形状のサンプルグラフィックが<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベントハンドラーに作成され、印刷される素材として機能します。  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     (ビジュアルC#とビジュアルC++)フォームのコンストラクターに次のコードを配置して、イベントハンドラーを登録します。  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     また、イベント<xref:System.Drawing.Printing.PrintDocument.BeginPrint>および<xref:System.Drawing.Printing.PrintDocument.EndPrint>イベントのコードを記述することもできます。たとえば、印刷するページの総数を表す整数を含め、各ページが印刷するたびにデクリメントします。  
  
    > [!NOTE]
    > フォームにコンポーネントを<xref:System.Windows.Forms.PrintDialog>追加して、ユーザーに対してクリーンで効率的なユーザーインターフェイス (UI) を提供できます。 コンポーネントのプロパティを設定すると、フォーム上で作業している印刷ドキュメントに関連するプロパティを設定できます。 <xref:System.Windows.Forms.PrintDialog.Document%2A> <xref:System.Windows.Forms.PrintDialog> コンポーネントの<xref:System.Windows.Forms.PrintDialog>詳細については、「 [PrintDialog コンポーネント](../controls/printdialog-component-windows-forms.md)」を参照してください。  
  
     プログラムで印刷ジョブを作成する方法など、Windows フォーム印刷ジョブの詳細については、「 <xref:System.Drawing.Printing.PrintPageEventArgs>」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Printing.PrintDocument>
- [Windows フォームにおける印刷のサポート](windows-forms-print-support.md)
