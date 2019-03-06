---
title: '方法: 段落間の間隔を調整する'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367480"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>方法: 段落間の間隔を調整する
この例では、調整またはフロー コンテンツ内の段落の間隔を排除する方法を示します。  
  
 フロー コンテンツ内にある段落間に表示される余分なスペースが余白の段落に設定の結果したがって、段落の間隔は、段落のマージンを調整することによって制御できます。  2 つの段落の間の余分なスペースを完全に取り除く設定には、段落のマージン**0**します。  段落全体を通じて等間隔に整列させる<xref:System.Windows.Documents.FlowDocument>、内のすべての段落の均一余白値を設定するスタイルを使用して、<xref:System.Windows.Documents.FlowDocument>します。  
  
 隣接する 2 つの段落のマージンが「折りたたみ」に注意してください、2 つの余白のうち大きい方ではなくを約 2 倍になります。 そのため、隣接する 2 つの段落では、それぞれ 20 ピクセルと 40 ピクセルの余白がある、段落の間の結果として得られる領域は 40 ピクセル、2 つの余白の値のうち、大きい方です。  
  
## <a name="example"></a>例  
 次の例では、すべての余白を設定するスタイルを使用して<xref:System.Windows.Documents.Paragraph>内の要素を<xref:System.Windows.Documents.FlowDocument>に**0**で段落の間の余分なスペースが事実上なくなります、<xref:System.Windows.Documents.FlowDocument>します。  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
