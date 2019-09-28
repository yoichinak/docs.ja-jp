---
title: /= 演算子 (Visual Basic)
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
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592172"
---
# <a name="-operator-visual-basic"></a>/= 演算子 (Visual Basic)
式の値によって変数またはプロパティの値を除算し、浮動小数点演算の結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 任意の数値変数またはプロパティ。  
  
 `expression`  
 必須。 任意の数式。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 演算子の左側の要素は、単純なスカラー変数、プロパティ、または配列の要素にすることができます。 変数またはプロパティを[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)にすることはできません。  
  
 @No__t-0 演算子は、まず、変数またはプロパティの値 (演算子の左辺) を式の値 (演算子の右側) によって除算することになります。 次に、演算子は、その演算の浮動小数点の結果を変数またはプロパティに代入します。  
  
 このステートメントでは、左側の変数またはプロパティに @no__t 0 値が割り当てられます。 @No__t-0 が `On` の場合、`variableorproperty` は `Double` である必要があります。 @No__t-0 が `Off` の場合、Visual Basic は暗黙的な変換を実行し、結果の値を実行時に発生する可能性のあるエラーと共に `variableorproperty` に割り当てます。 詳細については、「[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」および「 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)」を参照してください。  
  
## <a name="overloading"></a>オーバーロード  
 [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)は*オーバーロード*することができます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 @No__t-0 演算子のオーバーロードは、`/=` 演算子の動作に影響します。 コードで `/` をオーバーロードするクラスまたは構造体に @no__t 0 を使用している場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`/=` 演算子を使用して1つの @no__t 1 つの変数を2番目の変数に除算し、商を最初の変数に代入します。  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>関連項目

- [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\ = 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
