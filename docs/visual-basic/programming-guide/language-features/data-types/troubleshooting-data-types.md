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
ms.openlocfilehash: 851be5bdf4a3adced724dc2df33657a84226270d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818853"
---
# <a name="troubleshooting-data-types-visual-basic"></a>データ型のトラブルシューティング (Visual Basic)
このページには、組み込みデータ型の操作を実行するときに発生する一般的な問題が一覧表示されます。  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>浮動小数点式が等しいと比較しないでください。  
 浮動小数点数を使用する場合 ([Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)と[Double データ型](../../../../visual-basic/language-reference/data-types/double-data-type.md))を扱うときは、二進小数として格納されることに注意してください。 つまり、二進小数ではない（k /（2 ^ n）の形式で、k と n は整数）数量を正確に表すことはできません。 たとえば、0.5 (1/2 =) および 0.3125 (= 5/16) は正確な値として保持できますが、0.2（= 1/5）、0.3 （= 3/10）は 近似値にしかなりません。  
  
 このため、誤差に依存できない正確な結果浮動小数点値を操作するときにします。 具体的には、理論的に等しい 2 つの値には、若干異なる表現があります。  
  
| 浮動小数点の値を比較するには | 
|---| 
|1.使用して、その差の絶対値を計算、<xref:System.Math.Abs%2A>のメソッド、<xref:System.Math>クラス、<xref:System>名前空間。<br />2.許容される最大限の差を決めますに実用的な目的の場合、その違いは、サイズは、2 つの数量を検討することができます。<br />3.許容される相違点に差の絶対値を比較します。|  
  
 次の例では、2 つの正しくないと、適切な比較`Double`値。  
  
 [!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]  
  
 前の例では、<xref:System.Double.ToString%2A>のメソッド、<xref:System.Double>より精度を指定できるように構造体、`CStr`キーワードを使用します。 既定値は 15 桁の数字が、"G17"書式が 17 桁に拡張します。  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod 演算子には、正確な結果は返しません。  
 浮動小数点のストレージでの誤差のため、 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)が浮動小数点型のオペランドの少なくとも 1 つと、予期しない結果を返すことができます。  
  
 [Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)浮動小数点表現を使用しません。 正確で多くの数値`Single`と`Double`で正確では`Decimal`(0.2、0.3 など)。 演算で低速`Decimal`よりで浮動小数点、その価値があります精度の向上を実現するために、パフォーマンスが低下します。  
  
|浮動小数点数の整数の剰余を検索するには|  
|---|  
|1.変数として宣言`Decimal`します。<br />2.リテラルの型文字を使用して、`D`にリテラルを強制的に`Decimal`の値が大きすぎる場合、`Long`データ型。|  
  
 次の例では、浮動小数点のオペランドの誤差の可能性を示します。  
  
 [!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]  
  
 前の例では、<xref:System.Double.ToString%2A>のメソッド、<xref:System.Double>より精度を指定できるように構造体、`CStr`キーワードを使用します。 既定値は 15 桁の数字が、"G17"書式が 17 桁に拡張します。  
  
 `zeroPointTwo`は`Double`、その値を 0.2 には、無限に繰り返される 0.20000000000000001 として格納されている値を持つバイナリ小数部分。 この数量 2.0 で除算 0.19999999999999991 となりますの残りの部分で 9.9999999999999995 を生成します。  
  
 式で`decimalRemainder`、リテラルの型文字`D`強制的にオペランドは両方とも`Decimal`0.2 であり、正確に表現します。 そのため、`Mod`演算子が 0.0 の予想される残りの部分を生成します。  
  
 宣言するための十分ながないことに注意してください。`decimalRemainder`として`Decimal`します。 リテラルを強制することも必要があります。 `Decimal`、使用することも`Double`既定と`decimalRemainder`として同じ不正確な値を受け取る`doubleRemainder`します。  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Boolean データで正確な数値型に変換されません。  
 [Boolean データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)値は、数値として格納されず、格納された値は数値と同等であることを意図していません。 以前のバージョンとの互換性のために、Visual Basic には、`Boolean`と数値型の間の変換を行うための変換キーワード ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)、 `CBool`、`CInt`など) が用意されています。 ただし、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メソッドと同様に、他の言語でもこれらの変換の実行方法が異なる場合があります。  
  
 数値と等価の値に依存するコードを記述する必要がありますしない`True`と`False`します。 使用を制限する必要があります、可能な限り`Boolean`変数を論理値に設計されています。 組み合わせる必要がある場合`Boolean`数値、選択した変換の方法を理解することを確認します。  
  
