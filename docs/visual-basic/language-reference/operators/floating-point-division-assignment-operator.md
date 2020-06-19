---
title: /= 演算子
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: a8a031e968df90496a4e263ae78d47045ccdc923
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331034"
---
# <a name="-operator-visual-basic"></a>/= 演算子 (Visual Basic)
変数またはプロパティの値を式の値で除算し、その浮動小数点の結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須です。 任意の数値変数またはプロパティ。  
  
 `expression`  
 必須です。 任意の数式。  
  
## <a name="remarks"></a>Remarks  
 `/=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。 変数またはプロパティを [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 `/=` 演算子は、最初に (演算子の左側にある) 変数またはプロパティの値を (演算子の右側にある) 式の値で除算します。 次に、この演算子はその演算の浮動小数点の結果を変数またはプロパティに代入します。  
  
 このステートメントにより、左側の変数またはプロパティに `Double` 値が代入されます。 `Option Strict` が `On` の場合、`variableorproperty` は `Double` である必要があります。 `Option Strict` が `Off` の場合、Visual Basic によって暗黙的な変換が実行され、結果の値が `variableorproperty` に代入されます。実行時にエラーが発生する可能性があります。 詳細については、「[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」および「[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)」を参照してください。  
  
## <a name="overloading"></a>オーバーロード  
 [/ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体でその動作を再定義できます。 `/` 演算子をオーバーロードすると、`/=` 演算子の動作に影響します。 コードで、`/` をオーバーロードしているクラスまたは構造体に対して `/=` を使用する場合は、再定義される動作を必ず理解してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`/=` 演算子を使用して 1 番目の `Integer` 変数を 2 番目の変数で除算し、商を 1 番目の変数に代入します。  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>関連項目

- [/ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\= 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
