---
title: '方法: テキストのトリミングを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 367e1f46524d8135d8269a2e2159dfe7c2468c45
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354467"
---
# <a name="how-to-enable-text-trimming"></a>方法: テキストのトリミングを有効にする
この例は、使用状況とで使用できる値の効果では、<xref:System.Windows.TextTrimming>列挙体。  
  
## <a name="example"></a>例  
 次の例では、定義、<xref:System.Windows.Controls.TextBlock>を持つ要素、<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>属性に設定します。  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a>例  
 対応する設定<xref:System.Windows.TextTrimming>次の例では、コード内のプロパティ。  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 テキストのトリミングの現在の 3 つのオプションがあります。**CharacterEllipsis**、 **WordEllipsis**、および**None**します。  
  
 ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**CharacterEllipsis**テキストが切り取られ、トリミング エッジに最も近い文字に省略記号では継続します。  この設定では、トリミング境界により近い位置でテキストが切り取られます。ただし、単語の一部が切り取られる可能性があります。  次の図では、この設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上記で定義された 1 つに似ています。  
  
 ![例:TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")  
  
 ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**WordEllipsis**テキストが切り取られ、トリミング エッジに最も近い最初の完全な単語の最後にある省略記号では継続します。  この設定は、部分的に切り取らの単語は表示されませんが、テキストとして、トリミング エッジにできるだけ近くなる傾向があります、 **CharacterEllipsis**設定します。  次の図では、この設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上で定義します。  
  
 ![例:TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")  
  
 ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**None**テキストのトリミングは実行されません。  この場合、テキストは親テキスト コンテナーの境界にトリミングされるだけです。  次の図では、この設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上記で定義された 1 つに似ています。  
  
 ![例:TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")
