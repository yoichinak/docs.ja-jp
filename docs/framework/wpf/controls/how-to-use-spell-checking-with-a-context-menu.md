---
title: '方法: コンテキスト メニューでスペル チェックを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 72b24c386eb99140c9c2729688994b81f92e1a6f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192980"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>方法: コンテキスト メニューでスペル チェックを使用する
既定では、編集コントロールでスペル チェックを有効にするとがなど<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>、コンテキスト メニューでスペル チェックの選択肢を取得します。 たとえば、ユーザーは、スペル ミスの単語を右クリックし、ときのセットを取得するオプションや、スペルの修正候補**すべて無視**します。 ただし、独自のカスタム コンテキスト メニューで、既定のショートカット メニューをオーバーライドするときにこの機能は失われ、コンテキスト メニューでスペル チェック機能を再度有効にするコードを記述する必要があります。 次の例でこれを有効にする方法を示しています、<xref:System.Windows.Controls.TextBox>します。  
  
## <a name="example"></a>例  
 次の例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を作成する、<xref:System.Windows.Controls.TextBox>コンテキスト メニューを実装するために使用される一部のイベントにします。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>例  
 次の例では、コンテキスト メニューを実装するコードを示します。  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 これを行うために使用されるコード、<xref:System.Windows.Controls.RichTextBox>は似ています。 主な違いは、パラメーターに渡される、`GetSpellingError`メソッド。 <xref:System.Windows.Controls.TextBox>、キャレット位置の整数インデックスを渡します。  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <xref:System.Windows.Controls.RichTextBox>、渡す、<xref:System.Windows.Documents.TextPointer>キャレットの位置を指定します。  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>関連項目

- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
- [テキスト編集コントロールでスペル チェックを有効にする](how-to-enable-spell-checking-in-a-text-editing-control.md)
- [TextBox でカスタム コンテキスト メニューを使用する](how-to-use-a-custom-context-menu-with-a-textbox.md)
