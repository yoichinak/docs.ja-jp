---
title: '方法: (Windows フォーム) 文字列に引用符を挿入します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 14180f0326b38872f5d1b112c3d9a87022fb79e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328063"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>方法: (Windows フォーム) 文字列に引用符を挿入します。
テキストの文字列に引用符 (" ") を挿入することが必要な場合があります。 例:  
  
 わかりました、「を扱う優れた!」  
  
 代わりに、使用することも、<xref:Microsoft.VisualBasic.ControlChars.Quote>定数としてフィールド。  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>コードの文字列に引用符を挿入するには  
  
1. Visual basic を埋め込み引用符として行の 2 つの引用符を挿入します。 ビジュアルでC#と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]、エスケープ シーケンスを挿入\\"を埋め込み引用符として。 たとえば、上記の文字列を作成するには、次のコードを使用します。  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     - または -  
  
2. 引用符を表す ASCII 文字または Unicode 文字を挿入します。 Visual basic では、ASCII 文字 (34) を使用します。 ビジュアルでC#、Unicode 文字 (\u0022) を使用します。  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  この例では、基本文字セットの文字を指定するユニバーサル文字名を使用できないため、\u0022 を使用することはできません。 使用した場合、C3851 が発生します。 詳細については、「[コンパイラ エラー C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851)」を参照してください。  
  
     - または -  
  
3. 文字の定数を定義し、必要に応じてその定数を使用することもできます。  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [TextBox コントロールの概要](textbox-control-overview-windows-forms.md)
- [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御します。](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [方法: Windows フォーム TextBox コントロールでパスワード テキスト ボックスを作成します。](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [方法: 読み取り専用テキスト ボックスを作成します。](how-to-create-a-read-only-text-box-windows-forms.md)
- [方法: Windows フォームの TextBox コントロールでテキストを選択します。](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [方法: Windows フォームの TextBox コントロールで複数の行を表示します。](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox コントロール](textbox-control-windows-forms.md)
