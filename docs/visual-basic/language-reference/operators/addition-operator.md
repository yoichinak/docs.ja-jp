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
ms.openlocfilehash: ab18a7137a31ed8e616f465e7d617305c96d7b10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943025"
---
# <a name="-operator-visual-basic"></a>+ 演算子 (Visual Basic)
2つの数値を加算するか、数値式の正の値を返します。 は、2つの文字列式を連結するためにも使用できます。  
  
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
|`expression2`|`+`演算子が負の値を計算する場合を除き、必須です。 任意の数値または文字列式。|  
  
## <a name="result"></a>結果  
 と`expression1`が`expression2`両方とも数値の場合、結果は算術和になります。  
  
 が`expression2`存在しない場合`+` 、演算子は、式の変更されていない値の*単項*id 演算子です。 この意味では、操作はの`expression1`符号を保持することで構成されます。したがって、が負の場合`expression1` 、結果は負になります。  
  
 と`expression1`が`expression2`両方とも文字列の場合、結果はそれらの値を連結したものになります。  
  
 と`expression1`の`expression2`型が混在している場合、実行される操作は、その型、内容、および[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)の設定によって異なります。 詳細については、「解説」の表を参照してください。  
  
## <a name="supported-types"></a>サポートされている型  
 符号なしの型および浮動小数点型`Decimal`、、および`String`を含む、すべての数値型。  
  
## <a name="remarks"></a>Remarks  
 一般に、 `+`は、可能な場合は算術加算を実行し、両方の式が文字列である場合にのみ連結します。  
  
 どちらの式`Object`もでない場合、Visual Basic は次の操作を実行します。  
  
|式のデータ型|コンパイラによるアクション|  
|---|---|  
|両方の式は`SByte` 、数値`UInteger`データ型`Byte`(、 `UShort` `Integer` `Short` 、、`Long`、、、、、、 `Double`、または) です。 `ULong` `Decimal` `Single`|アドイン. 結果のデータ型は、および`expression1` `expression2`のデータ型に適した数値型です。 「[演算子の結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「整数演算」の表を参照してください。|  
|両方の式の型はです。`String`|つなげ.|  
|一方の式は数値データ型で、もう一方は文字列です。|`Option Strict` が`On`の場合は、コンパイラエラーを生成します。<br /><br /> が`Option Strict` `String`の場合は、をに暗黙的`Double`に変換し、を追加します。 `Off`<br /><br /> <xref:System.InvalidCastException>をに`Double`変換できない場合は、例外をスローします。 `String`|  
|1つの式は数値データ型であり、もう一方は[Nothing](../../../visual-basic/language-reference/nothing.md)です。|を0と`Nothing`して値を追加します。|  
|1つの式が文字列で、もう一方は`Nothing`|`Nothing`値を "" として連結します。|  
  
 1つの式が`Object`式の場合、Visual Basic は次のアクションを実行します。  
  
|式のデータ型|コンパイラによるアクション|  
|---|---|  
|`Object`式は数値を保持し、もう一方は数値データ型です。|`Option Strict` が`On`の場合は、コンパイラエラーを生成します。<br /><br /> `Option Strict` が`Off`の場合は、を追加します。|  
|`Object`式は数値を保持し、もう一方は型です。`String`|`Option Strict` が`On`の場合は、コンパイラエラーを生成します。<br /><br /> が`Option Strict` `String`の場合は、をに暗黙的`Double`に変換し、を追加します。 `Off`<br /><br /> <xref:System.InvalidCastException>をに`Double`変換できない場合は、例外をスローします。 `String`|  
|`Object`式は文字列を保持し、もう1つは数値データ型です。|`Option Strict` が`On`の場合は、コンパイラエラーを生成します。<br /><br /> が`Option Strict` `Object` `Double`の場合は、文字列をに暗黙的に変換し、を追加します。 `Off`<br /><br /> 文字列`Object`をに`Double`変換できない場合は、 <xref:System.InvalidCastException>例外をスローします。|  
|`Object`式は文字列を保持し、もう一方は型です。`String`|`Option Strict` が`On`の場合は、コンパイラエラーを生成します。<br /><br /> が`Option Strict`の場合、はに`Object`暗黙的`String`に変換され、連結さ`Off`れます。|  
  
 両方の式が`Object`式の場合、Visual Basic は次の`Option Strict Off`操作を実行します (のみ)。  
  
|式のデータ型|コンパイラによるアクション|  
|---|---|  
|両方`Object`の式が数値を保持します|アドイン.|  
|両方`Object`の式の型はです。`String`|つなげ.|  
|一方`Object`の式は数値を保持し、もう一方は文字列を保持します。|文字列`Object`をに暗黙的に`Double`変換し、を追加します。<br /><br /> 文字列`Object`を数値に変換できない場合は、 <xref:System.InvalidCastException>例外をスローします。|  
  
 いずれか`Object`の式が[Nothing](../../../visual-basic/language-reference/nothing.md)また<xref:System.DBNull>はに`+`評価される場合、 `String`演算子は、値が "" であるとして処理します。  
  
> [!NOTE]
> `+`演算子を使用すると、加算または文字列の連結が行われるかどうかを判断できない場合があります。 `&`演算子を連結に使用して、あいまいさをなくし、自己記述型のコードを提供します。  
  
## <a name="overloading"></a>オーバーロード  
 演算子はオーバーロードできます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 `+` コードでこのようなクラスまたは構造体に対してこの演算子を使用する場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では`+` 、演算子を使用して数値を追加します。 オペランドが両方とも数値の場合、Visual Basic 演算結果が計算されます。 算術結果は、2つのオペランドの合計を表します。  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 また、演算子を使用`+`して文字列を連結することもできます。 オペランドが両方とも文字列の場合は、Visual Basic 連結します。 連結の結果は、2つのオペランドの内容で構成される1つの文字列を表します。  
  
 オペランドが混合型の場合、結果は[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)の設定によって異なります。 次の例は、が`Option Strict` `On`の場合の結果を示しています。  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 次の例は、が`Option Strict` `Off`の場合の結果を示しています。  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 あいまいさをなくすには、の`&` `+`代わりに演算子を使用する必要があります。  
  
## <a name="see-also"></a>関連項目

- [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Visual Basic の算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
