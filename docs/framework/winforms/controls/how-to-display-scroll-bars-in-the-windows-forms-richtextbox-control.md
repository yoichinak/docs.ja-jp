---
title: '方法: Windows フォームの RichTextBox コントロールにスクロール バーを表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 152706cee511e4bca1dd324a652e8077b1f8548a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312658"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>方法: Windows フォームの RichTextBox コントロールにスクロール バーを表示する
既定では、Windows フォームで<xref:System.Windows.Forms.RichTextBox>コントロールは、必要に応じて、垂直および水平スクロール バーを表示します。 7 つの可能な値がある、<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>のプロパティ、<xref:System.Windows.Forms.RichTextBox>コントロールは、次の表で説明されています。  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>RichTextBox コントロールにスクロール バーを表示するには  
  
1. <xref:System.Windows.Forms.RichTextBox.Multiline%2A> プロパティを `true` に設定します。 場合、水平スクロール バーなどの型は表示されません、<xref:System.Windows.Forms.RichTextBox.Multiline%2A>プロパティに設定されて`false`します。  
  
2. 設定、<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>プロパティの適切な値を<xref:System.Windows.Forms.RichTextBoxScrollBars>列挙体。  
  
    |[値]|説明|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (既定値)|テキストがコントロールの高さや幅を超えた場合にのみ、水平または垂直スクロール バー、またはその両方を表示します。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|任意の種類のスクロール バーは表示されません。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|水平方向のスクロール バーのテキストがコントロールの幅を超えた場合にのみ表示されます。 (この場合、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>にプロパティを設定する必要があります`false`)。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|垂直方向のスクロール バーのテキストがコントロールの高さを超えた場合にのみ表示されます。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|水平スクロール バーの場合に表示されます、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>プロパティに設定されて`false`します。 テキストがコントロールの幅を超えていない場合は、スクロール バーを使用できなくなります。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|常に垂直スクロール バーが表示されます。 テキストがコントロールの長さを超えていない場合は、スクロール バーを使用できなくなります。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|常に垂直スクロール バーが表示されます。 水平スクロール バーの場合に表示されます、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>プロパティに設定されて`false`します。 テキストがコントロールの高さや幅を超えていない場合、スクロール バーは淡色表示になります。|  
  
3. <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティに適切な値を設定します。  
  
    |[値]|説明|  
    |-----------|-----------------|  
    |`false`|コントロール内のテキスト行の区切りに達するまで右にスクロールされますので、コントロールの幅に合わせて自動的に調整されません。 または、両方の水平スクロール バーの上に選択した場合は、この値を使用します。|  
    |`true` (既定値)|コントロール内のテキストは、コントロールの幅に合わせて自動的に調整されます。 水平スクロール バーは表示されません。 1 つまたは複数の段落を表示する、上記の垂直スクロール バーまたは [なし] を選択した場合は、この値を使用します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox コントロール](richtextbox-control-windows-forms.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
