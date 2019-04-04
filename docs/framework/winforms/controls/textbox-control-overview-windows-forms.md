---
title: TextBox コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: 716195238e99938c8c416466fc84c2eff0bc7ba9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709795"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox コントロールの概要 (Windows フォーム)
Windows フォームのテキスト ボックスは、ユーザーからの入力を取得する、またはテキストを表示するに使用されます。 <xref:System.Windows.Forms.TextBox>コントロールもできる読み取り専用ですが、通常、編集可能なテキストに使用します。 テキスト ボックスでは、複数の行を表示、テキスト、コントロールのサイズをラップ、および基本的な書式設定を追加できます。 <xref:System.Windows.Forms.TextBox>コントロールは、コントロールに表示または入力テキストを単一の書式スタイルを提供します。 複数の種類の書式設定されたテキストを表示するには、使用、<xref:System.Windows.Forms.RichTextBox>コントロール。 詳細については、[RichTextBox コントロールの概要](richtextbox-control-overview-windows-forms.md)を参照してください。  
  
## <a name="working-with-the-textbox-control"></a>TextBox コントロールの操作  
 コントロールによって表示されるテキストが含まれている、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティ。 既定では、テキスト ボックス内の 2048 文字まで入力できます。 設定した場合、<xref:System.Windows.Forms.TextBox.Multiline%2A>プロパティを`true`、最大 32 KB のテキストを入力することができます。 <xref:System.Windows.Forms.TextBox.Text%2A>実行時またはユーザー入力によってコードでは、実行時に [プロパティ] ウィンドウで、デザイン時にプロパティを設定することができます。 テキスト ボックスの現在の内容は、読み取ることによって実行時に取得できます、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティ。  
  
 次のコード例では、実行時にコントロールのテキストを設定します。 `InitializeMyControl`プロシージャが自動的に実行されません。 呼び出す必要があります。  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.TextBox>
- [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御します。](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [方法: Windows フォーム TextBox コントロールでパスワード テキスト ボックスを作成します。](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [方法: 読み取り専用テキスト ボックスを作成します。](how-to-create-a-read-only-text-box-windows-forms.md)
- [方法: 文字列に引用符を挿入します。](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [方法: Windows フォームの TextBox コントロールでテキストを選択します。](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [方法: Windows フォームの TextBox コントロールで複数の行を表示します。](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox コントロール](textbox-control-windows-forms.md)
