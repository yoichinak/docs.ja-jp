---
title: + 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 4fc8ce96caea436b63fe346139e27ec8dd048f10
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814108"
---
# <a name="-operator-visual-basic"></a>+ 演算子 (Visual Basic)
2 つの数値を追加します。 または、数値式の正の値を取得します。 2 つの文字列式を連結することも使用できます。  
  
## <a name="syntax"></a>構文  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`expression1`|必須。 任意の数値または文字列式。|  
|`expression2`|ために必要な場合を除き、`+`演算子が負の値を計算します。 任意の数値または文字列式。|  
  
## <a name="result"></a>結果  
 場合`expression1`と`expression2`はどちらも数値では、その算術の合計になります。  
  
 場合`expression2`、存在しない場合は、`+`演算子は、*単項*id 演算子式の値は変わりません。 操作は、この意味での符号を保持することで構成されます`expression1`で結果が負の値であるため、場合`expression1`が負の値。  
  
 場合`expression1`と`expression2`、両方の文字列をその値を連結したものになります。  
  
 場合`expression1`と`expression2`は、混合型の実行されるアクションは、その型の内容、およびの設定に依存、 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。 詳細については、します。「解説」表を参照してください。  
  
## <a name="supported-types"></a>サポートされている型  
 符号なしと浮動小数点型を含め、すべての数値型と`Decimal`、および`String`します。  
  
## <a name="remarks"></a>Remarks  
 一般に、`+`可能であれば、算術加算を実行し、両方の式が文字列が場合にのみを連結します。  
  
 どちらの式がある場合、 `Object`、Visual Basic は、次のアクションを実行します。  
  
|式のデータ型|コンパイラによる処理|  
|---|---|  
|両方の式が数値データ型 (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、または`Double`)|追加します。 結果のデータ型が数値型のデータ型に適した`expression1`と`expression2`します。 「整数の算術演算による」のテーブルを参照してください。[演算子結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。|  
|両方の式は型 `String`|連結します。|  
|1 つの式が数値データ型で、他の文字列|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、暗黙的に変換、`String`に`Double`を追加します。<br /><br /> 場合、`String`に変換できない`Double`、スローし、<xref:System.InvalidCastException>例外。|  
|1 つの式が数値データ型、もう一方は[Nothing](../../../visual-basic/language-reference/nothing.md)|追加すると`Nothing`値 0 にします。|  
|1 つの式が文字列、もう一方は `Nothing`|使用した、連結`Nothing`として値を持つ""です。|  
  
 1 つの式がある場合、`Object`式では、Visual Basic は、次のアクションを実行します。  
  
|式のデータ型|コンパイラによる処理|  
|---|---|  
|`Object` 式は、数値の値を保持し、もう一方の数値データ型|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、しを追加します。|  
|`Object` 式が数値の値を保持して、他の種類 `String`|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、暗黙的に変換、`String`に`Double`を追加します。<br /><br /> 場合、`String`に変換できない`Double`、スローし、<xref:System.InvalidCastException>例外。|  
|`Object` 式が文字列を保持し、もう一方の数値データ型|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、文字列を暗黙的に変換`Object`に`Double`を追加します。<br /><br /> 場合、文字列`Object`に変換できない`Double`、スローし、<xref:System.InvalidCastException>例外。|  
|`Object` 式文字列を保持する、他の種類 `String`|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、暗黙的に変換`Object`に`String`と連結します。|  
  
 両方の式が場合`Object`式では、Visual Basic は、次の操作 (`Option Strict Off`のみ)。  
  
|式のデータ型|コンパイラによる処理|  
|---|---|  
|どちらも`Object`式が数値の値を保持|追加します。|  
|どちらも`Object`型の式は、 `String`|連結します。|  
|1 つ`Object`式には、数値の値が保持しているし、その他の文字列を保持|文字列に暗黙的に変換`Object`に`Double`を追加します。<br /><br /> 場合、文字列`Object`値を数値に変換することはできませんし、スロー、<xref:System.InvalidCastException>例外。|  
  
 いずれか`Object`式に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)または<xref:System.DBNull>、`+`演算子として処理、`String`の値を持つ""。  
  
> [!NOTE]
>  使用すると、`+`演算子、する可能性を追加または文字列の連結が発生するかどうかを判断します。 使用して、`&`演算子の連結のあいまいさを排除し、自己文書化コードを提供します。  
  
## <a name="overloading"></a>オーバーロード  
 `+`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`+`番号を追加する演算子。 オペランドが両方の数値の場合は、Visual Basic は、算術演算の結果を計算します。 算術演算の結果は、2 つのオペランドの合計を表します。  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 使用することも、`+`文字列を連結する演算子。 オペランドが両方の文字列の場合は、Visual Basic はそれらを連結します。 文字列連結の結果は、他の後に、2 つのオペランドの内容で構成される 1 つの文字列を表します。  
  
 結果は異なりますの設定は、オペランドが混合型である場合、 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。 次の例は、結果を示しています。 ときに`Option Strict`は`On`します。  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 次の例は、結果を示しています。 ときに`Option Strict`は`Off`します。  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 あいまいさを排除するために使用する必要があります、`&`演算子の代わりに`+`連結します。  
  
## <a name="see-also"></a>関連項目

- [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
