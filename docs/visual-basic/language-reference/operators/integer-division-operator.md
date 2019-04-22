---
title: '\ 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 1753199e2ecf3f156b90d8c0a5cacd672397260d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828704"
---
# <a name="-operator-visual-basic"></a>\ 演算子 (Visual Basic)
2 つの数値を除算し、整数の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>指定項目  
 `expression1`  
 必須。 任意の数式。  
  
 `expression2`  
 必須。 任意の数式。  
  
## <a name="supported-types"></a>サポートされている型  
 符号なしと浮動小数点型を含め、すべての数値型と`Decimal`します。  
  
## <a name="result"></a>結果  
 結果は整数の商`expression1`で割った値`expression2`余りはすべて破棄され、整数部分だけが保持されます。 これと呼ばれます*切り捨て*します。  
  
 結果のデータ型が数値型のデータ型に適した`expression1`と`expression2`します。 「整数の算術演算による」のテーブルを参照してください。[演算子結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。  
  
 [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)小数部分の残りの部分を保持する、完全な商を返します。  
  
## <a name="remarks"></a>Remarks  
 除算を実行する前に、Visual Basic に任意の浮動小数点の数値式の変換を試みます`Long`します。 場合`Option Strict`は`On`、コンパイラ エラーが発生します。 場合`Option Strict`は`Off`、<xref:System.OverflowException>値の範囲外の場合は、 [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)します。 変換`Long`対象にも*銀行型丸め*します。 詳細については、「部分の小数部」を参照してください[型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)します。  
  
 場合`expression1`または`expression2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。  
  
## <a name="attempted-division-by-zero"></a>0 による除算  
 場合`expression2`を 0 に評価される、`\`演算子がスローされます、<xref:System.DivideByZeroException>例外。 これは、すべての数値データ型のオペランドの場合は true。  
  
> [!NOTE]
>  `\`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`\`整数除算を実行する演算子。 結果は、破棄された残りの部分を 2 つのオペランドの商の整数を表す整数です。  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 前の例の式では、それぞれ 2、3、33、および ~ 22 日の値を返します。  
  
## <a name="see-also"></a>関連項目

- [\\= 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
