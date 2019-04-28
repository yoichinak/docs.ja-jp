---
title: '方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: 43fdb023f19aa988dfef3dcd68443d6f59808472
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746629"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する
Windows フォームと<xref:System.Windows.Forms.TextBox>コントロールがフォーカスを受け取る最初に、テキスト ボックス内の既定のカーソルが既存のテキストの左側にします。 ユーザーは、キーボードまたはマウス カーソルを移動できます。 テキスト ボックスは、フォーカスを得たを失い場合、カーソルが任意の場所、ユーザー置かれたことになります。  
  
 場合によっては、この動作は、ユーザーの混乱を招くにできます。 アプリケーションをワード プロセッシング、ユーザーは既存のテキストの後に表示される新しい文字を予想どおりです。 データ エントリのアプリケーションで、ユーザーが任意の既存のエントリを置換する新しい文字予想します。 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>と<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>プロパティを有効にすることを目的に合わせて動作を変更します。  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>TextBox コントロールでのカーソル位置を制御するには  
  
1. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> プロパティに適切な値を設定します。 0 は、最初の文字の左側にすぐにカーソルを配置します。  
  
2. (省略可能)設定、<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>プロパティを選択するテキストの長さにします。  
  
     次のコードは、常に 0 に挿入ポイントを返します。 `TextBox1_Enter`イベント ハンドラーの詳細については、コントロールにバインドする必要がありますを参照してください[Windows フォームでのイベント ハンドラーの作成](../creating-event-handlers-in-windows-forms.md)です。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>挿入ポイントを既定で表示します。  
 <xref:System.Windows.Forms.TextBox>挿入ポイントが新しいフォームのみ場合に既定で表示される、<xref:System.Windows.Forms.TextBox>コントロールがタブ オーダーの先頭にします。 提供する場合にのみ、カーソルがそれ以外の場合、表示、<xref:System.Windows.Forms.TextBox>キーボードまたはマウスのいずれかにフォーカスします。  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>既定では新しいフォームにテキスト ボックスのカーソル位置を表示する  
  
- 設定、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティを`0`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- [TextBox コントロールの概要](textbox-control-overview-windows-forms.md)
- [方法: Windows フォーム TextBox コントロールでパスワード テキスト ボックスを作成します。](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [方法: 読み取り専用テキスト ボックスを作成します。](how-to-create-a-read-only-text-box-windows-forms.md)
- [方法: 文字列に引用符を挿入します。](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [方法: Windows フォームの TextBox コントロールでテキストを選択します。](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [方法: Windows フォームの TextBox コントロールで複数の行を表示します。](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox コントロール](textbox-control-windows-forms.md)
