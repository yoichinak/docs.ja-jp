---
title: プログラムによる RichTextBox での選択の変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
ms.openlocfilehash: a85dc4baa8a59d25f577996c541a422bbe2af24e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367077"
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a>プログラムによる RichTextBox での選択の変更
この例は、プログラムでの現在の選択を変更する方法を示します、<xref:System.Windows.Controls.RichTextBox>します。 この選択は、ユーザーは、ユーザー インターフェイスを使用して、コンテンツを選択した場合と同じです。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]コードを説明する名前付き<xref:System.Windows.Controls.RichTextBox>単純コンテンツを持つコントロール。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a>例  
 次のコードは、内部で、ユーザーがクリックしたときにプログラムでいくつかの任意のテキストを選択、<xref:System.Windows.Controls.RichTextBox>します。  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a>関連項目
- [RichTextBox の概要](richtextbox-overview.md)
- [TextBox の概要](textbox-overview.md)
