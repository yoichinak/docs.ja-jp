---
title: '方法: TextBox から行のコレクションを取得する'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224638"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>方法: TextBox から行のコレクションを取得する
この例からのテキストの行のコレクションを取得する方法を示しています、<xref:System.Windows.Controls.TextBox>します。  
  
## <a name="example"></a>例  
 次の例を受け取る単純なメソッドを示しています、<xref:System.Windows.Controls.TextBox>引数として返す、<xref:System.Collections.Specialized.StringCollection>内のテキストの行を含む、 **TextBox**。  <xref:System.Windows.Controls.TextBox.LineCount%2A>プロパティを使用して、現在の行の数を調べます、 **TextBox**と<xref:System.Windows.Controls.TextBox.GetLineText%2A>メソッドを使用して各行を抽出し、行のコレクションに追加します。  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>関連項目

- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
