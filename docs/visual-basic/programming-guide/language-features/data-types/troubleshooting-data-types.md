---
title: データ型のトラブルシューティング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 5b2cb0d5270b7e14c3462aeaf54942f939511fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933231"
---
# <a name="troubleshooting-data-types-visual-basic"></a>データ型のトラブルシューティング (Visual Basic)
このページでは、組み込みデータ型に対して操作を実行するときに発生する可能性がある一般的な問題をいくつか示します。  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>浮動小数点式は等しいと比較されません  
 浮動小数点数を使用する場合 ([Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)と[Double データ型](../../../../visual-basic/language-reference/data-types/double-data-type.md))を扱うときは、二進小数として格納されることに注意してください。 つまり、二進小数ではない（k /（2 ^ n）の形式で、k と n は整数）数量を正確に表すことはできません。 たとえば、0.5 (1/2 =) および 0.3125 (= 5/16) は正確な値として保持できますが、0.2（= 1/5）、0.3 （= 3/10）は 近似値にしかなりません。  
  
 このおける誤差により、浮動小数点値を操作するときに正確な結果を利用することはできません。 特に、理論的に等しい2つの値の表現は多少異なる場合があります。  
  
| 浮動小数点の数量を比較するには | 
|---| 
|1.名前空間の<xref:System.Math.Abs%2A> <xref:System.Math>クラスのメソッドを使用して、違いの絶対値を計算します。 <xref:System><br />2.許容される最大の差を判断します。これにより、2つの数量を実際の目的のために等しいと見なすことができます。<br />3.差の絶対値と許容される差を比較します。|  
  
 次の例では、2つ`Double`の値の誤った比較と正しい比較を示します。  
  
 [!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]  
  
 前の例では<xref:System.Double.ToString%2A> 、 <xref:System.Double>構造体のメソッドを使用して、 `CStr`キーワードが使用するよりも高い精度を指定できるようにしています。 既定値は15桁ですが、"G17" の形式は17桁に拡張されます。  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod 演算子が正確な結果を返しません  
 浮動小数点型ストレージのおける誤差のため、少なくとも1つのオペランドが浮動小数点である場合、 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)は予期しない結果を返すことがあります。  
  
 [Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)では、浮動小数点表現は使用されません。 とで`Single`正確ではない多くの数値は`Decimal` 、 `Double` (0.2 と0.3 など) に正確になります。 浮動小数点`Decimal`よりも算術の方が遅くなりますが、精度を高めるためにパフォーマンスが低下する可能性があります。  
  
|浮動小数点数値の剰余を求めるには|  
|---|  
|1.変数をと`Decimal`して宣言します。<br />2.リテラルを`D` `Decimal`強制的に使用するには、リテラルの型文字を使用します。値`Long`がデータ型に対して大きすぎる場合に使用します。|  
  
 次の例は、浮動小数点オペランドのおける誤差の可能性を示しています。  
  
 [!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]  
  
 前の例では<xref:System.Double.ToString%2A> 、 <xref:System.Double>構造体のメソッドを使用して、 `CStr`キーワードが使用するよりも高い精度を指定できるようにしています。 既定値は15桁ですが、"G17" の形式は17桁に拡張されます。  
  
 `zeroPointTwo` は`Double`であるため、0.2 の値は、0.20000000000000001 の値が格納されている無限の連続するバイナリ部分です。 2\.0 をこの数量で割ると、9.9999999999999995 が0.19999999999999991 になります。  
  
 の`decimalRemainder`式では、リテラルの型文字`D`によって両方`Decimal`のオペランドがに強制され、0.2 に正確な表現が指定されています。 したがって`Mod` 、演算子は0.0 の予想される剰余を生成します。  
  
 として宣言`decimalRemainder`するだけでは不十分であることに注意して`Decimal`ください。 また、リテラルをに強制的に`Decimal`適用するか、 `Double`を既定で`decimalRemainder`使用して、と`doubleRemainder`同じ不正確な値を受け取ります。  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Boolean データで正確な数値型に変換されません。  
 [Boolean データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)値は、数値として格納されず、格納された値は数値と同等であることを意図していません。 以前のバージョンとの互換性のために、Visual Basic には、`Boolean`と数値型の間の変換を行うための変換キーワード ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)、 `CBool`、`CInt`など) が用意されています。 ただし、その他の言語では、.NET Framework メソッドと同様に、これらの変換が異なる方法で実行されることがあります。  
  
 `True` と`False`の等価の数値に依存するコードを記述することは避けてください。 可能な限り、変数の`Boolean`使用は、設計対象の論理値に制限する必要があります。 と数値を混在`Boolean`させる必要がある場合は、選択した変換方法を理解していることを確認してください。  
  
