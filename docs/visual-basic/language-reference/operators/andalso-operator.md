---
title: AndAlso 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 3876fd9c32d486b8ebecc9ee2428486a687a1624
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817124"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso 演算子 (Visual Basic)
ショート サーキットの 2 つの式の論理積を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`result`|必須。 任意のブール型 ( `Boolean` ) の式を指定します。 結果は、 `Boolean` 2 つの式の比較の結果。|  
|`expression1`|必須。 任意のブール型 ( `Boolean` ) の式を指定します。|  
|`expression2`|必須。 任意のブール型 ( `Boolean` ) の式を指定します。|  
  
## <a name="remarks"></a>Remarks  
 論理操作はモード*ショート サーキット*場合は、コンパイルされたコードは、別の式の結果に応じて 1 つの式の評価をバイパスできます。 最初に評価される式の結果には、操作の最終的な結果が判断した場合必要はありません 2 番目の式を評価するため、最終的な結果を変更することはできません。 ショート サーキットと、バイパスされる式は、複雑な場合、またはプロシージャの呼び出しが含まれる場合にパフォーマンスを向上できます。  
  
 両方の式が評価される場合`True`、`result`は`True`します。 次の表はどのように`result`決定されます。  
  
|場合`expression1`は|`expression2`は|値`result`は|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(評価されていません)|`False`|  
  
## <a name="data-types"></a>データの種類  
 `AndAlso`のみの演算子が定義されている、[ブール データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)します。 Visual Basic の変換を必要に応じて、各オペランド`Boolean`全体での操作を実行および`Boolean`します。 Visual Basic 変換から数値型に結果を割り当てた場合`Boolean`その型にします。 これにより、予期しない動作が生成する可能性があります。 たとえば、`5 AndAlso 12`結果`–1`に変換される`Integer`します。  
  
## <a name="overloading"></a>オーバーロード  
 [And 演算子](../../../visual-basic/language-reference/operators/and-operator.md)と[IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)できる*オーバー ロードされた*、いるクラスまたは構造体を再定義できますの動作はその型つまりクラスまたは構造体。 オーバー ロード、`And`と`IsFalse`演算子の動作に影響、`AndAlso`演算子。 コードで使用する場合`AndAlso`クラスまたは構造体をオーバー ロードで`And`と`IsFalse`、その再定義された動作を確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`AndAlso`演算子を 2 つの式に対して論理積を実行します。 結果は、`Boolean`全体が式を連結するかどうかを表す値は true。 最初の式が場合`False`、2 つ目は評価されません。  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 前の例の結果を生成する`True`、 `False`、および`False`、それぞれします。 計算に`secondCheck`、1 つは、既にあるために、2 番目の式は評価されません`False`します。 計算に 2 番目の式を評価するただし、`thirdCheck`します。  
  
## <a name="example"></a>例  
 次の例は、`Function`プロシージャの配列の要素間で指定された値を検索します。 配列が空の場合、または配列の長さを超過した場合、`While`ステートメントでは、検索する値に対して配列の要素はテストしません。  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>関連項目

- [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And 演算子](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Visual Basic での論理とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
