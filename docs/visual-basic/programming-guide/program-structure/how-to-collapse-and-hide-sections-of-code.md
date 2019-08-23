---
title: '方法: コードのセクションを折りたたんで非表示にする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: db396adf24c12542f720d3b235068aea2329288d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949732"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>方法: コードのセクションを折りたたんで非表示にする (Visual Basic)
`#Region`ディレクティブを使用すると、Visual Basic ファイル内のコードのセクションを折りたたんで非表示にすることができます。 `#Region`ディレクティブを使用すると、Visual Studio コードエディターを使用して展開または折りたたむことができるコードブロックを指定できます。 コードを選択的に非表示にする機能により、ファイルの管理が容易になり、読みやすくなります。 詳細については、「[アウトライン](/visualstudio/ide/outlining)」を参照してください。  
  
 `#Region`ディレクティブは、などのコードブロック`#If...#End If`のセマンティクスをサポートします。 つまり、1つのブロックで開始し、別のブロックで終了することはできません。start と end は同じブロック内になければなりません。 `#Region`ディレクティブは、関数内ではサポートされていません。  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>コードのセクションを折りたたんで非表示にするには  
  
- 次の例に示すように`#Region` 、 `#End Region`コードのセクションをステートメントとステートメントの間に配置します。  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     ブロック`#Region`は、コードファイル内で複数回使用できます。したがって、ユーザーは、プロシージャやクラスを折りたたむことができる独自のブロックを定義できます。 `#Region`ブロックは、他の`#Region`ブロック内で入れ子にすることもできます。  
  
    > [!NOTE]
    > コードを非表示にしても、コンパイルが妨げら`#If...#End If`れることはなく、ステートメントにも影響しません。  
  
## <a name="see-also"></a>関連項目

- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [アウトライン](/visualstudio/ide/outlining)
