---
title: '>>= 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 0ae4eb16727b2b297088170ada04cfd07d6c7a0a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980114"
---
# <a name="-operator-visual-basic"></a>>>= 演算子 (Visual Basic)
変数またはプロパティの値に算術右シフトを実行し、結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 整数型の変数またはプロパティ (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。  
  
 `amount`  
 必須。 拡大変換後のデータ型の数値式`Integer`します。  
  
## <a name="remarks"></a>Remarks  
 左側にある要素、`>>=`演算子は、単純なスカラー変数、プロパティ、または配列の要素。 変数またはプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
 `>>=`演算子変数またはプロパティの値に対して算術右シフトをまず実行します。 演算子は、変数またはプロパティに、その操作の結果を割り当てます。  
  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端のシフトは行われません。 算術右シフトの右端のビット位置より後ろのシフトが破棄されと値のビットが左側にある空いたビット位置に反映されます。 つまり、`variableorproperty`負の値を持つ、空いた位置は 1 つに設定します。 場合`variableorproperty`が正の値か、空いた位置を 0 に設定されて、データ型が符号なしの型の場合は、します。  
  
## <a name="overloading"></a>オーバーロード  
 [>> 演算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)できます*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 オーバー ロード、`>>`演算子の動作に影響、`>>=`演算子。 コードで使用する場合`>>=`クラスまたは構造体をオーバー ロードで`>>`、再定義された動作を確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`>>=`のビット パターンをシフトする演算子、`Integer`変数、指定された量と割り当てを変数に結果を右。  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>関連項目
- [>> 演算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
