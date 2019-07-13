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
ms.openlocfilehash: f85acfe7592d7b90423107e0d45bb007fce5f4a8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601156"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>データ型の有効な使用方法 (Visual Basic)
宣言されていない変数とデータ型なしで宣言された変数が割り当てられている、`Object`データ型。 プログラムを迅速に記述が簡単になります。 ただし、ことより緩やかに変化を実行することがあります。  
  
## <a name="strong-typing"></a>厳密な型指定  
 すべての変数のデータ型の指定と呼びます*厳密な型指定*します。 厳密な型指定を使用して、いくつかの利点があります。  
  
- 変数に IntelliSense をサポートをできます。 これにより、コードに入力すると、プロパティやその他のメンバーを表示することができます。  
  
- コンパイラの型チェックの利点がかかります。 これは、オーバーフローなどのエラーにより実行時に失敗するステートメントをキャッチします。 サポートしていないオブジェクトに対するメソッドの呼び出しをキャッチします。  
  
- コードの実行速度が速くなります。  
  
## <a name="most-efficient-data-types"></a>最も効率的なデータ型  
 決して分数を含む変数、整数データ型は非整数の型よりも効率的です。 Visual basic で`Integer`と`UInteger`は最も効率的な数値型。  
  
 数値の小数部から成る場合`Double`を最も効率的なデータ型は、現在のプラットフォーム上のプロセッサでは、倍精度浮動小数点演算を実行するためです。 ただし、操作を`Double`などの整数型と同様に高速でない`Integer`します。  
  
## <a name="specifying-data-type"></a>データ型の指定  
 使用して、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)特定の型の変数を宣言します。 使用して、アクセス レベルを指定することが同時に、[Public](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)、または[Private](../../../../visual-basic/language-reference/modifiers/private.md)に示すように、キーワード、次の例です。  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>文字の変換  
 `AscW`と`ChrW`関数は Unicode で動作します。 優先的に使用する必要があります`Asc`と`Chr`Unicode との間に変換する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [数値のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [IntelliSense の使用](/visualstudio/ide/using-intellisense)