### <a name="conversion-in-visual-basic"></a>Visual Basic での変換  
 `CType`また`Boolean`は`CBool`変換キーワードを使用して数値データ型をに変換すると`False` `True`、0がになり、その他のすべての値がになります。 変換キーワードを`Boolean`使用して値を数値型に変換する`False`と、は`True` 0 になり、-1 になります。  
  
### <a name="conversion-in-the-framework"></a>フレームワークでの変換  
 名前空間の<xref:System.Convert.ToInt32%2A> <xref:System.Convert>クラス`True`のメソッドは、+ 1 に変換されます。 <xref:System>  
  
 値を`Boolean`数値データ型に変換する必要がある場合は、使用する変換方法に注意してください。  
  
## <a name="character-literal-generates-compiler-error"></a>文字リテラルによってコンパイラエラーが生成される  
 型文字が存在しない場合、Visual Basic はリテラルの既定のデータ型を想定します。 引用符 (`" "`) で囲まれた文字リテラルの既定の型は`String`です。  
  
 データ型が[Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)に拡大変換されません。 `String` つまり、 `Char`変数にリテラルを代入する場合は、縮小変換を行うか、リテラルを強制的`Char`に型にする必要があります。  

|変数または定数に代入する Char リテラルを作成するには|
|---|  
|1.変数または定数をと`Char`して宣言します。<br />2.文字値を引用符 (`" "`) で囲みます。<br />3.リテラルの型を`C` `Char`強制的に指定するには、終わりの二重引用符の後にリテラルの型文字を指定します。 これは、型チェックスイッチ ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) が`On`で、どのような場合でも望ましい場合に必要です。|  
  
 次の例では、 `Char`変数へのリテラルの割り当てが失敗したか成功したかを示しています。  
  
 [!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]  
  
 実行時に失敗する可能性があるため、縮小変換の使用には常にリスクがあります。 たとえば、値に複数の`String` `String`文字`Char`が含まれている場合、からへの変換は失敗する可能性があります。 そのため、 `C`型文字を使用する方が適切なプログラミングです。  
  
## <a name="string-conversion-fails-at-run-time"></a>String の変換は実行時に失敗します。  
 [文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)は、非常に多くの拡大変換に関与します。 `String`自体`Object`とだけに拡大変換され`Char` 、 `Char()`と ( `Char`配列) だけが`String`に拡大変換されます。 これは、 `String`変数と定数に他のデータ型に含めることができない値を含めることができるためです。  
  
 型チェックスイッチ ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) がの場合`On`、コンパイラは暗黙的な縮小変換をすべて許可しません。 これには、 `String`に関係するものも含まれます。 コードで[は、など](../../../../visual-basic/language-reference/functions/ctype-function.md)の変換キーワードを`CStr`使用して、.NET Framework が変換を試行するように指定することもできます。  
  
> [!NOTE]
> `For Each…Next`のコレクション内の要素からループ コントロール変数への変換では、縮小変換エラーが抑制されます。 詳細と例については、[For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)の"縮小変換"セクションを参照してください。  
  
### <a name="narrowing-conversion-protection"></a>縮小変換保護  
 縮小変換の欠点は、実行時にエラーが発生する可能性があることです。 たとえば、 `String`変数に "True" または "False" 以外のものが含まれている場合は、 `Boolean`に変換できません。 区切り文字が含まれている場合、任意の数値型への変換は失敗します。 `String`変数が、変換先の型が受け入れることができる値を常に保持していることがわかっている場合を除き、変換を試行しないでください。  
  
 変換する必要がある場合`String`を別のデータ型では、最も安全な手順で実行しようとした変換を囲む、[Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。 これにより、実行時エラーに対処できます。  
  
### <a name="character-arrays"></a>文字配列  
 1つ`Char`のと要素の`Char`配列の両方が`String`に拡大変換されます。 ただし、 `String`はに`Char()`拡大されません。 `String`値を`Char`配列に変換するには、 <xref:System.String?displayProperty=nameWithType>クラスの<xref:System.String.ToCharArray%2A>メソッドを使用します。  
  
### <a name="meaningless-values"></a>意味のない値  
 一般に、`String`値他のデータ型では意味がなく、変換は非常に危険です。 可能な限り`String`の使用をそれらが設計されている文字シーケンスに制限する必要があります。 他の型の同等の値に依存するコードを記述することは避けてください。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [データ型の有効な使用方法](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
