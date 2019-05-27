---
title: '方法: Windows フォームでグラフィックスを印刷する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 347c7064c199e953b496c9505f08c9e12c1ae670
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052811"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>方法: Windows フォームでグラフィックスを印刷する
多くの場合、Windows ベースのアプリケーションでグラフィックスを印刷するされます。 <xref:System.Drawing.Graphics>クラスは、画面やプリンターなどのデバイスにオブジェクトを描画するためのメソッドを提供します。  
  
### <a name="to-print-graphics"></a>グラフィックスを印刷するには  
  
1. 追加、<xref:System.Drawing.Printing.PrintDocument>コンポーネントをフォームにします。  
  
2. <xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント ハンドラーを使用して、<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>のプロパティ、<xref:System.Drawing.Printing.PrintPageEventArgs>クラスにどのようなグラフィックスを印刷するプリンターの指示をします。  
  
     次のコード例では、外接する四角形内に青い楕円を作成するために使用するイベント ハンドラーを示します。 四角形が次の位置およびサイズ: 100 から始まる 250 の幅、高さ 250 150。  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     (VisualC#とビジュアルC++)イベント ハンドラーを登録するフォームのコンス トラクターでは、次のコードを配置します。  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Windows フォームにおける印刷のサポート](windows-forms-print-support.md)
