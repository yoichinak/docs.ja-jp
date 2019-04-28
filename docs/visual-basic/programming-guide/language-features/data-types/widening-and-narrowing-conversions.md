---
title: 拡大変換と縮小変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: 9f1a71e8e2e3e4ebb9b412be74b5ea8702eb164f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61827159"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>拡大変換と縮小変換 (Visual Basic)
型変換で重要な考慮事項は、変換の結果が変換先のデータ型の範囲内かどうか。  
  
 A*拡大変換*元のデータのすべての値の許容されるデータ型に値を変更します。  拡大変換では、ソース値を保持するが、その表現を変更できます。 これは、型から整数型へ変換する場合に発生`Decimal`からまたは`Char`に`String`します。  
  
 *縮小変換* により、有効値の一部を保持できない可能性のあるデータ型に値が変更されます。 たとえば、小数部の値は整数型、およびに変換する数値型に変換されるときに丸められます`Boolean`がいずれかに減少する`True`または`False`します。  
  
## <a name="widening-conversions"></a>拡大変換  
 次の表では、標準の拡大変換を示します。  
  
|データの種類|データ型に拡大変換されます<sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、`Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|いずれかの列挙型 ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|基になる整数型と任意の型を基になる型拡大変換されます。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` 配列|`Char` 配列、 `String`|  
|任意の型|[Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|すべての派生型|いずれかの基本データ型の派生元である<sup>3</sup>します。|  
|任意の型|任意のインターフェイスを実装します。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任意のデータ型またはオブジェクトの種類。|  
  
 <sup>1</sup>定義では、すべてのデータ型は自動的に拡大します。  
  
 <sup>2</sup>から変換`Integer`、 `UInteger`、 `Long`、 `ULong`、または`Decimal`に`Single`または`Double`大きさが失われることはありませんが、精度が失われる可能性があります。 この意味ではない情報の損失がかかります。  
  
 <sup>3</sup>派生型からその基本型のいずれかへの変換を広げることは驚くかもしれません。 理由は、派生型には、基本型のインスタンスとして扱うことのように、基本の型のすべてのメンバーが含まれています。 方向が逆に、基本データ型では、派生型によって定義されたメンバーは含まれません。  
  
 拡大変換では、実行時に常に成功して、データの損失が発生することはありません。 暗黙的に常に実行して、かどうか、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)型チェック スイッチを設定`On`または`Off`します。  
  
## <a name="narrowing-conversions"></a>縮小変換  
 標準の縮小変換を以下に示します。  
  
- (すべての型は、自動的に拡大) する点を除いて、前の拡大変換の逆の方向がテーブルにします。  
  
- いずれかの方向との間で変換[ブール](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)と任意の数値型  
  
- 列挙型の任意の数値型からいずれかへの変換 (`Enum`)  
  
- いずれかの方向との間で変換[文字列](../../../../visual-basic/language-reference/data-types/string-data-type.md)と任意の数値型`Boolean`、または[日付](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
- それから派生した型にデータ型またはオブジェクトからの変換の入力します。  
  
 縮小変換は常にではありません、実行時に成功し失敗したり、データ損失が発生できます。 エラーは、先のデータ型に変換される値を受信できない場合に発生します。 たとえば、数値変換が、オーバーフローがあります。 コンパイラでは許可しない限り、暗黙的に縮小変換を実行することできません、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)型チェック スイッチを設定`Off`します。  
  
> [!NOTE]
>  縮小変換エラーが抑制されて内の要素からの変換、`For Each…Next`ループ コントロール変数のコレクション。 詳細と例については、"Narrowing Conversions"セクションを参照してください[ごとにしています。。。次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。  
  
### <a name="when-to-use-narrowing-conversions"></a>縮小変換を使用する場合  
 元の値は、エラーまたはデータ損失のない変換先のデータ型に変換できることがわかっている場合は、縮小変換を使用します。 ある場合など、`String`使用できますがわかっている"True"または"False"のいずれかが含まれています、`CBool`に変換キーワード`Boolean`します。  
  
## <a name="exceptions-during-conversion"></a>変換中に例外  
 拡大変換を常にあるため、成功しますが、例外をスローしないでください。 失敗したときに、縮小変換は、最もよく、次の例外をスローします。  
  
- <xref:System.InvalidCastException> -2 つの型の間で変換が定義されていない場合  
  
- <xref:System.OverflowException> -(整数型の場合のみ)、指定した型の変換後の値が大きすぎる場合  
  
 クラスまたは構造体が定義されている場合、 [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)そのクラスまたは構造体、または変換演算子として機能するを`CType`適切と見なされるすべての例外をスローすることができます。 さらを`CType`Visual Basic の関数を呼び出すことがありますまたは[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メソッドで、さらに、さまざまな例外をスローする可能性があります。  
  
## <a name="changes-during-reference-type-conversions"></a>参照型の変換中の変更  
 変換、*参照型*ポインターだけが、値をコピーします。 値そのものがコピーも、何らかの方法で変更します。 変更できることだけでは、ポインターを保持する変数のデータ型です。 次の例では、データ型は、派生クラスから、その基底クラスに変換されますが、両方の変数をポイントするようになりましたオブジェクトは変更されません。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [方法: オブジェクトを Visual Basic で別の型に変換します。](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
