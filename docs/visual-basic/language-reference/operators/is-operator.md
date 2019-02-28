---
title: Is 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: c4b23bb2d81d1f5272a5813123681da7406c3368
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980341"
---
# <a name="is-operator-visual-basic"></a>Is 演算子 (Visual Basic)
2 つのオブジェクト参照変数を比較します。  
  
## <a name="syntax"></a>構文  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 すべて`Boolean`値。  
  
 `object1`  
 必須。 すべて`Object`名。  
  
 `object2`  
 必須。 すべて`Object`名。  
  
## <a name="remarks"></a>Remarks  
 `Is`演算子が 2 つのオブジェクト参照が同じオブジェクトを参照してかどうかを決定します。 ただし、値の比較は実行されません。 場合`object1`と`object2`両方には、まったく同じオブジェクト インスタンスを参照してください`result`は`True`; が存在しない場合、`result`は`False`します。  
  
 `Is` 使用することができますも、`TypeOf`キーワードを`TypeOf`.`Is`オブジェクト変数のデータ型と互換性があるかどうかをテストする式。  
  
> [!NOTE]
>  `Is`でキーワードを使用しても、[を選択しています.Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)します。  
  
## <a name="example"></a>例  
 次の例では、`Is`オブジェクト参照のペアを比較する演算子。 割り当てられている結果を`Boolean`2 つのオブジェクトが同一であるかどうかを表す値。  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 使用することができます、前の例に示すよう、`Is`両方をテストする演算子が事前バインディングし、遅延バインドされたオブジェクト。  
  
## <a name="see-also"></a>関連項目
- [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
