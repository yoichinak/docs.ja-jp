---
title: '方法 : 定数を宣言する'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 5054d4a4fc02d8bd22efceb01770fc54167d8cb3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347466"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>方法: 定数を宣言する (Visual Basic)
You use the `Const` statement to declare a constant and set its value. By declaring a constant, you assign a meaningful name to a value. Once a constant is declared, it cannot be modified or assigned a new value.  
  
 You declare a constant within a procedure or in the declarations section of a module, class, or structure. Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.  
  
 The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>To declare a constant  
  
- Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).  
  
     When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause. The compiler determines the type of the constant from the type of the expression. For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>To declare a constant that has an explicitly stated data type  
  
- Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line. If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>To declare multiple constants on a single line  
  
- Separate the declarations with a comma and a space, as in the following example:  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>関連項目

- [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)
- [定数とリテラルのデータ型](constant-and-literal-data-types.md)
- [定数の概要](constants-overview.md)
- [方法 : 定数を宣言する](how-to-declare-a-constant.md)
- [ユーザー定義定数](user-defined-constants.md)
- [定数とリテラルのデータ型](constant-and-literal-data-types.md)
- [方法 : 関連する定数値をまとめてグループ化する](how-to-group-related-constant-values-together.md)
- [列挙型の概要](enumerations-overview.md)
- [方法 : 列挙型を宣言する](how-to-declare-enumerations.md)
- [方法 : 列挙型のメンバーを参照する](how-to-refer-to-an-enumeration-member.md)
- [列挙型と名前の修飾](enumerations-and-name-qualification.md)
- [方法 : 列挙型を反復処理する](how-to-iterate-through-an-enumeration.md)
- [方法 : 列挙値に関連付けられている文字列を確認する](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [列挙型を使用する状況](when-to-use-an-enumeration.md)

- [列挙型の概要](enumerations-overview.md)
- [定数の概要](constants-overview.md)
- [How to: Declare an Enumeration](how-to-declare-enumerations.md)
- [列挙型と名前の修飾](enumerations-and-name-qualification.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
