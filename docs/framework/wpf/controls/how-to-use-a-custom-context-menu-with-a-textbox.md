---
title: '方法: TextBox でカスタム コンテキスト メニューを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: b0507c6fa37f0f51f9e12ebe5f908c39c25b50d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129417"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>方法: TextBox でカスタム コンテキスト メニューを使用する
この例は、定義して、単純なカスタム コンテキスト メニューを実装する方法を示します、<xref:System.Windows.Controls.TextBox>します。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例、<xref:System.Windows.Controls.TextBox>コントロールをカスタム コンテキスト メニューが含まれています。  
  
 使用して、コンテキスト メニューを定義、<xref:System.Windows.Controls.ContextMenu>要素。  自体のコンテキスト メニューから成る、一連の<xref:System.Windows.Controls.MenuItem>要素と<xref:System.Windows.Controls.Separator>要素。  各<xref:System.Windows.Controls.MenuItem>要素は、コンテキスト メニューのコマンドを定義、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>属性は、メニュー コマンドの表示テキストを定義し、<xref:System.Windows.Controls.MenuItem.Click>属性は、各メニュー項目のハンドラー メソッドを指定します。  <xref:System.Windows.Controls.Separator>要素は、前と後のメニュー項目の間に表示される区切り線を単純に、します。  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>例  
 次の例では、前のコンテキスト メニューの定義の実装コードも有効にし、コンテキスト メニューを無効にするコードを示します。  <xref:System.Windows.Controls.ContextMenu.Opened>イベントを使用して動的に有効またはの現在の状態に応じて、特定のコマンドを無効にするのには<xref:System.Windows.Controls.TextBox>します。  
  
 既定のショートカット メニューを復元するには、使用、<xref:System.Windows.DependencyObject.ClearValue%2A>の値をクリアする方法、<xref:System.Windows.FrameworkElement.ContextMenu%2A>プロパティ。  コンテキスト メニューを完全に無効にするのには、設定、<xref:System.Windows.FrameworkElement.ContextMenu%2A>プロパティを null 参照 (`Nothing` Visual Basic で)。  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>関連項目

- [コンテキスト メニューでスペル チェックを使用する](how-to-use-spell-checking-with-a-context-menu.md)
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
