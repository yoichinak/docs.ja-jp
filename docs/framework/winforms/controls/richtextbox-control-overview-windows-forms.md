---
title: RichTextBox コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0827c1919597e9eb85bfa41721676008b76564d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201599"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.RichTextBox>を表示する、入力、およびテキストの書式形式のコントロールを使用します。 <xref:System.Windows.Forms.RichTextBox>コントロールはすべて、<xref:System.Windows.Forms.TextBox>コントロールを使用して、できますが、ことができますフォント、色、およびリンクの表示; ファイルからテキストと埋め込み画像を読み込み、指定した文字を検索します。 <xref:System.Windows.Forms.RichTextBox>コントロールを通常使用するテキストの操作を行い、Microsoft Word などのワード プロセッシング アプリケーションに似た機能を表示します。 ように、<xref:System.Windows.Forms.TextBox>コントロール、<xref:System.Windows.Forms.RichTextBox>コントロールがスクロール バーを表示できますとは異なり、<xref:System.Windows.Forms.TextBox>コントロール、その既定値は、必要に応じて、水平および垂直の両方向のスクロール バーを表示して、スクロール バーの追加の設定があります。  
  
## <a name="working-with-the-richtextbox-control"></a>RichTextBox コントロールの操作  
 同様、<xref:System.Windows.Forms.TextBox>コントロール表示されるテキストが設定されて、<xref:System.Windows.Forms.RichTextBox.Text%2A>プロパティ。 <xref:System.Windows.Forms.RichTextBox>コントロール テキストの書式をさまざまなプロパティがあります。 これらのプロパティの詳細については、「[方法。Windows フォームの RichTextBox コントロールのフォント属性を設定](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)と[方法。設定してインデント、ぶら下げインデント、および箇条書き段落を Windows フォームの RichTextBox コントロールで](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)します。 ファイルを操作する、<xref:System.Windows.Forms.RichTextBox.LoadFile%2A>と<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>メソッドの表示し、プレーン テキスト、Unicode のプレーン テキスト、およびリッチ テキスト形式 (RTF) を含む複数のファイル形式を記述できます。 使用可能なファイル形式が表示されます<xref:System.Windows.Forms.RichTextBoxStreamType>します。 使用することができます、<xref:System.Windows.Forms.RichTextBox.Find%2A>テキストまたは特定の文字の文字列を検索するメソッド。  
  
 使用することも、<xref:System.Windows.Forms.RichTextBox>を設定して Web スタイルのリンクのコントロール、<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>プロパティを`true`を処理するコードを記述し、<xref:System.Windows.Forms.RichTextBox.LinkClicked>イベント。 詳細については、「[方法 :Windows で Web スタイルのリンクを表示フォームの RichTextBox コントロール](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)します。 ユーザーが設定して、コントロール内のテキストの一部またはすべてを操作するように、<xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A>プロパティを`true`します。  
  
 元に戻すのほとんどの編集操作をやり直したりすることができます、<xref:System.Windows.Forms.RichTextBox>コントロールを呼び出すことによって、<xref:System.Windows.Forms.TextBoxBase.Undo%2A>と<xref:System.Windows.Forms.RichTextBox.Redo%2A>メソッド。 <xref:System.Windows.Forms.RichTextBox.CanRedo%2A>メソッドでは、コントロールにユーザーを元に戻した最後の操作を再適用できるかどうかを判断することができます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox コントロール](richtextbox-control-windows-forms.md)
- [TextBox コントロールの概要 (Windows フォーム)](textbox-control-overview-windows-forms.md)
