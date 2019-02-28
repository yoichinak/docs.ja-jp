---
title: Visual Basic における比較演算子
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: cd7ee90e749be76012cf7143787bc6f1d096da03
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969376"
---
# <a name="comparison-operators-in-visual-basic"></a>Visual Basic における比較演算子
比較演算子は 2 つの式を比較し、`Boolean`これらの値のリレーションシップを表す値。 数値、文字列、比較演算子、およびオブジェクトの比較演算子を比較するための演算子があります。 すべての 3 種類の演算子はここで説明します。  
  
## <a name="comparing-numeric-values"></a>数値の値を比較します。  
 Visual Basic では、6 つの数値の比較演算子を使用して数値の値を比較します。 各演算子はオペランドとして数値に評価される 2 つの式を受け取ります。 次の表では、演算子の一覧し、それぞれの例を示します。  
  
|演算子|テスト条件|使用例|  
|--------------|----------------------|--------------|  
|`=` (等価)|最初の式と等しい値を 2 番目の値とは|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (非等値)|最初の式の値と等しく、2 つ目の値か。|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (より小さい)|最初の式の値より小さく、2 つ目の値とは|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (より大きい)|最初の式の値は、2 つ目の値よりも大きいですか。|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (に等しいまたはそれよりも小さい)|最初の式の値を 2 番目の値未満ですか。|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (より大きいまたは等しい)|最初の式の値が 2 番目の値以上か。|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>文字列の比較  
 Visual Basic を使用して文字列を比較し、 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)数値比較演算子とします。 `Like`演算子を使用するパターンを指定できます。 文字列を比較し、パターンと一致した場合、結果は`True`します。 それ以外の場合、結果は `False` です。 数値演算子では、比較できます。`String`として次の例は、値が並べ替え順序に基づいています。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 上記の例では、結果は`True`のため、2 番目の文字列の最初の文字の前に、最初の文字列の最初の文字を並べ替えます。 最初の文字と等しい場合は、比較は、両方の文字列では、次の文字を続けるし、などです。 次の例のように、等値演算子を使用して文字列の等価性をテストすることもできます。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 1 つの文字列が"aa"と"aaa"など、別のプレフィックスである場合より長い文字列が短い文字列より大きいと見なされます。 次に例を示します。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 並べ替え順序がバイナリの比較またはテキストの比較の設定に応じてのいずれかに基づいて`Option Compare`します。 詳細については、次を参照してください。 [Option Compare ステートメント](../../../../visual-basic/language-reference/statements/option-compare-statement.md)します。  
  
## <a name="comparing-objects"></a>オブジェクトの比較  
 Visual Basic での 2 つのオブジェクト参照変数を比較し、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)と[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)します。 2 つの参照変数が同じオブジェクト インスタンスを参照している場合を判断するには、これらの演算子のいずれかを使用します。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 前の例では、`x Is y`に評価される`True`、両方の変数が同じインスタンスを参照してください。 この結果を次の例と比較します。  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 前の例では、`x Is y`に評価される`False`、その型の異なるインスタンスに、同じ型のオブジェクトへの参照を変数が参照しているためです。  
  
 同じインスタンスを指していない 2 つのオブジェクトをテストする場合に、`IsNot`演算子の文法的に「不器用な組み合わせを回避しますできます。`Not`と`Is`します。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 前の例では、`If a IsNot b`と等価`If Not a Is b`します。  
  
### <a name="comparing-object-type"></a>オブジェクトの型の比較  
 特定の種類のオブジェクトがあるかどうかをテストすることができます、 `TypeOf`.`Is`式。 構文は次のとおりです。  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 ときに`typename`インターフェイス型を指定します、 `TypeOf`.`Is`式を返します`True`オブジェクトがインターフェイス型を実装している場合。 ときに`typename`式を返しますが、クラス型`True`場合は、オブジェクトは、指定したクラスのまたは指定したクラスから派生したクラスのインスタンス。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 前の例では、`TypeOf x Is Control`式に評価されます`True`ための種類`x`は`Button`から継承される`Control`します。  
  
 詳細については、次を参照してください。 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)します。  
  
## <a name="see-also"></a>関連項目
- [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [演算子](../../../../visual-basic/language-reference/operators/index.md)
- [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Visual Basic での論理とビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
