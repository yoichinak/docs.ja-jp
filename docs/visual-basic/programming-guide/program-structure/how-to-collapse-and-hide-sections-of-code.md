---
title: '方法: 折りたたみし、コード (Visual Basic) のセクションを非表示'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: 367527fd638f6855077caf8ff5911edb333dfcbf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648765"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>方法: 折りたたみし、コード (Visual Basic) のセクションを非表示
`#Region`ディレクティブでは、折りたたんでのコード Visual Basic ファイルのセクションを非表示にすることができます。 `#Region`ディレクティブでは、Visual Studio コード エディターを使用する場合は、拡張可能なコードまたは折りたたみのブロックを指定することができます。 選択的にコードを非表示にする機能は、ファイルをより管理しやすく、読みやすくになります。 詳細については、「[アウトライン](/visualstudio/ide/outlining)」を参照してください。  
  
 `#Region` ディレクティブのサポート コード ブロックのセマンティクス`#If...#End If`します。 つまり、1 つのブロックの開始し、は別の終了ことはできません。先頭と末尾は、同じブロック内にする必要があります。 `#Region` ディレクティブは、関数内ではサポートされていません。  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>折りたたみし、コードのセクションを非表示にするには  
  
- 間のコード セクションの配置、`#Region`と`#End Region`ステートメントは、次の例のように。  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     `#Region`ブロックは、コード ファイルで複数回使用できますが。 そのため、ユーザーがプロシージャおよび折りたたむことができ、さらに、クラスの独自のブロックを定義できます。 `#Region` 内でその他のブロックをネストすることも`#Region`ブロックします。  
  
    > [!NOTE]
    >  コードを非表示にコンパイルされないは防止されませんしには影響しません`#If...#End If`ステートメント。  
  
## <a name="see-also"></a>関連項目

- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [アウトライン](/visualstudio/ide/outlining)
