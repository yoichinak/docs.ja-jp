---
title: 列挙型を使用する状況
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 5daae8d487ddfe079a54e305e59e32e8ded8f65e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353955"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>列挙型を使用する状況 (Visual Basic)
Enumerations offer an easy way to work with sets of related constants. An enumeration, or `Enum`, is a symbolic name for a set of values. Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.  
  
## <a name="when-to-use-an-enumeration"></a>列挙型を使用する状況  
 Whenever a procedure accepts a limited set of variables, consider using an enumeration. Enumerations make for clearer and more readable code, particularly when meaningful names are used.  
  
 The benefits of using enumerations include:  
  
- Reduces errors caused by transposing or mistyping numbers.  
  
- Makes it easy to change values in the future.  
  
- Makes code easier to read, which means it is less likely that errors will creep into it.  
  
- Ensures forward compatibility. With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.  
  
## <a name="naming-enumerations"></a>Naming Enumerations  
 Use a naming convention for enumeration members. When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name. Use a unique prefix that identifies the values from your application or component.  
  
 When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement. For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Predefined Enumerations  
 Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code. For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>関連項目

- [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [方法 : 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [方法 : 列挙値に関連付けられている文字列を確認する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
