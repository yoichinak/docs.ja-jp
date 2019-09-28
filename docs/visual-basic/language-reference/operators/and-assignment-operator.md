---
title: '&amp; = 演算子 (Visual Basic)'
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
ms.openlocfilehash: 82d791e5d66c301442c99d2cc73e3172c3e30f17
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591636"
---
# <a name="amp-operator-visual-basic"></a>&amp; = 演算子 (Visual Basic)
@No__t 0 の式を @no__t 1 つまたは複数の変数またはプロパティに連結し、その結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 @No__t 0 の変数またはプロパティ。  
  
 `expression`  
 必須。 任意のブール型 ( `String` ) の式を指定します。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 演算子の左側の要素は、単純なスカラー変数、プロパティ、または配列の要素にすることができます。 変数またはプロパティを[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)にすることはできません。 @No__t-0 演算子は、右側の `String` 式を左側の `String` 変数またはプロパティに連結し、その結果を左側の変数またはプロパティに代入します。  
  
## <a name="overloading"></a>オーバーロード  
 [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)は*オーバーロード*することができます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 @No__t-0 演算子のオーバーロードは、`&=` 演算子の動作に影響します。 コードで `&` をオーバーロードするクラスまたは構造体に @no__t 0 を使用している場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`&=` 演算子を使用して2つの @no__t 変数を連結し、その結果を最初の変数に代入します。  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
