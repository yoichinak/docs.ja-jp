---
title: '&amp; 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 2237da5d64ada6817d3a9a88b04b76f573bd76c0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976513"
---
# <a name="amp-operator-visual-basic"></a>&amp; 演算子 (Visual Basic)
2 つの式の文字列の連結を生成します。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 すべて`String`または`Object`変数。  
  
 `expression1`  
 必須。 任意の式を拡張するデータ型を持つ`String`します。  
  
 `expression2`  
 必須。 任意の式を拡張するデータ型を持つ`String`します。  
  
## <a name="remarks"></a>Remarks  
 データ型の場合`expression1`または`expression2`ない`String`に拡大変換されますが、`String`に変換されます`String`します。 かどうか、データ型のいずれかが拡大変換されないに`String`、コンパイラ エラーが発生します。  
  
 データ型`result`は`String`します。 1 つまたは両方の式に評価される場合[Nothing](../../../visual-basic/language-reference/nothing.md)またはの値に<xref:System.DBNull.Value?displayProperty=nameWithType>の値を文字列として扱われます""です。  
  
> [!NOTE]
>  `&`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
> [!NOTE]
>  型として変数を識別するために、アンパサンド (&) 文字を使用することができますも`Long`します。 詳細については、次を参照してください。[型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)します。  
  
## <a name="example"></a>例  
 この例では、`&`文字列の連結を強制する演算子。 結果は、2 つの文字列オペランドの連結を表す文字列値です。  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>関連項目
- [& = 演算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic の連結演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
