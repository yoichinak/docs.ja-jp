---
title: 暗黙の型変換と明示的な型変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 4bcf2d76a2983294f244b72f286842a92fb5e64e
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512867"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>暗黙の型変換と明示的な型変換 (Visual Basic)

暗黙の型*変換*では、ソースコードに特別な構文は必要ありません。 次の例では、Visual Basic をに`k` `q`代入する前に、の値を単精度浮動小数点値に暗黙的に変換します。

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

*明示的な変換*では、型変換キーワードを使用します。 Visual Basic には、かっこ内の式を目的のデータ型に強制的に変換するいくつかのキーワードが用意されています。 これらのキーワードは関数と同様に機能しますが、コンパイラによってインラインでコードが生成されるため、関数呼び出しの場合よりも実行速度が若干速くなります。

前の例の次の拡張機能では`CInt` 、キーワードをに`k`代入`q`する前に、の値を整数に変換します。

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a>変換キーワード

次の表は、使用可能な変換キーワードを示しています。

|型変換キーワード|式をデータ型に変換します。|変換する式の許容データ型|
|---|---|---|
|`CBool`|[Boolean データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および列挙型を含む`String`)、、`Object`|
|`CByte`|[Byte データ型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|任意の数値型 ( `SByte`および列挙型を含む`Boolean`) `String`、、、`Object`|
|`CChar`|[Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|
|`CDate`|[Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|
|`CDbl`|[Double 型](../../../../visual-basic/language-reference/data-types/double-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|
|`CDec`|[Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|
|`CInt`|[Integer データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|
|`CLng`|[Long データ型](../../../../visual-basic/language-reference/data-types/long-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|
|`CObj`|[Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)|任意の型|
|`CSByte`|[SByte データ型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|任意の数値型 ( `Byte`および列挙型を含む`Boolean`) `String`、、、`Object`|
|`CShort`|[Short データ型](../../../../visual-basic/language-reference/data-types/short-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|
|`CSng`|[Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|
|`CStr`|[String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および列挙型を含む`Boolean`) `Char`、 `Char` 、、 `Date`array、、`Object`|
|`CType`|コンマ (`,`) の後に指定された型|基本*データ型*(基本型の配列を含む) に変換する場合、対応する conversion キーワードで許可されているものと同じ型です。<br /><br /> *複合データ型*に変換する場合、それが実装するインターフェイスと継承元のクラス<br /><br /> オーバーロード`CType`されたクラスまたは構造体に変換する場合、そのクラスまたは構造体|
|`CUInt`|[UInteger データ型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|
|`CULng`|[ULong データ型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|
|`CUShort`|[UShort データ型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|任意の数値型 ( `Byte`、 `SByte`、および`String`列挙型を含む`Boolean`)、、、`Object`|

## <a name="the-ctype-function"></a>CType 関数

[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)は、2つの引数を操作します。 1つ目は変換される式で、2番目は変換先のデータ型またはオブジェクトクラスです。 最初の引数は型ではなく、式である必要があることに注意してください。

`CType`は*インライン関数*です。つまり、コンパイルされたコードは、多くの場合、関数呼び出しを生成せずに変換を行います。 これにより、パフォーマンスが向上します。

`CType`と他の型変換キーワードの比較については、「 [DirectCast operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast operator](../../../../visual-basic/language-reference/operators/trycast-operator.md)」を参照してください。

### <a name="elementary-types"></a>基本型

次の例は、`CType` の使い方を示しています。

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a>複合型

を使用`CType`すると、値を複合データ型だけでなく基本型にも変換できます。 また、次の例のように、このメソッドを使用して、オブジェクトクラスをそのインターフェイスの1つの型に強制的に変換することもできます。

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a>配列型

`CType`次の例のように、配列のデータ型を変換することもできます。

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

詳細と例については、「[配列の変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)」を参照してください。

### <a name="types-defining-ctype"></a>CType を定義する型

定義した`CType`クラスまたは構造体に対してを定義できます。 これにより、クラスまたは構造体の型との間で値を変換できます。 詳細と例については、 [「方法:変換演算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)を定義します。

> [!NOTE]
> 変換キーワードと共に使用する値は、変換先のデータ型に対して有効でなければなりません。または、エラーが発生します。 たとえば`Long` 、を`Integer`に変換しようとした場合、の`Long`値は、 `Integer`データ型の有効な範囲内である必要があります。

> [!CAUTION]
> ソース`CType`型が変換先の型から派生していない場合、実行時に、あるクラス型から別の型に変換するように指定すると、が失敗します。 このようなエラーが<xref:System.InvalidCastException>発生すると、例外がスローされます。

ただし、型のいずれかが定義した構造体またはクラスであり、その構造体`CType`またはクラスでを定義している場合、 `CType`の要件を満たすと、変換が成功する可能性があります。 「[方法:変換演算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)を定義します。

明示的な変換を実行することは、特定のデータ型またはオブジェクトクラスに式を*キャスト*することとも呼ばれます。

## <a name="see-also"></a>関連項目

- [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [方法: オブジェクトを Visual Basic 内の別の型に変換する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
