---
title: '方法: インデント、ぶら下げインデント、および箇条書き段落を Windows フォームの RichTextBox コントロールでを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: b2173769634ddc4b7b42c822c3f60212eb8d8886
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713032"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>方法: インデント、ぶら下げインデント、および箇条書き段落を Windows フォームの RichTextBox コントロールでを設定します。
Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールが、表示するテキストを書式設定するためのさまざまなオプションです。 設定して箇条書きとして選択した段落を書式設定することができます、<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>プロパティ。 使用することも、 <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>、 <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>、および<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>左側と、コントロールの右端と左端の他の行のテキストの段落のインデントを設定するプロパティ。  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>段落を箇条書きとして書式設定するには  
  
1.  <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> プロパティを `true`に設定します。  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>段落にインデントを設定するには  
  
1.  設定、<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>プロパティにコントロールの左端とテキストの左端のピクセル単位で距離を表す整数。  
  
2.  設定、<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>プロパティに同じ段落の後続行の左端と段落のテキストの最初の行の左端のピクセル単位で距離を表す整数。 値、<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>プロパティは、最初の行の下で折り返されて段落内の行にのみ適用されます。  
  
3.  設定、<xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>プロパティに、コントロールの右端とテキストの右端の間のピクセル単位で距離を表す整数。  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  これらすべてのプロパティは、選択したテキストを含む段落に影響し、現在の挿入ポイントの後に入力されるテキストにも影響します。 たとえば、ユーザーが段落内の単語を選択して、インデントを調整すると、新しい設定はその単語を含む段落全体に適用され、選択した段落の後に入力される段落にも適用されます。 プログラムでテキストを選択する方法の詳細については、<xref:System.Windows.Forms.TextBoxBase.Select%2A>を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox コントロール](richtextbox-control-windows-forms.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
