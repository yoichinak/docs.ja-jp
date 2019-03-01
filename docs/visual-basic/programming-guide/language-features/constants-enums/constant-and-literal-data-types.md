---
title: 定数とリテラルのデータ型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 269045dcfec14fafe878c2716490c93e79efe3d7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978216"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>定数とリテラルのデータ型 (Visual Basic)
リテラルは、変数の値または値 3 または文字列「こんにちは」など、式の結果ではなく自体として表現される値です。 定数とは、リテラルの代わりを受け取り、値が変化し、変数ではなく、プログラム全体で同じ値を保持するわかりやすい名前です。  
  
 ときに[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`データ型を持つすべての定数を明示的に宣言する必要があります。 データ型を次の例では、`MyByte`データ型として明示的に宣言されて`Byte`:  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 ときに`Option Infer`は`On`または`Option Strict`は`Off`、定数を宣言するにはデータ型を指定せず、`As`句。 コンパイラは、定数式の型からの種類を決定します。 既定でに整数リテラルをキャスト、`Integer`データ型。 浮動小数点数がの既定のデータ型`Double`、およびキーワード`True`と`False`指定、`Boolean`定数。  
  
## <a name="literals-and-type-coercion"></a>リテラルおよび強制型変換  
 場合によっては、リテラルを特定のデータ型を強制する可能性があります。たとえば、特に大きな整数リテラル値を型の変数に割り当てるときに`Decimal`します。 次の例では、エラーが生成されます。  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 リテラルの形式から、エラーが発生します。 `Decimal`データ型値を保持できるこの大きさが、リテラルは暗黙的に表した、 `Long`、することはできません。  
  
 2 つの方法で特定のデータ型のリテラルを強制する。 または文字を囲む内に配置することによって、型文字を追加することで。 型文字および文字を囲む必要がありますすぐに前に、またはなしに空白、または任意の種類の文字、リテラルに従ってください。  
  
 前の例を実行するために、追加することができます、`D`文字入力すると、リテラルとして表現すると、その、 `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 次の例では、型文字と囲み文字の正しい使用法を示しています。  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 次の表は、それを囲む文字と Visual Basic で利用可能な型の文字。  
  
|データの種類|囲み文字|末尾の型文字|  
|---|---|---|  
|`Boolean`|(なし)|(なし)|  
|`Byte`|(なし)|(なし)|  
|`Char`|"|C|  
|`Date`|#|(なし)|  
|`Decimal`|(なし)|D または @|  
|`Double`|(なし)|R または #|  
|`Integer`|(なし)|または %|  
|`Long`|(なし)|L または (& a)|  
|`Short`|(なし)|S|  
|`Single`|(なし)|F または!|  
|`String`|"|(なし)|  
  
## <a name="see-also"></a>関連項目
- [ユーザー定義定数](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [方法: 定数を宣言します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Option Explicit ステートメント](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [方法: 列挙体を宣言します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
