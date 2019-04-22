---
title: '&amp;= 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: a79e779d8fcf549daeabc494e0a55deee30b5d22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835467"
---
# <a name="amp-operator-visual-basic"></a>&amp;= 演算子 (Visual Basic)
連結、`String`式を`String`変数またはプロパティし、結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 すべて`String`変数またはプロパティ。  
  
 `expression`  
 必須。 任意のブール型 ( `String` ) の式を指定します。  
  
## <a name="remarks"></a>Remarks  
 左側にある要素、`&=`演算子は、単純なスカラー変数、プロパティ、または配列の要素。 変数またはプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。 `&=`演算子の連結、 `String` 、右辺の式、`String`変数またはプロパティの左側にし、結果を代入する変数またはプロパティの左側にします。  
  
## <a name="overloading"></a>オーバーロード  
 [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)できる*オーバー ロードされた*、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型つまりします。 オーバー ロード、`&`演算子の動作に影響、`&=`演算子。 コードで使用する場合`&=`クラスまたは構造体をオーバー ロードで`&`、再定義された動作を確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`&=`を 2 つの連結演算子`String`変数と、その結果、最初の変数を割り当てます。  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
