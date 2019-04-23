---
title: '方法: RichTextBox からテキスト コンテンツを抽出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
ms.openlocfilehash: 220da59ec893528c99014e9ec95fb185c461b291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086118"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>方法: RichTextBox からテキスト コンテンツを抽出する
この例の内容を抽出する方法を示しています、<xref:System.Windows.Controls.RichTextBox>プレーン テキストとして。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]コードを説明する名前付き<xref:System.Windows.Controls.RichTextBox>単純コンテンツを持つコントロール。  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>例  
 次のコードを受け取るメソッドを実装する、<xref:System.Windows.Controls.RichTextBox>を引数としてのプレーン テキストの内容を表す文字列を返します、<xref:System.Windows.Controls.RichTextBox>します。  
  
 新しいメソッドを作成<xref:System.Windows.Documents.TextRange>の内容から、<xref:System.Windows.Controls.RichTextBox>を使用して、<xref:System.Windows.Documents.FlowDocument.ContentStart%2A>と<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>を抽出する内容の範囲を示すためにします。  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>各プロパティを返す、<xref:System.Windows.Documents.TextPointer>の内容を表す基になる FlowDocument でアクセスできるは、<xref:System.Windows.Controls.RichTextBox>します。  <xref:System.Windows.Documents.TextRange> プレーン テキストの部分を返すテキスト プロパティを取得するには、提供、<xref:System.Windows.Documents.TextRange>を文字列として。  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>関連項目

- [RichTextBox の概要](richtextbox-overview.md)
- [TextBox の概要](textbox-overview.md)
