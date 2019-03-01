---
title: '方法: 分割および連結コード (Visual Basic) ステートメント'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: a43d09be53eb5a04d154e482f9388e2ca480118a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967179"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>方法: 分割および連結コード (Visual Basic) ステートメント
コードを書くときにステートメントが長くなり、コード エディターでの水平方向スクロールが必要になるを作成する可能性があります。 方法は、これには影響しませんが、コードを実行、困難や他のユーザーをモニターに表示されるコードを読み取る。 このような場合は、1 つの長いステートメントを複数行に分割を検討してください。  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>複数の行に 1 つのステートメントを分割するには  
  
-   アンダー スコアである行連結文字を使用して (`_`)、改行をポイントします。 アンダースコアは、スペースの直後、および行終端記号 (キャリッジ リターン) の直前に指定する必要があります。  
  
    > [!NOTE]
    >  場合によっては、行連結文字を省略した場合、Visual Basic コンパイラ暗黙的には引き続きステートメントで次のコード行。 行連結文字を省略できます構文要素については、「暗黙的な行継続」を参照してください[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)します。  
  
     次の例では、ステートメントは行連結文字をすべて終了して 4 つの行が最後の行に分割されます。  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     このシーケンスを使用して、コード読みやすく、オンラインとタイミングの両方を印刷します。  
  
     行連結文字は、行の最後の文字である必要があります。 その他の同じ行に、それをフォローできません。  
  
     いくつかの制限の存在は行連結文字を使用することができますかたとえば、引数の名前の途中では使用できません。 行連結文字の引数リストを分割することができますが、個々 の引数の名前は残す必要があります。  
  
     行連結文字を使用してコメントを続行することはできません。 コンパイラは、特別な意味のコメント内の文字を確認しません。 複数行のコメントのコメント記号を繰り返します (`'`) 行ごとにします。  
  
 別の行に各ステートメントを配置することは推奨される方法が、Visual Basic は同じ行に複数のステートメントを配置することをもできます。  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>同じ行に複数のステートメントを配置するには  
  
-   ステートメントをコロンで区切ります (`:`)、次の例のようにします。  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>関連項目
- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
