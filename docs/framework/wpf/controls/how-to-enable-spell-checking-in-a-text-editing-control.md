---
title: '方法: テキスト編集コントロールでスペル チェックを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- spellchecking [WPF]
- real-time spellchecking
- TextBox control [WPF], real-time spellchecking
- spelling checker [WPF]
- checking spelling [WPF]
ms.assetid: 6f953d2b-67e8-4012-84ce-53c0e958da47
ms.openlocfilehash: 633ffe38503df743df355a8b476e7b254fcafffa
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370679"
---
# <a name="how-to-enable-spell-checking-in-a-text-editing-control"></a>方法: テキスト編集コントロールでスペル チェックを有効にする
次の例では、リアルタイムのスペル チェックを有効にする方法を示しています、<xref:System.Windows.Controls.TextBox>を使用して、<xref:System.Windows.Controls.SpellCheck.IsEnabled%2A>のプロパティ、<xref:System.Windows.Controls.SpellCheck>クラス。  
  
## <a name="example"></a>例  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellCheckExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/spellcheckexample.xaml#spellcheckexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/CSharp/SpellCheckExample.cs#spellcheckcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/visualbasic/spellcheckexample.vb#spellcheckcodeexamplewholepage)]  
  
## <a name="see-also"></a>関連項目
- [コンテキスト メニューでスペル チェックを使用する](how-to-use-spell-checking-with-a-context-menu.md)
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
