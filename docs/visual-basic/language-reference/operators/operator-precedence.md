---
title: Visual Basic における演算子の優先順位
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 95505fd593881ff27418c69550952d072b4e3949
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628872"
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic における演算子の優先順位
いくつかの操作は、式の中で発生した場合、各部分が評価されと呼ばれる事前に定義された順序で解決*演算子の優先順位*します。  
  
## <a name="precedence-rules"></a>優先順位の規則  
 式には、複数のカテゴリからの演算子が含まれている場合は、次の規則に従って評価されます。  
  
- 算術演算および連結演算子の優先順位が次のセクションで説明されているが、比較、論理よりも大きい優先順位とビットごとの演算子。  
  
- すべての比較演算子は、優先順位が等しく、論理とビットごとの演算子よりも大きい優先順位が算術演算および連結演算子よりも優先順位の低いすべてがあります。  
  
- 論理/ビット処理演算子の優先順位が次のセクションで説明しますが、算術演算子、文字列連結演算子、および比較演算子よりも優先順位の低い。  
  
- 左から右に優先順位の等しい演算子が評価された式で表示される順序で。  
  
## <a name="precedence-order"></a>優先順位  
 演算子は、次の優先順位で評価されます。  
  
### <a name="await-operator"></a>Await 演算子  
 Await   
  
### <a name="arithmetic-and-concatenation-operators"></a>算術演算および連結演算子  
 指数 (`^`)  
  
 単項 id と否定 (`+`、 `–`)  
  
 乗算と除算の浮動小数点 (`*`、 `/`)  
  
 整数除算 (`\`)  
  
 剰余演算 (`Mod`)  
  
 加算と減算 (`+`、 `–`)  
  
 文字列の連結 (`&`)  
  
 算術ビット シフト (`<<`、 `>>`)  
  
### <a name="comparison-operators"></a>比較演算子  
 すべての比較演算子 (`=`、 `<>`、 `<`、 `<=`、 `>`、 `>=`、 `Is`、 `IsNot`、 `Like`、 `TypeOf`.`Is`)  
  
### <a name="logical-and-bitwise-operators"></a>論理演算子とビット処理演算子  
 否定 (`Not`)  
  
 組み合わせて (`And`、 `AndAlso`)  
  
 包括的論理和 (`Or`、 `OrElse`)  
  
 排他的論理和 (`Xor`)  
  
### <a name="comments"></a>コメント  
 `=`演算子はのみ、等値比較演算子、代入演算子ではありません。  
  
 文字列連結演算子 (`&`)、算術演算子ではありませんが、算術演算子を使用してグループ化の優先順位。  
  
 `Is`と`IsNot`演算子は、オブジェクト参照の比較演算子。 2 つのオブジェクトの値を比較しないでください。これらは、2 つのオブジェクト変数が同じオブジェクト インスタンスを参照しているかどうか判断のみを確認します。  
  
## <a name="associativity"></a>結合規則  
 同じ優先順位の演算子は、乗算と除算、たとえば、式にまとめて表示されます。 が発生すると、左から右に、コンパイラは各操作を評価します。 次に例を示します。  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 1 番目の式では、除算 96/8 (これは、結果は 12) し、除算 12/4 で、結果は 3 です。 コンパイラの操作を評価するため`n1`左右からから、評価は、同じの順序が明示的に示されたとき`n2`します。 両方`n1`と`n2`3 つの結果になります。 これに対し、`n3`かっこは、コンパイラは 8 の評価を強制するために、48 の結果を持つ/4 最初。  
  
 この動作により演算子があると言います。*結合規則が左*Visual Basic でします。  
  
## <a name="overriding-precedence-and-associativity"></a>優先順位と結合規則の上書き  
 かっこを使用して、他のユーザーの前に評価する式の一部を強制することができます。 これには、優先順位の順序と左結合の両方をオーバーライドできます。 Visual Basic では、常に外部の前にかっこで囲まれた操作を実行します。 一方、かっこ内で保持通常の優先順位と結合規則にかっこを使用する場合を除き、します。 次に例を示します。  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>関連項目

- [= 演算子](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Like 演算子](../../../visual-basic/language-reference/operators/like-operator.md)
- [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Await 演算子](../../../visual-basic/language-reference/operators/await-operator.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
