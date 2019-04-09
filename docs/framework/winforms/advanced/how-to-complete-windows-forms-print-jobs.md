---
title: '方法: Windows フォームの印刷ジョブを完了する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: f8d0f1f067efbae6e2b667328e75996179b91737
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159823"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>方法: Windows フォームの印刷ジョブを完了する
多くの場合、ワード プロセッサや他の印刷に関連するアプリケーションは、印刷ジョブが完了したユーザーにメッセージを表示するオプションを提供します。 処理することにより、Windows フォーム内でこの機能を行うことができます、<xref:System.Drawing.Printing.PrintDocument.EndPrint>のイベント、<xref:System.Drawing.Printing.PrintDocument>コンポーネント。  
  
 次の手順で Windows ベースのアプリケーションを作成することが必要です、<xref:System.Drawing.Printing.PrintDocument>コンポーネントをこれは、Windows ベースのアプリケーションから印刷を有効にする標準的な方法です。 使用して Windows フォームからの印刷の詳細については、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを参照してください[方法。標準の Windows フォーム印刷ジョブを作成](how-to-create-standard-windows-forms-print-jobs.md)です。  
  
### <a name="to-complete-a-print-job"></a>印刷ジョブを完了するには  
  
1.  設定、<xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>のプロパティ、<xref:System.Drawing.Printing.PrintDocument>コンポーネント。  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  <xref:System.Drawing.Printing.PrintDocument.EndPrint> イベントを処理するコードを記述します。  
  
     次のコード例では、メッセージ ボックスが表示されます、ドキュメントの印刷が完了したことを示します。  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     (Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Printing.PrintDocument>
- [Windows フォームにおける印刷のサポート](windows-forms-print-support.md)
