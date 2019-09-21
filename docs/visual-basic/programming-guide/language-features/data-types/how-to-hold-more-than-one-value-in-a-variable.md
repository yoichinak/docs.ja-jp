---
title: '方法: 1つの変数に複数の値を保持する (Visual Basic)'
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
ms.openlocfilehash: 8d07a34a98303f9d220dba0a3c955120b421340e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054194"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>方法: 1つの変数に複数の値を保持する (Visual Basic)

*複合データ型*として宣言すると、変数に複数の値が保持されます。

[複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)には、構造体、配列、およびクラスが含まれます。 複合データ型の変数は、基本データ型とその他の複合型の組み合わせを保持できます。 構造体とクラスは、データだけでなくコードも保持できます。

## <a name="to-hold-more-than-one-value-in-a-variable"></a>変数に複数の値を格納するには

1. 変数に使用する複合データ型を決定します。

2. 複合データ型がまだ定義されていない場合は、変数で使用できるように定義します。

    - Structure[ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)を使用して構造体を定義します。

    - [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)を使用して配列を定義します。

    - Class[ステートメント](../../../../visual-basic/language-reference/statements/class-statement.md)を使用してクラスを定義します。

3. ステートメントを`Dim`使用して変数を宣言します。

4. 変数名`As`の後に句を指定します。

5. キーワードの`As`後に、適切な複合データ型の名前を入力します。

## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
