---
title: '&amp;演算子 (Visual Basic)'
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
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968352"
---
# <a name="amp-operator-visual-basic"></a>&amp;演算子 (Visual Basic)
2つの式の文字列連結を生成します。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 `String`または`Object`変数。  
  
 `expression1`  
 必須。 変換後のデータ型`String`を持つ任意の式。  
  
 `expression2`  
 必須。 変換後のデータ型`String`を持つ任意の式。  
  
## <a name="remarks"></a>Remarks  
 `expression1`または`String` `String`のデータ型`String`がでない場合は、に変換されます。 `expression2` データ型のいずれかがに`String`拡大変換されない場合、コンパイラはエラーを生成します。  
  
 の`result`データ型が`String`です。 一方または両方の式が、 [Nothing](../../../visual-basic/language-reference/nothing.md)に評価される<xref:System.DBNull.Value?displayProperty=nameWithType>場合、または値がの場合は、値が "" である文字列として扱われます。  
  
> [!NOTE]
> 演算子はオーバーロードできます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 `&` コードでこのようなクラスまたは構造体に対してこの演算子を使用する場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
> [!NOTE]
> アンパサンド (&) 文字を使用して、変数を型`Long`として識別することもできます。 詳細については、「[型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)」を参照してください。  
  
## <a name="example"></a>例  
 この例では`&` 、演算子を使用して文字列の連結を強制的に実行します。 結果は、2つの文字列オペランドの連結を表す文字列値です。  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [& = 演算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic での連結演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
