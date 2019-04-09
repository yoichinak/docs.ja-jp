---
title: '方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: f2017ccfd6d8320d6afc7b5e8a2ce8349c4fbd17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110613"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する
パスワード ボックスは、ユーザーが入力文字列中に、プレース ホルダー文字を表示する Windows フォーム テキスト ボックスです。  
  
### <a name="to-create-a-password-text-box"></a>パスワード テキスト ボックスを作成するには  
  
1.  設定、<xref:System.Windows.Forms.TextBox.PasswordChar%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>特定の文字をコントロールします。  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A>プロパティは、テキスト ボックスに表示される文字を指定します。 たとえば、アスタリスクをパスワード ボックスに表示する場合は、指定 * の<xref:System.Windows.Forms.TextBox.PasswordChar%2A>プロパティ ウィンドウでプロパティ。 次に、どのような文字は、ユーザーがテキスト ボックスに関係なく、アスタリスクが表示されます。  
  
2.  (省略可能)設定、<xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>プロパティ。 プロパティは、テキスト ボックスに入力できる文字数を決定します。 最大長を超過した場合は、ビープ音が鳴ります、テキスト ボックスは、多くの文字を受け付けません。 使用すると、パスワードを推測しようとしているハッカーのパスワードの最大長としてしない可能性がありますので注意があります。  
  
     次のコード例では、最大で 14 文字の文字列をそのまま使用され、文字列の代わりにアスタリスクが表示されるテキスト ボックスを初期化する方法を示します。 `InitializeMyControl`プロシージャが自動的に実行されません。 呼び出す必要があります。  
  
    > [!IMPORTANT]
    >  使用して、<xref:System.Windows.Forms.TextBox.PasswordChar%2A>プロパティ テキスト ボックスには、その他のユーザーは、入力ユーザーを確認する場合は、ユーザーのパスワードを決定できませんを確認できます。 このセキュリティ対策では、あらゆる種類のストレージや、アプリケーション ロジックが原因で発生する可能性があるパスワードの送信は含まれません。 入力したテキストが何らかの方法で暗号化されていないので、他の機密データを同じように扱う必要があります。 として表示されない場合でも、パスワードはされているとして扱われますプレーン テキスト文字列 (いくつか追加のセキュリティ対策を実装している) 場合を除き、します。  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- [TextBox コントロールの概要](textbox-control-overview-windows-forms.md)
- [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [方法: 読み取り専用テキスト ボックスを作成する](how-to-create-a-read-only-text-box-windows-forms.md)
- [方法: 文字列に引用符を挿入する](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [方法: Windows フォーム TextBox コントロールでテキストを選択する](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [方法: Windows フォーム TextBox コントロールで複数行を表示する](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox コントロール](textbox-control-windows-forms.md)
