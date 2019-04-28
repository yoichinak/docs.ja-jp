---
title: << = 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: da2b5ca0b7538d77c3c8d8bc7d45712d656ce63a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768317"
---
# <a name="-operator-visual-basic"></a>\<\<= 演算子 (Visual Basic)
変数またはプロパティの値に算術左シフトを実行し、結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 整数型の変数またはプロパティ (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。  
  
 `amount`  
 必須。 拡大変換後のデータ型の数値式`Integer`します。  
  
## <a name="remarks"></a>Remarks  
 左側にある要素、`<<=`演算子は、単純なスカラー変数、プロパティ、または配列の要素。 変数またはプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
 `<<=`演算子は、変数またはプロパティの値の算術左シフトをまず実行します。 演算子は、その変数またはプロパティに、その操作の結果を割り当てます。  
  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端のシフトは行われません。 算術左シフトでは、結果のデータ型の範囲を超えてシフトが破棄され、右側の空いたビット位置が 0 に設定します。  
  
## <a name="overloading"></a>オーバーロード  
 [<< 演算子](../../../visual-basic/language-reference/operators/left-shift-operator.md)できます*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 オーバー ロード、`<<`演算子の動作に影響、`<<=`演算子。 コードで使用する場合`<<=`クラスまたは構造体をオーバー ロードで`<<`、再定義された動作を確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`<<=`のビット パターンをシフトする演算子、`Integer`変数に指定された量と割り当ての結果では変数のままです。  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>関連項目

- [<< 演算子](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
