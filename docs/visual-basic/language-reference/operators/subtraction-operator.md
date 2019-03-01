---
title: '- 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 0c10fc3998469e19d5be744ea8fb4faed25f1a2a
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201223"
---
# <a name="--operator-visual-basic"></a>- 演算子 (Visual Basic)
2 つの数値式または数値式の負の値の差を返します。  
  
## <a name="syntax"></a>構文  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>指定項目  
 `expression1`  
 必須。 任意の数式。  
  
 `expression2`  
 ために必要な場合を除き、`–`演算子が負の値を計算します。 任意の数式。  
  
## <a name="result"></a>結果  
 結果の違いは、`expression1`と`expression2`、または負の値の`expression1`します。  
  
 結果のデータ型が数値型のデータ型に適した`expression1`と`expression2`します。 「整数の算術演算による」のテーブルを参照してください。[演算子結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。  
  
## <a name="supported-types"></a>サポートされている型  
 すべての数値型。 これには、符号なしと浮動小数点型が含まれますと`Decimal`します。  
  
## <a name="remarks"></a>Remarks  
 最初の使用率が、前に示した構文に示すように、`–`演算子は、*バイナリ*算術減算演算子の 2 つの数値式の違い。  
  
 2 つ目の使用率が、前に示した構文に示すように、`–`演算子は、*単項*式の負の値を否定演算子。 この意味では、否定の符号を反転の`expression1`、結果は正ように場合`expression1`が負の値。  
  
 いずれかの式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、`–`演算子は 0 として処理します。  
  
> [!NOTE]
>  `–`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、その再定義された動作を理解することを確認します。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`–`演算子を計算して、2 つの数値の差を返すし、数値を否定します。  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 これらのステートメントの実行`binaryResult`124.45 が含まれていますと`unaryResult`–334.90 が含まれています。  
  
## <a name="see-also"></a>関連項目
- [-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
