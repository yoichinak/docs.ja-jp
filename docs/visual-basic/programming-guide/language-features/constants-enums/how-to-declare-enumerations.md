---
title: 'How to: Declare Enumerations'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 042aea045313bcaf3832274acf1000f87a084b72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354043"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>方法: 列挙型を宣言する (Visual Basic)
You create an enumeration with the `Enum` statement in the declarations section of a class or module. You cannot declare an enumeration within a method. To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.  
  
 An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant. The name must be a valid Visual Basic .NET qualifier. The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`. `Integer` が既定値です。 Enumerations are always strongly typed and are not interchangeable with integer number types.  
  
 Enumerations cannot have floating-point values. If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results. If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.  
  
 For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>To declare an enumeration  
  
1. Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Define the constants in the enumeration. By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant. For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. You can explicitly assign values to constants in an enumeration by using an assignment statement. You can assign any integer value, including negative numbers. For example, you may want constants with values less than zero to represent error conditions. In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`. Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`. The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>To declare an enumeration as an explicit type  
  
- Specify the type of the enum by using the `As` clause, as shown in the following example.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [方法 : 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [方法 : 列挙値に関連付けられている文字列を確認する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
