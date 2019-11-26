---
title: '方法 : 変数内で複数の値を保持する'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: d452fbf35f9d200348234b38c40f8636f0ec4b4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350014"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>方法: 変数内で複数の値を保持する (Visual Basic)

A variable holds more than one value if you declare it to be of a *composite data type*.

[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes. A variable of a composite data type can hold a combination of elementary data types and other composite types. Structures and classes can hold code as well as data.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>To hold more than one value in a variable

1. Determine what composite data type you want to use for your variable.

2. If the composite data type is not already defined, define it so that your variable can use it.

    - Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).

    - Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).

    - Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).

3. Declare your variable with a `Dim` statement.

4. Follow the variable name with an `As` clause.

5. Follow the `As` keyword with the name of the appropriate composite data type.

## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
