---
title: += 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 7fdf5cd422cf2a4081372bc14e74ed7463393520
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979854"
---
# <a name="-operator-visual-basic"></a>+= 演算子 (Visual Basic)
数値型の変数またはプロパティの値に数値式の値を追加し、結果を変数またはプロパティに代入します。 連結するためにも使用する、`String`に式を`String`変数やプロパティと、割り当て、その結果を変数またはプロパティ。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 任意の数値または`String`変数またはプロパティ。  
  
 `expression`  
 必須。 任意の数値または`String`式。  
  
## <a name="remarks"></a>Remarks  
 左側にある要素、`+=`演算子は、単純なスカラー変数、プロパティ、または配列の要素。 変数またはプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
 `+=`演算子が変数またはプロパティを左側に、右側の値を追加し、変数またはプロパティの左側に、その結果を代入します。 `+=`を連結する演算子を使用することも、 `String` 、右辺の式、`String`変数またはプロパティに割り当て、その結果、変数を左、またはその左側のプロパティ。  
  
> [!NOTE]
>  使用すると、`+=`演算子、する可能性を追加または文字列の連結が発生するかどうかを判断します。 使用して、`&=`演算子の連結のあいまいさを排除し、自己文書化コードを提供します。  
  
 この代入演算子では、拡大縮小しない変換のコンパイル環境は、厳密なセマンティクスを適用している場合、暗黙的に実行します。 これらの変換の詳細については、次を参照してください。 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)します。 厳密なと制限の緩やかなセマンティクスの詳細については、次を参照してください。 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。  
  
 制限の緩やかなセマンティクスは許可されている場合、`+=`演算子は、さまざまなによって実行されるものと同じ文字列と数値の変換を暗黙的に実行、`+`演算子。 これらの変換について詳しくは、次を参照してください。 [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)します。  
  
## <a name="overloading"></a>オーバーロード  
 `+`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 オーバー ロード、`+`演算子の動作に影響、`+=`演算子。 コードで使用する場合`+=`クラスまたは構造体をオーバー ロードで`+`、再定義された動作を確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`+=`と他の 1 つの変数の値を結合する演算子。 最初の部分を使用して`+=`別に 1 つの値を追加する数値変数を使用します。 2 番目の部分を使用して`+=`で`String`と他の 1 つの値を連結する変数。 どちらの場合は、結果は最初の変数に割り当てられます。  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 値`num1`13、およびの値が、 `str1` 「103」ようになります。  
  
## <a name="see-also"></a>関連項目
- [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
