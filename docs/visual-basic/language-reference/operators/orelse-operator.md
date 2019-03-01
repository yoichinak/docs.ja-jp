---
title: OrElse 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: d5a0a3420d86df67e38df390ce98fbbe43c69459
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981356"
---
# <a name="orelse-operator-visual-basic"></a>OrElse 演算子 (Visual Basic)
ショート サーキットの 2 つの式の包括的論理和演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 任意のブール型 ( `Boolean` ) の式を指定します。  
  
 `expression1`  
 必須。 任意のブール型 ( `Boolean` ) の式を指定します。  
  
 `expression2`  
 必須。 任意のブール型 ( `Boolean` ) の式を指定します。  
  
## <a name="remarks"></a>Remarks  
 論理操作はモード*ショート サーキット*場合は、コンパイルされたコードは、別の式の結果に応じて 1 つの式の評価をバイパスできます。 最初に評価される式の結果には、操作の最終的な結果が判断した場合必要はありません 2 番目の式を評価するため、最終的な結果を変更することはできません。 ショート サーキットと、バイパスされる式は、複雑な場合、またはプロシージャの呼び出しが含まれる場合にパフォーマンスを向上できます。  
  
 いずれかまたは両方の式に評価される場合`True`、`result`は`True`します。 次の表はどのように`result`決定されます。  
  
|場合`expression1`は|`expression2`は|値`result`は|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(評価されていません)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>データの種類  
 `OrElse`のみの演算子が定義されている、[ブール データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)します。 Visual Basic の変換を必要に応じて、各オペランド`Boolean`全体での操作を実行および`Boolean`します。 Visual Basic 変換から数値型に結果を割り当てた場合`Boolean`その型にします。 これにより、予期しない動作が生成する可能性があります。 たとえば、`5 OrElse 12`結果`–1`に変換される`Integer`します。  
  
## <a name="overloading"></a>オーバーロード  
 [または演算子](../../../visual-basic/language-reference/operators/or-operator.md)と[IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)できる*オーバー ロードされた*、ことクラスまたは構造体は動作を再定義オペランドは、そのクラスの型を持つことを意味します。または、構造体。 オーバー ロード、`Or`と`IsTrue`演算子の動作に影響、`OrElse`演算子。 コードで使用する場合`OrElse`クラスまたは構造体をオーバー ロードで`Or`と`IsTrue`、その再定義された動作を確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`OrElse`演算子を 2 つの式に対して論理和演算を実行します。 結果は、`Boolean`値を表す 2 つの式のいずれかが true かどうか。 最初の式が場合`True`、2 つ目は評価されません。  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 前の例の結果を生成する`True`、 `True`、および`False`それぞれします。 計算に`firstCheck`、1 つは、既にあるために、2 番目の式は評価されません`True`します。 計算に 2 番目の式を評価するただし、`secondCheck`します。  
  
## <a name="example"></a>例  
 次の例は、 `If`.`Then` 2 つのプロシージャ呼び出しを含むステートメント。 最初の呼び出しが返された場合`True`、2 番目の手順は呼び出されません。 2 番目の手順で、コードのこのセクションの実行時に常に実行する重要なタスクを実行する場合は、予期しない結果を生成これでした。  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>関連項目
- [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or 演算子](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Visual Basic での論理とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
