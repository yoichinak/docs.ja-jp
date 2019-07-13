---
title: Windows フォームとコントロールの国際対応フォント
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 1f9afd575e2de04e0b11556ad34436839e13d968
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942897"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Windows フォームとコントロールの国際対応フォント

国際対応のアプリケーションでは、可能な場合は、フォント フォールバックを使用するフォントを選択する勧めします。 スクリプトの文字をシステムが決定されるフォント フォールバック手段に属しています。

## <a name="using-font-fallback"></a>フォント フォールバックの使用

この機能を利用する設定しないでください、<xref:System.Drawing.Font>フォームまたはその他の要素のプロパティ。 アプリケーションは、オペレーティング システムの 1 つのローカライズされた言語によって異なるため既定のシステム フォントを自動的に使用します。 アプリケーションを実行すると、システムは自動的に提供されているオペレーティング システムで選択されているカルチャの適切なフォントを使用します。

設定しないと、フォント スタイルを変更する場合は、フォントのルールに例外があります。 ユーザーが表示されるテキスト ボックスにテキストを太字で表示するボタンをクリックしたアプリケーションの重要なことが考えられます。 そのためには関数を作成するを太字のテキスト ボックスのフォント スタイルを変更する、フォームのフォントにします。 2 つの場所でこの関数を呼び出すことが重要。 ボタンの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーと、<xref:System.Windows.Forms.Control.FontChanged>イベント ハンドラー。 のみ、関数が呼び出された場合、<xref:System.Windows.Forms.Control.Click>フォーム全体のフォント ファミリの変更のイベント ハンドラーとコードの他の部分では、によって、テキスト ボックスは、フォームの残りの部分と変わりません。

```vb
Private Sub MakeBold()
   ' Change the TextBox to a bold version of the form font
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)
End Sub

Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
   ' Clicking this button makes the TextBox bold
   MakeBold()
End Sub

Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged
   ' If the TextBox is already bold and the form's font changes,
   ' change the TextBox to a bold version of the new form font
   If (TextBox1.Font.Style = FontStyle.Bold) Then
      MakeBold()
   End If
End Sub
```

```csharp
private void button1_Click(object sender, System.EventArgs e)
{
   // Clicking this button makes the TextBox bold
   MakeBold();
}

private void MakeBold()
{
   // Change the TextBox to a bold version of the form's font
   textBox1.Font = new Font(this.Font, FontStyle.Bold);
}

private void Form1_FontChanged(object sender, System.EventArgs e)
{
   // If the TextBox is already bold and the form's font changes,
   // change the TextBox to a bold version of the new form font
   if (textBox1.Font.Style == FontStyle.Bold)
   {
      MakeBold();
   }
}
```

ただし、アプリケーションをローカライズするときに太字のフォント可能性があります表示が不十分な特定の言語。 問題になる場合は、ローカライズで、通常のテキストに太字のフォントを切り替えるオプションが必要です。 ローカライザーは、開発者は通常、ソース コードへのアクセス権がない、ためにのリソースのファイルにのみ、このオプションがリソース ファイルで設定する必要があります。 これを行うには、設定、<xref:System.Drawing.Font.Bold%2A>プロパティを`true`します。 これは、結果、ローカライザーが編集できる、リソース ファイルに書き込まれているフォントを設定します。 後のコードを作成し、`InitializeComponent`フォントをリセットする方法、フォームのフォントに基づいていますが、リソース ファイルで指定されたフォント スタイルを使用します。

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>関連項目

- [Windows フォーム アプリケーションのグローバル化](globalizing-windows-forms.md)
- [フォントとテキストの使用](using-fonts-and-text.md)