### <a name="conversion-in-visual-basic"></a>Visual Basic での変換  
 使用すると、`CType`または`CBool`数値データ型に変換する変換キーワード`Boolean`、0 になります`False`他のすべての値になると`True`します。 変換する際に`Boolean`値を変換のキーワードを使用して、数値型に`False`が 0 になると`True`-1 になります。  
  
### <a name="conversion-in-the-framework"></a>フレームワークでの変換  
 <xref:System.Convert.ToInt32%2A>のメソッド、<xref:System.Convert>クラス、<xref:System>名前空間に変換します`True`は +1。  
  
 変換する必要があります場合、`Boolean`値、数値データ型を注意を使用する変換メソッド。  
  
## <a name="character-literal-generates-compiler-error"></a>文字リテラルには、コンパイラ エラーが生成されます。  
 任意の型文字がない場合、Visual Basic によって、リテラルのデータ型が既定に前提とします。 リテラル文字の既定の型: 引用符で囲む (`" "`) — は`String`します。  
  
 `String`データ型に拡大変換されない、 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)します。 つまり、リテラルを割り当てる場合、`Char`変数、する必要がありますか、縮小変換、または強制的にリテラル、`Char`型。  

|Char 型の変数または定数に割り当てるリテラルを作成するには|
|---|  
|1.変数または定数として宣言`Char`します。<br />2.文字の値を引用符で囲みます (`" "`)。<br />3.次のリテラルの型文字と終わりの二重引用符`C`にリテラルを強制的に`Char`します。 これは型チェック スイッチの場合に必要です ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`、いずれの場合も必要があるとします。|  
  
 次の例は、リテラルを成功、失敗の割り当て、`Char`変数。  
  
 [!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]  
  
 常にリスクが縮小の変換を使用して実行時にそれらが失敗する可能性です。 変換など、`String`に`Char`が失敗する場合、`String`値には、1 つ以上の文字が含まれています。 そのため、それを使用するプログラミングがより、`C`文字を入力します。  
  
## <a name="string-conversion-fails-at-run-time"></a>String の変換は実行時に失敗します。  
 [文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)がごく少数の拡大変換に参加します。 `String` 自体にのみ拡大変換と`Object`とのみ`Char`と`Char()`(、`Char`配列) に拡大変換`String`。 これは、ため`String`変数と定数は、他のデータ型を含めることはできませんの値を含めることができます。  
  
 型チェックを切り替えると ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`コンパイラには、すべての暗黙的な縮小変換が許可されていません。 関連するものが含まれます`String`します。 コードの変換キーワードをなど、使用もできる`CStr`と[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)、どのダイレクト、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]変換を試みます。  
  
> [!NOTE]
>  縮小変換エラーが抑制されて内の要素からの変換、`For Each…Next`ループ コントロール変数のコレクション。 詳細と例については、"Narrowing Conversions"セクションを参照してください[ごとにしています...次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。  
  
### <a name="narrowing-conversion-protection"></a>縮小変換の保護  
 縮小変換の欠点は、ことは、実行時に失敗したことができます。 たとえば場合、`String`変数のものを含む"True"または"False"に変換できない以外`Boolean`します。 区切り文字が含まれている、任意の数値型への変換は失敗します。 あるとわかっている場合を除き、`String`変数変換先の型を受け入れることができる値を常に保持する、変換しないでください。  
  
 変換する必要がある場合`String`を別のデータ型では、最も安全な手順で実行しようとした変換を囲む、[Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。 これにより、実行時エラーに対処できます。  
  
### <a name="character-arrays"></a>文字配列  
 1 つ`Char`と配列の`Char`要素の両方に拡大変換する`String`します。 ただし、`String`に拡大変換されない`Char()`します。 変換する、`String`値を`Char`使用することができます、配列、<xref:System.String.ToCharArray%2A>のメソッド、<xref:System.String?displayProperty=nameWithType>クラス。  
  
### <a name="meaningless-values"></a>意味のない値  
 一般に、`String`値他のデータ型では意味がなく、変換は非常に危険です。 可能な限り`String`の使用をそれらが設計されている文字シーケンスに制限する必要があります。 その他の種類に対応する値に依存するコードを書かないようにしてください。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [データ型の有効な使用方法](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
