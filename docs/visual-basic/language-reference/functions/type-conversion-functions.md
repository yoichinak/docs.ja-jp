---
title: データ型変換関数 (Visual Basic)
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 2b750f41343a4a68e29af6055815efd1e6470252
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816266"
---
# <a name="type-conversion-functions-visual-basic"></a>データ型変換関数 (Visual Basic)
これらの関数は、インラインでのコンパイル、つまり、変換コード式を評価するコードの一部です。 場合によってパフォーマンスを向上させると、変換を実行するプロシージャの呼び出しではありません。 各関数は、特定のデータ型に式を変換します。  
  
## <a name="syntax"></a>構文  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## <a name="part"></a>パーツ  
 `expression`  
 必須。 ソースのデータ型の任意の式。  
  
## <a name="return-value-data-type"></a>戻り値のデータ型  
 関数名は、次の表に示すように、返す値のデータ型を決定します。  
  
|関数名|戻り値のデータ型|範囲を指定`expression`引数|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任意の有効な`Char`または`String`または数値式です。|  
|`CByte`|[Byte データ型](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) を通じて<xref:System.Byte.MaxValue?displayProperty=nameWithType>(255) (未署名) 小数部は丸められます。<sup> 。1</sup><br/><br/>Visual Basic 15.8 以降、Visual Basic で浮動小数点数バイトを使用する変換からのパフォーマンスを最適化、`CByte`関数です。 はを参照してください、[解説](#remarks)詳細についてはします。 参照してください、 [CInt 例](#cint-example)例については、セクション。|  
|`CChar`|[Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md)|任意の有効な`Char`または`String`式。 の最初の文字のみを`String`変換されます。 値は 0 ~ 65535 (符号なし) を指定できます。|  
|`CDate`|[Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)|任意の有効な日付と時刻の表現。|  
|`CDbl`|[Double 型](../../../visual-basic/language-reference/data-types/double-data-type.md)|-- を 4.94065645841246544E-(負の値)。4.94065645841246544E-324 正の値の 1.79769313486231570 e + 308 ~。|  
|`CDec`|[Decimal データ型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|数字の 0 の 79,228,162,514,264,337,593,543,950,335、+/-小数点以下の桁数は、番号します。 数値の小数点以下桁数が 28 場合、範囲は、7.9228162514264337593543950335 です。 最小の可能な 0 以外の数値は、(1 e ~ 28) +/-0.0000000000000000000000000001 です。|  
|`CInt`|[Integer データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) を通じて<xref:System.Int32.MaxValue?displayProperty=nameWithType>(2,147, 483,647) です小数部は丸められます。<sup> 。1</sup> <br/><br/>Visual Basic 15.8 以降、Visual Basic で浮動小数点数に整数型の変換からのパフォーマンスを最適化、`CInt`関数です。 はを参照してください、[解説](#remarks)詳細についてはします。 参照してください、 [CInt 例](#cint-example)例については、セクション。 |  
|`CLng`|[Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) を通じて<xref:System.Int64.MaxValue?displayProperty=nameWithType>(9,223,372,036,854,775,807) 小数部は丸められます。<sup> 。1</sup><br/><br/>Visual Basic 15.8 以降、Visual Basic で浮動小数点数に 64 ビット整数の変換からのパフォーマンスを最適化、`CLng`関数です。 はを参照してください、[解説](#remarks)詳細についてはします。 参照してください、 [CInt 例](#cint-example)例については、セクション。|  
|`CObj`|[Object 型](../../../visual-basic/language-reference/data-types/object-data-type.md)|任意の有効な式。|  
|`CSByte`|[SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) を通じて<xref:System.SByte.MaxValue?displayProperty=nameWithType>(127) 小数部は丸められます。<sup> 。1</sup><br/><br/>Visual Basic 15.8 以降、Visual Basic で浮動小数点数を使用する符号付きバイト変換からのパフォーマンスを最適化、`CSByte`関数です。 はを参照してください、[解説](#remarks)詳細についてはします。 参照してください、 [CInt 例](#cint-example)例については、セクション。|  
|`CShort`|[Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) を通じて<xref:System.Int16.MaxValue?displayProperty=nameWithType>(32,767) 小数部は丸められます。<sup> 。1</sup><br/><br/>Visual Basic 15.8 以降、Visual Basic で浮動小数点数 16 ビット整数を使用する変換からのパフォーマンスを最適化、`CShort`関数です。 はを参照してください、[解説](#remarks)詳細についてはします。 参照してください、 [CInt 例](#cint-example)例については、セクション。|  
|`CSng`|[Single データ型](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823 e + 38 ~ - 1.401298E-45 の負の値。1.401298E-45 ~ 3.402823 e + 38 の正の値。|  
|`CStr`|[String データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)|返します`CStr`に依存、`expression`引数。 参照してください[CStr 関数の戻り値](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)します。|  
|`CUInt`|[UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) を通じて<xref:System.UInt32.MaxValue?displayProperty=nameWithType>(4,294,967,295) (未署名) 小数部は丸められます。<sup> 。1</sup><br/><br/>Visual Basic 15.8 以降、Visual Basic で浮動小数点数の符号なし整数型の変換からのパフォーマンスを最適化、`CUInt`関数です。 はを参照してください、[解説](#remarks)詳細についてはします。 参照してください、 [CInt 例](#cint-example)例については、セクション。|  
|`CULng`|[ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) を通じて<xref:System.UInt64.MaxValue?displayProperty=nameWithType>(18,446,744,073,709,551,615) (未署名) 小数部は丸められます。<sup> 。1</sup><br/><br/>Visual Basic 15.8 以降、Visual Basic での符号なし長整数に変換する浮動小数点のパフォーマンスを最適化、`CULng`関数です。 はを参照してください、[解説](#remarks)詳細についてはします。 参照してください、 [CInt 例](#cint-example)例については、セクション。|  
|`CUShort`|[UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) を通じて<xref:System.UInt16.MaxValue?displayProperty=nameWithType>(65,535) (未署名) 小数部は丸められます。<sup> 。1</sup><br/><br/>Visual Basic 15.8 以降、Visual Basic で浮動小数点数 16 ビット符号なし整数を使用する変換からのパフォーマンスを最適化、`CUShort`関数です。 はを参照してください、[解説](#remarks)詳細についてはします。 参照してください、 [CInt 例](#cint-example)例については、セクション。|  
  
 <sup>1</sup>小数部分は、特殊な種類と呼ばれる丸め処理を行うを受けることができます*銀行型丸め*します。 詳細については、「解説」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 原則として、する必要がありますを使用する方が優先的 .NET Framework のメソッドは、Visual Basic の型変換関数など`ToString()`、いずれかで、<xref:System.Convert>クラスまたは個々 の型の構造体またはクラスにします。 Visual Basic の関数は、Visual Basic コードの最適な対話のために設計されていて、ソース コードを短く読みやすくすることも、します。 さらに、.NET Framework の変換メソッドは常に結果を生成しない、同じ例では変換するときに、Visual Basic の関数として`Boolean`に`Integer`します。 詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)します。  


Visual Basic 15.8 から始めてに渡すときに、浮動-小数点からに整数型の変換のパフォーマンスは最適化された、<xref:System.Single>または<xref:System.Double>整数変換関数のいずれかに、次のメソッドによって返される値 (`CByte`、 `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

この最適化を行うコードを 2 回ほど高速に実行する整数の変換の数が多い。 次の例は、最適化された浮動-小数点 integer 型変換を示しています。

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a>動作  
  
-   **強制型変換。** 一般に、既定のデータ型ではなく、特定のデータ型を操作の結果を強制的にデータ型の変換関数を使用することができます。 たとえば、使用して`CDec`単精度、倍精度、または整数演算が通常行う場所の場合の 10 進数の演算を強制的にします。  
  
-   **変換の失敗。** 場合、`expression`先は、変換されるデータ型の範囲外は、関数に渡される、<xref:System.OverflowException>に発生します。  
  
-   **小数部分。** 整数以外の値を整数に変換すると、型、整数の変換関数 (`CByte`、 `CInt`、 `CLng`、 `CSByte`、 `CShort`、 `CUInt`、 `CULng`、および`CUShort`) を削除します小数部し、を最も近い整数値に切り上げられます。  
  
     小数部が正確に場合は 0.5、整数の変換関数に丸める、近い偶数の整数。 たとえば、0.5 は、0、および 1.5 および 2.5 は 2 にどちらに丸められます。 これと呼ぶことが*銀行型丸め*目的は、このような多くの数値を一緒に追加するときに蓄積する偏りを補正するためにします。  
  
     `CInt` `CLng`とは異なる、<xref:Microsoft.VisualBasic.Conversion.Int%2A>と<xref:Microsoft.VisualBasic.Conversion.Fix%2A>切り上げるには、数値の小数部ではなく、切り捨て関数。 また、`Fix`と`Int`内を通過すると常に同じデータ型の値を返します。  
  
-   **日付/時刻の変換。** 使用して、<xref:Microsoft.VisualBasic.Information.IsDate%2A>値を日付と時刻に変換できるかどうかを判断する関数。 `CDate` リテラルの日付と時刻リテラルが数値以外の値を認識します。 Visual Basic 6.0 を変換する`Date`値を`Date`Visual Basic 2005 での値、または以降のバージョンを使用できます、<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>メソッド。  
  
-   **中立的な日付/時刻値。** [Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)常に 日付と時刻の両方の情報が含まれます。 型変換のために、Visual Basic であると見なす 1/1/0001 (年 1 月 1日年 1 月)、*ニュートラル値*を時間のニュートラル値の日付、および 00時 00分: 00 (午前 0 時)。 変換する場合、`Date`値を文字列では、`CStr`結果の文字列に基準値を含めません。 たとえば、変換する`#January 1, 0001 9:30:00#`結果は"9時 30分: 00 AM"を文字列には、日付情報は表示されません。 ただし、日付情報は、元に引き続き存在`Date`値し、などの関数で回復できる<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>関数。  
  
-   **カルチャの区別。** 文字列に関係する型変換関数は、アプリケーションの現在のカルチャ設定に基づいて変換を実行します。 たとえば、`CDate`システムのロケール設定に従って日付形式を認識します。 日、月、および使用されるロケールの正しい順序で年を指定するか、日付が正しく解釈されない可能性があります。 長い日付形式は、"Wednesday"などの曜日の文字列が含まれている場合は認識されません。  
  
     または現在のロケールで指定した以外の形式で値の文字列形式からに変換する必要がある場合は、Visual Basic の型変換関数を使用することはできません。 これを行うには、使用、`ToString(IFormatProvider)`と`Parse(String, IFormatProvider)`値の型のメソッド。 などを使用して、<xref:System.Double.Parse%2A?displayProperty=nameWithType>を文字列に変換するときに、`Double`を使用して<xref:System.Double.ToString%2A?displayProperty=nameWithType>型の値を変換するときに`Double`文字列にします。  
  
## <a name="ctype-function"></a>CType Function  
 [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) 2 番目の引数を受け取り`typename`、型に変換および`expression`に`typename`ここで、`typename`任意のデータ型、構造体、クラス、またはインターフェイスの有効な変換が存在することができます。  
  
 比較について`CType`他の型変換キーワードで、次を参照してください。 [DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)と[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)します。  
  
## <a name="cbool-example"></a>CBool 例  
 次の例では、`CBool`関数を式に変換する`Boolean`値。 式が 0 以外の値に評価される場合`CBool`返します`True`。 それ以外を返します`False`します。  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a>CByte 例  
 次の例では、`CByte`関数を式に変換する、`Byte`します。  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a>Cchar 関数の例  
 次の例では、`CChar`関数の最初の文字に変換する、`String`に式を`Char`型。  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 入力引数`CChar`データ型でなければなりません`Char`または`String`します。 使用することはできません`CChar`ため文字に数値を変換する`CChar`数値データ型を受け入れることはできません。 次の例では、コード ポイント (文字コード) を表す数値を取得し、対応する文字に変換します。 使用して、<xref:Microsoft.VisualBasic.Interaction.InputBox%2A>桁の数字の文字列を取得する関数`CInt`入力文字列に変換する`Integer`、および`ChrW`入力数に変換する`Char`します。  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a>Cdate 関数の例  
 次の例では、`CDate`に文字列を変換する関数`Date`値。 一般に、ハードコーディングされた日付と時刻を (この例で示す) のように文字列としては推奨されません。 日付リテラルと #Feb 12、1969 # などの時刻のリテラルを使用し、# 4時 45分: 23 PM #、代わりにします。  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a>Cdbl 関数の例  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a>CDec 例  
 次の例では、`CDec`関数を数値に変換する`Decimal`します。  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a>CInt 例  
 次の例では、`CInt`値を変換する関数`Integer`します。  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a>CLng 例
 次の例では、`CLng`値に変換する関数`Long`します。  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a>CObj 例  
 次の例では、`CObj`関数を数値に変換する`Object`します。 `Object`変数自体を指す 4 バイト ポインターのみが含まれています、`Double`に割り当てられた値。  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a>CSByte 例  
 次の例では、`CSByte`関数を数値に変換する`SByte`します。  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a>CShort 例  
 次の例では、`CShort`関数を数値に変換する`Short`します。  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a>CSng 例  
 次の例では、`CSng`値に変換する関数`Single`します。  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a>Cstr 関数の例  
 次の例では、`CStr`関数を数値に変換する`String`します。  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 次の例では、`CStr`関数に変換する`Date`値`String`値。  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` 常に表示します、`Date`の現在のロケールの標準の短い形式で値"2003 年 6 月 15 4時 35分: 47 PM"です。 ただし、`CStr`抑制、*ニュートラル値*1/1/0001 から、日付と時刻の 00時 00分: 00 の。  
  
 によって返される値の詳細については`CStr`を参照してください[CStr 関数の戻り値](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)します。  
  
## <a name="cuint-example"></a>CUInt 例  
 次の例では、`CUInt`関数を数値に変換する`UInteger`します。  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a>CULng 例  
 次の例では、`CULng`関数を数値に変換する`ULong`します。  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a>CUShort 例  
 次の例では、`CUShort`関数を数値に変換する`UShort`します。  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [変換関数](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
