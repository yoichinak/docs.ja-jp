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
ms.openlocfilehash: 369946581847b4bdcf8bc658aeb94b14c529061c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182286"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>方法: コントロールのコレクションに対して実行時にコントロールを追加または削除する
アプリケーション開発の一般的なタスクは、フォーム上の任意のコンテナー コントロール (または コントロール、<xref:System.Windows.Forms.Panel>フォーム<xref:System.Windows.Forms.GroupBox>自体など) に対してコントロールを追加したり、コントロールを削除したりすることです。 デザイン時に、コントロールをパネルやグループ ボックスに直接ドラッグすることができます。 実行時には、これらのコントロールは `Controls` コレクションを保持し、それらにどのコントロールが置かれているかを追跡します。  
  
> [!NOTE]
> 次のコード例は、コントロールのコレクションを保持する任意のコントロールに適用されます。  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>プログラムを使用して、コレクションにコントロールを追加するには  
  
1. 追加するコントロールのインスタンスを作成します。  
  
2. 新しいコントロールのプロパティを設定します。  
  
3. 親コントロールの `Controls` コレクションにコントロールを追加します。  
  
     コントロールのインスタンスを作成する方法を次のコード例<xref:System.Windows.Forms.Button>に示します。 コントロールを持つフォームが<xref:System.Windows.Forms.Panel>必要で、作成されるボタンのイベント処理メソッドが`NewPanelButton_Click`既に存在します。  
  
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
  
1. イベントからイベント ハンドラーを削除します。 Visual Basic では[、RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)キーワードを使用します。C# では[、-= 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)を使用します。  
  
2. `Remove` メソッドを使用して、パネルの `Controls` コレクションから目的のコントロールを削除します。  
  
3. コントロールで<xref:System.Windows.Forms.Control.Dispose%2A>使用されているすべてのリソースを解放するメソッドを呼び出します。  
  
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
