---
title: '方法: 実行時に PrintDialog のユーザー入力をキャプチャします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
ms.openlocfilehash: 69a3632ddb4d68f5a916f5ffca020630abe1bd68
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707333"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>方法: 実行時に PrintDialog のユーザー入力をキャプチャします。
デザイン時に印刷に関連するオプションを設定できますが、最も可能性の高いユーザーが行う選択により、実行時にこれらのオプションを変更するは場合があります。 使用してドキュメントを印刷するためのユーザー入力をキャプチャすることができます、<xref:System.Windows.Forms.PrintDialog>と<xref:System.Drawing.Printing.PrintDocument>コンポーネント。  
  
### <a name="to-change-print-options-programmatically"></a>プログラムで印刷オプションを変更するには  
  
1.  追加、<xref:System.Windows.Forms.PrintDialog>と<xref:System.Drawing.Printing.PrintDocument>コンポーネントをフォームにします。  
  
2.  設定、<xref:System.Windows.Forms.PrintDialog.Document%2A>のプロパティ、<xref:System.Windows.Forms.PrintDialog>を<xref:System.Drawing.Printing.PrintDocument>フォームに追加します。  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  表示、<xref:System.Windows.Forms.PrintDialog>コンポーネントを使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッド。  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  ダイアログ ボックスから、ユーザーの印刷オプションにコピーされる、<xref:System.Drawing.Printing.PrinterSettings>のプロパティ、<xref:System.Drawing.Printing.PrintDocument>コンポーネント。  
  
## <a name="see-also"></a>関連項目
- [方法: Windows フォームで複数ページのテキスト ファイルを印刷します。](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Windows フォームにおける印刷のサポート](windows-forms-print-support.md)
