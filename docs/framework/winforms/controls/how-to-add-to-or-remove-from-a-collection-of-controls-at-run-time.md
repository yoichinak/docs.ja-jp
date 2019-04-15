---
title: '方法: コントロールのコレクションに対して実行時にコントロールを追加または削除する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 85c1d398c1aabbb73d5ae34186775e2c63666cfb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309447"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>方法: コントロールのコレクションに対して実行時にコントロールを追加または削除する
アプリケーション開発の一般的なタスクをするコントロールを追加し、フォーム上のコンテナー コントロールからコントロールを削除する (など、<xref:System.Windows.Forms.Panel>または<xref:System.Windows.Forms.GroupBox>コントロール、またはフォーム自体)。 デザイン時に、コントロールをパネルやグループ ボックスに直接ドラッグすることができます。 実行時には、これらのコントロールは `Controls` コレクションを保持し、それらにどのコントロールが置かれているかを追跡します。  
  
> [!NOTE]
>  次のコード例は、コントロールのコレクションを保持する任意のコントロールに適用されます。  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>プログラムを使用して、コレクションにコントロールを追加するには  
  
1. 追加するコントロールのインスタンスを作成します。  
  
2. 新しいコントロールのプロパティを設定します。  
  
3. 親コントロールの `Controls` コレクションにコントロールを追加します。  
  
     次のコード例のインスタンスを作成する方法を示しています、<xref:System.Windows.Forms.Button>コントロール。 使用して、フォームが必要です、<xref:System.Windows.Forms.Panel>コントロールとボタンのイベント処理メソッドが作成される、 `NewPanelButton_Click`、既に存在します。  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code   
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {   
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code   
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>プログラムを使用してコレクションからコントロールを削除するには  
  
1. イベントからイベント ハンドラーを削除します。 Visual Basic で使用して、 [RemoveHandler ステートメント](~/docs/visual-basic/language-reference/statements/removehandler-statement.md)キーワード; ビジュアルでC#を使用して、 [-= 演算子 (C#リファレンス)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md)します。  
  
2. `Remove` メソッドを使用して、パネルの `Controls` コレクションから目的のコントロールを削除します。  
  
3. 呼び出す、<xref:System.Windows.Forms.Control.Dispose%2A>コントロールによって使用されるすべてのリソースを解放します。  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of   
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _   
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of   
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.   
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Panel>
- [Panel コントロール](panel-control-windows-forms.md)
