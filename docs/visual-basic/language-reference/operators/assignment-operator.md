---
title: = 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: ca4c519dd80c07f54dc1c3dfe70daf6948446363
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591838"
---
# <a name="-operator-visual-basic"></a>= 演算子 (Visual Basic)
変数またはプロパティに値を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 任意の書き込み可能な変数または任意のプロパティ。  
  
 `value`  
 任意のリテラル、定数、または式。  
  
## <a name="remarks"></a>コメント  
 等号 (`=`) の左側の要素は、単純なスカラー変数、プロパティ、または配列の要素にすることができます。 変数またはプロパティを[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)にすることはできません。 @No__t-0 演算子は、左側の変数またはプロパティに右辺の値を代入します。  
  
> [!NOTE]
> @No__t-0 演算子は、比較演算子としても使用されます。 詳細については、「[比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)」を参照してください。  
  
## <a name="overloading"></a>オーバーロード  
 @No__t-0 演算子は、代入演算子としてではなく、関係比較演算子としてのみオーバーロードできます。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、代入演算子を示しています。 右側の値は、左側の変数に割り当てられます。  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>関連項目

- [& = 演算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= 演算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\ = 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= 演算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
- [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
