---
title: Boolean 式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: ce9146791935a488108d110134e9273507b0da6f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825535"
---
# <a name="boolean-expressions-visual-basic"></a>Boolean 式 (Visual Basic)
*ブール式*の値に評価される式を指定、[ブールのデータ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md):`True`または`False`です。 `Boolean` 式には、いくつかの形式を取ります。 単純な形式の値を直接比較、`Boolean`変数を`Boolean`リテラルは、次の例に示すようにします。  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>2 つの意味、= 演算子  
 注意して代入ステートメント`newCustomer = True`前の例では、式と同じに見えますが、別の関数を実行して異なる方法で使用されます。 前の例では、式で`newCustomer = True`ブール値を表す、`=`記号は、比較演算子と解釈されます。 スタンドアロンのステートメントで、`=`記号は、代入演算子と解釈され、左側の変数を右側にある値を割り当てます。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 詳細については、次を参照してください。[値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)と[ステートメント](../../../../visual-basic/language-reference/statements/index.md)します。  
  
## <a name="comparison-operators"></a>比較演算子  
 比較演算子`=`、 `<`、 `>`、 `<>`、 `<=`、および`>=`ブール式を右側にある式を演算子の左側にある式を比較することによって生成演算子と、結果としての評価の`True`または`False`します。 次に例を示します。  
  
 `42 < 81`  
  
 上記の例ではブール式の評価が 42 81 未満なので`True`します。 このような式の詳細については、次を参照してください。[値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)します。  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>比較演算子が論理演算子と組み合わせる  
 比較式より複雑なブール式を生成するために論理演算子を使用して結合できます。 次の例では、論理演算子と組み合わせて比較演算子の使用を示します。  
  
 `x > y And x < 1000`  
  
 上記の例では、全体的な式の値がの両側の式の値に依存、`And`演算子。 両方の式が場合`True`、全体的な式に評価し、`True`します。 いずれかの式が場合`False`、全体の式に評価し、`False`します。  
  
## <a name="short-circuiting-operators"></a>ショート サーキット演算子  
 論理演算子`AndAlso`と`OrElse`と呼ばれる現象が発生する*ショート サーキット*します。 ショート サーキット演算子は、まず、左側のオペランドを評価します。 左側のオペランドでは、式全体の値を決定、右の式を評価することがなくプログラムの実行が処理されます。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 前の例では、演算子は、左の式を評価`45 < 12`します。 左の式が評価されるため`False`、論理式全体に評価される必要があります`False`します。 プログラムの実行はそのためのコードの実行をスキップ、`If`右の式を評価することがなくブロック`testFunction(3)`します。 この例は呼び出しません`testFunction()`左の式が式全体を falsifies ためです。  
  
 同様に場合、左の式を使用して、論理式で`OrElse`に評価される`True`、左の式が既に全体を検証するため、右の式を評価せず、次のコード行に実行されます式。  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>非ショート サーキット演算子との比較  
 これに対し、論理演算子の両辺が評価されるときに、論理演算子`And`と`Or`使用されます。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 上記の例では、 `testFunction()` 、左の式を評価する場合でも`False`します。  
  
## <a name="parenthetical-expressions"></a>かっこで囲まれた式  
 ブール式の評価の順序を制御するのにかっこを使用することができます。 かっこで囲まれた式が最初に評価されます。 複数のレベルの入れ子では、優先順位が最も深く入れ子になった式に付与されます。 かっこ内では、評価は演算子の優先順位の規則に従って処理されます。 詳細については、次を参照してください。 [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic での論理とビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [ステートメント](../../../../visual-basic/programming-guide/language-features/statements.md)
- [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Boolean データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
