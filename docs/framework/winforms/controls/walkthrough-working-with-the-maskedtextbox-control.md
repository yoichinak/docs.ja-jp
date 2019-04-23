---
title: 'チュートリアル: MaskedTextBox コントロールの使用'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: ff9a0edb44a95f5853edf711e0a1559e3b2e3b15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342466"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>チュートリアル: MaskedTextBox コントロールの使用
このチュートリアルでは、以下のタスクを行います。  
  
-   初期化、<xref:System.Windows.Forms.MaskedTextBox>コントロール  
  
-   使用して、<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>文字が、マスクに準拠していないときにユーザーに警告するイベント ハンドラー  
  
-   型の割り当て、<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>プロパティを使用して、<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>コミットしようとして値の型の有効な場合、ユーザーのアラートを生成するイベント ハンドラー  
  
## <a name="creating-the-project-and-adding-a-control"></a>プロジェクトを作成し、コントロールの追加  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>MaskedTextBox コントロールをフォームに追加するには  
  
1. 配置するフォームを開いて、<xref:System.Windows.Forms.MaskedTextBox>コントロール。  
  
2. ドラッグ、<xref:System.Windows.Forms.MaskedTextBox>コントロールから、**ツールボックス**をフォームにします。  
  
3. コントロールを右クリックし、選択**プロパティ**します。 **プロパティ**ウィンドウで、**マスク**プロパティをクリックして、 **.** プロパティ名の横にある (省略記号) ボタンをクリックします。  
  
4. **定型入力**ダイアログ ボックスで、**短い日付**マスクし、をクリックして**OK**。  
  
5. **プロパティ**ウィンドウのセット、<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A>プロパティを`true`します。 このプロパティの場合、短いビープ音を鳴らす、ユーザーが入力マスクの定義に違反している文字を試みるたびにします。  
  
 Mask プロパティをサポートする、文字の概要については、「解説」を参照してください、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティ。  
  
## <a name="alert-the-user-to-input-errors"></a>入力エラーをユーザーに警告します。  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>拒否されたマスク入力のバルーン ヒントを追加します  
  
1. 戻り、**ツールボックス**を追加し、<xref:System.Windows.Forms.ToolTip>をフォームにします。  
  
2. イベント ハンドラーを作成、<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>イベントを発生させる、<xref:System.Windows.Forms.ToolTip>入力エラーが発生します。 5 秒間、または、ユーザーがクリックするまで、バルーン ヒントが表示されたままです。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>無効な種類のユーザーに警告します。  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>無効なデータ型のバルーン ヒントを追加します  
  
1. フォームの<xref:System.Windows.Forms.Form.Load>イベント ハンドラーを割り当てる、<xref:System.Type>オブジェクトを表す、<xref:System.DateTime>型、<xref:System.Windows.Forms.MaskedTextBox>コントロールの<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>プロパティ。  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2. <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> イベントのイベント ハンドラーを追加します。  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MaskedTextBox>
- [MaskedTextBox コントロール](maskedtextbox-control-windows-forms.md)
