---
title: 型文字 (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: a469a08ebadd77d5abbfa95b270784c9ef534691
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906751"
---
# <a name="type-characters-visual-basic"></a>型文字 (Visual Basic)

だけでなく、宣言ステートメントでデータ型を指定すると、一部のプログラミング要素のデータ型を強制することができます、*文字入力*します。 型文字は、任意の種類の間にある文字がない、要素を直後にする必要があります。

要素の名前の一部でない型の文字。 型文字を使用せず、型文字で定義された要素を参照できます。

## <a name="identifier-type-characters"></a>識別子の型文字

Visual Basic のセットを提供する*識別子の型文字*変数または定数のデータ型を指定する宣言で使用できます。 次の表では、使用状況の例で使用できる識別子の型文字を示します。
  
|識別子の型文字|データの種類|例|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 識別子の型文字が存在しない、 `Boolean`、 `Byte`、 `Char`、 `Date`、 `Object`、 `SByte`、 `Short`、 `UInteger`、 `ULong`、または`UShort`データ型、またはいずれか配列や構造体などの複合データ型。

場合によっては、追加することができます、`$`文字、Visual Basic の関数をたとえば`Left$`の代わりに`Left`、返される型の値を取得する`String`します。

すべてのケースでは、識別子の型文字は、識別子名の直後にする必要があります。

## <a name="literal-type-characters"></a>リテラルの型文字

A*リテラル*データ型の特定の値のテキスト表現です。  

### <a name="default-literal-types"></a>既定のリテラル型

通常、コード内のリテラルの形式によってのデータ型が決まります。 次の表では、これらの既定の型を示します。  
  
|リテラルのテキストの形式|既定のデータ型|例|  
|-----------------------------|-----------------------|-------------|  
|数値の小数部のない部分|`Integer`|`2147483647`|  
|数値のない小数部分、に対して大きすぎます `Integer`|`Long`|`2147483648`|  
|数値の小数部分|`Double`|`1.2`|  
|二重引用符で囲まれています。|`String`|`"A"`|  
|番号記号で囲まれました。|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>リテラル型の強制

Visual Basic のセットを提供する*リテラルの型文字*、強制的に、1 つ以外のデータ型にそのフォームを想定するリテラルに使用できることを示します。 そのためには、リテラルの末尾に文字を追加します。 次の表では、使用状況の例を含む使用可能なリテラルの型文字を示します。
  
|リテラルの型文字|データの種類|例|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

リテラルの型文字が存在しない、 `Boolean`、 `Byte`、 `Date`、 `Object`、 `SByte`、または`String`データ型、または配列や構造体などの任意の複合データ型。

リテラルには、識別子の型文字が使用してもできます (`%`、 `&`、 `@`、 `!`、 `#`、 `$`)、変数、定数、および式のことができます。 ただし、リテラルの型文字 (`S`、 `I`、 `L`、 `D`、 `F`、 `R`、 `C`) リテラルでのみ使用できます。

すべてのケースでは、リテラルの型文字は、リテラル値の直後にする必要があります。

## <a name="hexadecimal-binary-and-octal-literals"></a>16 進数、バイナリ、および 8 進数リテラル

コンパイラは、通常、10 進数 (基数 10) の数である整数リテラルを解釈します。 16 進数 (基数 16) を付けて、整数リテラルを定義することも、`&H`の (基本 2 進数としてのプレフィックス、`&B`プレフィックス、先頭に (基数 8)、8 進数として番号を`&O`プレフィックス。 以降の数字が、プレフィックスは、数のシステムの適切なである必要があります。 次の表は、これを示しています。  
  
|基数|プレフィックス|有効桁の値|例|
|-----------------|------------|------------------------|-------------|
|16 進数 (基数 16)。|`&H`|0-9、A ~ F|`&HFFFF`|
|バイナリ (基本 2)|`&B`|0-1|`&B01111100`|
|8 進数 (基数 8)。|`&O`|0-7|`&O77`|

Visual Basic 2017 から、アンダー スコア文字を使用することができます (`_`) 整数リテラルの読みやすさを強化するために、グループ区切り記号として。 次の例では、`_`バイナリ リテラルを 8 ビットのグループにグループ化する文字。

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

リテラルの型文字とプレフィックスの付いたリテラルに従うことができます。 次の例に示します。

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

前の例では、 `counter` -32768 の 10 進数の値を持つと`flags`+32768 の 10 進数の値を持ちます。

Visual Basic 15.5 以降では、使用することできますもアンダー スコア文字 (`_`) プレフィックスと 16 進数、バイナリ、または 8 進数の桁の間の先頭の区切り記号として。 例:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
