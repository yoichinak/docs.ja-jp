---
title: '方法: TextBox コントロールにフォーカスを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: 8c3b9881ada843d65db035835fc5f4c865a177e9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368481"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>方法: TextBox コントロールにフォーカスを設定する
この例は、使用する方法を示します、<xref:System.Windows.UIElement.Focus%2A>にフォーカスを設定する方法、<xref:System.Windows.Controls.TextBox>コントロール。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例で、単純な<xref:System.Windows.Controls.TextBox>という名前のコントロール*は*  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.UIElement.Focus%2A>にフォーカスを設定する方法、<xref:System.Windows.Controls.TextBox>名前を持つコントロール*は*します。  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
