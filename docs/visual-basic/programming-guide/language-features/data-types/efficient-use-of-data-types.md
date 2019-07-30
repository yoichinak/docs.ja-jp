---
title: データ型の有効な使用方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 68371a9f8d4dcc5d0a2b67955d5e88943a83b085
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631108"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>データ型の有効な使用方法 (Visual Basic)
宣言されていない変数およびデータ型を使用`Object`せずに宣言された変数には、データ型が割り当てられます。 これにより、プログラムをすばやく簡単に記述できるようになりますが、実行速度が低下する可能性があります。

## <a name="strong-typing"></a>厳密な型指定
 すべての変数のデータ型を指定することを、*厳密な*型指定と呼びます。 厳密な型指定を使用すると、いくつかの利点があります。

- これにより、変数の IntelliSense サポートが有効になります。 これにより、コードで入力するときに、プロパティや他のメンバーを表示できます。

- コンパイラの型チェックを利用します。 これは、オーバーフローなどのエラーによって実行時に失敗する可能性があるステートメントをキャッチします。 また、サポートされていないオブジェクトのメソッドの呼び出しもキャッチします。

- これにより、コードの実行時間が短縮されます。

## <a name="most-efficient-data-types"></a>最も効率的なデータ型
 分数を含まない変数の場合、整数データ型は非整数型よりも効率的です。 Visual Basic では`Integer` 、 `UInteger`とが最も効率的な数値型です。

 小数部`Double`の場合、は最も効率的なデータ型です。これは、現在のプラットフォームのプロセッサが倍精度で浮動小数点演算を実行するためです。 ただし、を使用`Double`した操作は、など`Integer`の整数型ほど高速ではありません。

## <a name="specifying-data-type"></a>データ型の指定
 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)を使用して、特定の型の変数を宣言します。 使用して、アクセス レベルを指定することが同時に、[Public](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)、または[Private](../../../../visual-basic/language-reference/modifiers/private.md)に示すように、キーワード、次の例です。

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a>文字変換
 関数`AscW` と`ChrW`関数は、Unicode で動作します。 これらは、と`Asc` `Chr`に優先して使用する必要があります。これは、Unicode との間で変換を行う必要があります。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [数値のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [IntelliSense の使用](/visualstudio/ide/using-intellisense)
