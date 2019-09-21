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
ms.openlocfilehash: f615df50643912beb12eb89d80b922fc30a3e6df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944483"
---
# <a name="-operator-visual-basic"></a>+= 演算子 (Visual Basic)
数値式の値を数値変数またはプロパティの値に加算し、その結果を変数またはプロパティに代入します。 また、を使用して、 `String` `String`変数またはプロパティに式を連結し、その結果を変数またはプロパティに代入することもできます。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 任意の数値`String`または変数またはプロパティ。  
  
 `expression`  
 必須。 任意の数値`String`または式。  
  
## <a name="remarks"></a>Remarks  
 `+=`演算子の左側の要素は、単純なスカラー変数、プロパティ、または配列の要素にすることができます。 変数またはプロパティを[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)にすることはできません。  
  
 演算子`+=`は、右辺の値を左側の変数またはプロパティに追加し、結果を左側の変数またはプロパティに代入します。 演算子を使用すると、右側の`String`式を左側の`String`変数またはプロパティに連結し、その結果を左側の変数またはプロパティに代入することもできます。 `+=`  
  
> [!NOTE]
> `+=`演算子を使用すると、加算または文字列の連結が行われるかどうかを判断できない場合があります。 `&=`演算子を連結に使用して、あいまいさをなくし、自己記述型のコードを提供します。  
  
 コンパイル環境で厳密なセマンティクスが適用されている場合、この代入演算子は、暗黙的に拡張を実行しますが、縮小変換は実行しません。 これらの変換の詳細については、「[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。 厳密なセマンティクスと寛容なセマンティクスの詳細については、「 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)」を参照してください。  
  
 寛容なセマンティクスが許可され`+=`ている場合、演算子は、 `+`演算子によって実行されるものと同一のさまざまな文字列と数値変換を暗黙的に実行します。 これらの変換の詳細については、「 [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)」を参照してください。  
  
## <a name="overloading"></a>オーバーロード  
 演算子はオーバーロードできます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 `+` 演算子のオーバーロードは、 `+=`演算子の動作に影響します。 `+` をオーバーロード`+=` `+`するクラスまたは構造体でコードを使用する場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では`+=` 、演算子を使用して、ある変数の値を別の変数と結合します。 最初の部分で`+=`は、数値変数と共にを使用して、1つの値を別の値に追加します。 2番目の`+=`部分`String`では、を使用して、1つの値を別の値と連結します。 どちらの場合も、結果は最初の変数に割り当てられます。  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 の`num1`値は13になり、の`str1`値は "103" になります。  
  
## <a name="see-also"></a>関連項目

- [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
