---
title: '方法: Windows フォームのダイアログ ボックスを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: b99f2273dae88faf86448da6e1d2986a83803abf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773819"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>方法: Windows フォームのダイアログ ボックスを表示する
同様に、アプリケーションでその他の形式を表示するには、ダイアログ ボックスを表示します。 スタートアップ フォームは、アプリケーションの実行時に自動的に読み込みます。 2 番目のフォームまたはダイアログ ボックスをアプリケーションで表示するために、読み込む、表示するコードを記述します。 同様に、フォームまたはダイアログ ボックスを非アンロードしたり非表示にするコードを記述します。  
  
### <a name="to-display-a-dialog-box"></a>ダイアログ ボックスを表示するには  
  
1. ダイアログ ボックスを開くイベント ハンドラーに移動します。 これは、ボタンがクリックされたときに、メニュー コマンドが選択した場合、または他のイベントが発生したときに発生することができます。  
  
2. イベント ハンドラーでは、ダイアログ ボックスを開くコードを追加します。 この例では、ボタン クリック イベントを使用して、ダイアログ ボックスを表示します。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:   
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
