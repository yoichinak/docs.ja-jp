---
title: '方法: TextBox コントロールのテキスト コンテンツを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 6c0e6e53518d382a2052efa43993d418e35fa0f2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364126"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>方法: TextBox コントロールのテキスト コンテンツを設定する
この例は、使用する方法を示します、<xref:System.Windows.Controls.TextBox.Text%2A>の最初のテキストの内容を設定するプロパティを<xref:System.Windows.Controls.TextBox>コントロール。  
  
 **注**が、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の例では、バージョンを使用、`<TextBox.Text>`の各ボタンのテキスト タグで囲みます<xref:System.Windows.Controls.TextBox>コンテンツの必要はありませんので、<xref:System.Windows.Controls.TextBox>適用されます、<xref:System.Windows.Markup.ContentPropertyAttribute>属性を<xref:System.Windows.Controls.TextBox.Text%2A>プロパティ。 詳細については、次を参照してください。 [XAML の概要 (WPF)](../advanced/xaml-overview-wpf.md)します。  
  
## <a name="example"></a>例  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a>例  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a>関連項目
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
